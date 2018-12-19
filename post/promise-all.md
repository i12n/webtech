# 实现 Promise.all

1. Promise.all() 要并行处理多个 promise，所有 promise 都执行完毕才将结果返回。这个过程也是一个异步过程，即所有 promise 执行完毕之后进行回调。
2. Promise.all() 返回值也是一个 promise

```
Promise.all = function(args = []) {
  var promises = args.slice();
  var results = [], count = 0;
  return new Promise(function(resolve, reject) {
    for(var i = 0; i < promises.length; i++) {
      (function(i) {
      	 // 执行 promise
        Promise.resolve(promises[i]).then(result => {
          results[i] = result;
          count = count + 1;
          
          // 全部 promise 执行完毕
          if (count == promises.length) {
            resolve(results);
          }

        }, error => {
          reject(error)
        })
      })(i)
    }   
  })
}
```

以下代码验证：

```
Promise
.all([
  new Promise(function(resolve) {
    setTimeout(() => resolve(2), 3000)
  }),
  3
]).then(results => console.log(results))

// 打印输出 [2, 3]

```

[代码示例](https://codepen.io/gewenmao/pen/vQzKqb?editors=0012)

[参考示例](https://github.com/chunpu/min-promise/blob/gh-pages/src/index.js#L29)