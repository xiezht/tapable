

```js
// asyncParallel 调用 call 实时编译生成的 tap 函数代码
var _fn1 = _x[1];
_fn1(x, function (_err1) {
  if (_err1) {
    if (_counter > 0) {
      _callback(_err1);
      _counter = 0;
    }
  } else {
    if (--_counter === 0) _done();
  }
});


// 跑一下测试用例，得到的完整 callAsync 函数如下
"use strict";
var _context;
var _x = this._x;
do {
  var _counter = 2;
  var _done = function () {
    _callback();
  };
  if (_counter <= 0) break;
  var _fn0 = _x[0];
  _fn0(x, function (_err0) {
    if (_err0) {
      if (_counter > 0) {
        _callback(_err0);
        _counter = 0;
      }
    } else {
      if (--_counter === 0) _done();
    }
  });
  if (_counter <= 0) break;
  var _fn1 = _x[1];
  _fn1(x, function (_err1) {
    if (_err1) {
      if (_counter > 0) {
        _callback(_err1);
        _counter = 0;
      }
    } else {
      if (--_counter === 0) _done();
    }
  });
} while (false);
```


