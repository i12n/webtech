# Promise 的一些特性

```
new Promise(resolve => {
  resolve(2)
})
.then(4)
.then(res => {
  console.log(res)
})

// 2
```


```
let promise = Promise.resolve('A')
console.log('B'); 
promise.then(res => {
  console.log(res + 1);
  return res + '4'
}).then(res => {
  console.log(res)
})
console.log('C')
promise.then(res => {
  console.log(res + 2);
  return;
})

// B C A1 A2 A4
```



```
var promise = new Promise(resolve => {
	var promise1  = new Promise(resolve1 => {
		resolve1(1)
	})
	.then(res => {
		console.log(1);
		return 2;
	})
	.then(res => {
		console.log(res);
		return 3
	});
	resolve(promise1)
})
.then(res => console.log(res))

// 1 2 3
```

1 2 3

- [Promise A+ 标准](https://promisesaplus.com/)
- [Promise A+ 实现](https://promisesaplus.com/implementations)
- [ECMA 262 Promise](https://tc39.github.io/ecma262/#sec-promise-objects)
- [robin-egg-bluebird 实现 Promise](https://github.com/danthareja/robin-egg-bluebird)