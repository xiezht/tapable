

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

// 跑一下测试用例，得到的完整 callAsync 函数如下 function callAsync(x, _callback) { fnCode }
// x 为 new Hook(x) 时传递的参数，new Hook时定义的参数名字回传递给 tap 注册的回调函数
"use strict";
var _context;
// 这里的this，会指向 hook 实例（hook.callAsync），而非 Factory 实例
// 执行 compile 时，hook._x 会被设置为 tap.map(item => item.fn)
// 拷贝引用避免被修改
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
  // 这里的 x 是callAsync的第一个参数
  _fn1(x, function (_err1) {
    if (_err1) {
      if (_counter > 0) {
        // callAsync 的 _callback 参数
        _callback(_err1);
        _counter = 0;
      }
    } else {
      if (--_counter === 0) _done();
    }
  });
} while (false);
```
