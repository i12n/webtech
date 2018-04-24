# instanceof 操作符简介

`instanceof` 用于判断某个对象是否是某个类的一个示例，那么，`instanceof` 是如何实现判断的过程呢？在 [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/instanceof) 上有这么一句话来描述 `instanceof `: 

> The instanceof operator tests whether the prototype property of a constructor appears anywhere in the prototype chain of an object.

简而言之，`instanceof` 判断构造函数的原型属性是否出现在对象的原型链上，如果 构造函数的原型属性出现在对象的原型链上则返回 true，否则返回 false。下图是一个原型链示意图：

![](/image/prototype_chain.png)

当执行 `a instanceof Object` 时，因为 `Object.prototype` 在 `a` 的原型链上，所以返回为 `true`

知道这一点，我们可以自己实现一个方法用来模拟 `instanceof` 功能: 

```
function instancof(a, A) {
	while(a != null) {
		if (a.__proto__ == A.prototype) {
			return true;
		}
		a = a.__proto__;
	}
	return false;
}
```
