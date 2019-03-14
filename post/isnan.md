# window.isNaN & Number.isNaN

window.isNaN 用于判断某个变量是否是合法的数字，例如：

```js
window.isNaN(1); // false
window.isNaN('1'); // false
window.isNaN('a'); // true
```

这里隐含一个条件就是，会对变量做隐式类类型转换，如果转换的最终结果不是有效的数字那么 isNaN 为 true，这一过程与以下类似：

```js
Number(1); // 1
Number('1'); // 1
Number('a'); // NaN
```

值得注意的是 NaN 是一个 Number 类型：

```js
typeof NaN;  // number
```

还有一点，NaN 与 NaN 之间不相等：

```js
NaN == NaN; // false
```

那么，这里有这样一个问题，如何判断某个变量是否是 NaN ？例如：

```js
var num = Number('a'); // 如何 a 是 NaN
```

换个说法，如何判断 NaN？（与如何判断一个数字是否合法是有区别的）

```js
window.isNaN(NaN); // true, 无法判断是不是 NaN
```

这时候需要用 Number.isNaN :

```js
Number.isNaN(NaN); // true
Number.isNaN('a'); // false
Number.isNaN(1); // false
```

可以等价于：

```js
 var a = NaN;
 window.isNaN(a) && typeof a == 'number'; // true
```