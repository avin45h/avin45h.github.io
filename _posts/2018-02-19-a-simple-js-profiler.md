---
layout: post
title: How is my node.js code performing?
---

Well, below is a nifty piece of code that I use (node.js) almost all the time when I am trying to keep a track of how good my code is performing.

```javascript
class Profiler {
    constructor(label) {
        this.label = label;
        this.times = {};
        this.initTime = null;
        this.index = 0;
    }

    start() {
        this.initTime = process.hrtime();
    }

    record(label, label2) {
        if (!this.initTime) {
            this.start();
        }
        const time = process.hrtime();
        const fromInit = diff(time, this.initTime);
        const fromInitNanos = toNanos(fromInit);
        this.times[label || this.index] = {
            time: time,
            from: {
                init: {
                    time: fromInit,
                    nanos: fromInitNanos,
                    millis: fromInitNanos/1e6
                }
            }
        };
        if (label2 && this.times[label2] && this.times[label2].time) {
            const fromLabelTime = diff(time, this.times[label2].time);
            const nanos = toNanos(fromLabelTime);
            this.times[label].from[label2] = {
                time: fromLabelTime,
                nanos: nanos,
                millis: nanos/1e6
            }
        }
        this.index += 1;
    }

    print(tabs) {
        console.log(JSON.stringify(this.times, null, tabs || 2));
    }
}

function toNanos(time){
    return time[0] * 1e9 + time[1]
}

function diff(a, b) {
    let s = a[0] - b[0];
    let ms = a[1] - b[1];

    if (ms < 0) {
        s = s - 1;
        ms = 1e9 + ms;
    }

    return [s, ms];
}

module.exports = function (label) {
    if (process.env.NODE_ENV === 'development') {
        return new Profiler(label);
    } else if (process.env.NODE_ENV === 'production') {
        return {
            start: function () {
            },
            record: function () {
            },
            print: function () {
            }
        }
    } else {
        throw new Error('Must set NODE_ENV');
    }
};
```

And the output :D

Code

```javascript

var timer = require('./simple-code-profiler')('example-profiler');
timer.start();
setTimeout(function(){
    timer.record('foo');
    setTimeout(function(){
        timer.record('bar', 'foo');
        timer.print();
    }, 1000);
}, 2000);
    
```

Output

```javascript
{
  "foo": {
    "time": [
      224162,
      379566684
    ],
    "from": {
      "init": {
        "time": [
          2,
          2506717
        ],
        "nanos": 2002506717,
        "millis": 2002.506717
      }
    }
  },
  "bar": {
    "time": [
      224163,
      384909087
    ],
    "from": {
      "init": {
        "time": [
          3,
          7849120
        ],
        "nanos": 3007849120,
        "millis": 3007.84912
      },
      "foo": {
        "time": [
          1,
          5342403
        ],
        "nanos": 1005342403,
        "millis": 1005.342403
      }
    }
  }
}
```

Future scope: Maybe add graphs and streaming to some stats collection like data dog