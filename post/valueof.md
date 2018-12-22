# valueOf


1. 如何实现 `a == 1 && a == 2` 为 `true`

```
var a = {i: 0};

a.valueOf = function() {
	this.i = this.i + 1;
	return this.i;
};
	
a==1 && a==2; // true
```

关于 `a === 1 && a === 2`

```
var b = 1;
Object.defineProperty(window, 'a', {
	get: function() {
		return this.b += 1;
	}
});
a === 2 && a === 3; // true
```

2. 实现 `add` 的链式调用

```
function add(value) {
	var result = function (data) {
		return add(data + value);
	};
	result.valueOf = function() {
		return value;
	};
	return result;
};

add(1)(2)(3)
```
 