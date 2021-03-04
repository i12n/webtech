# 关于 Boolean

Boolean 有两种用法，第一种是作为构造函数生成一个布尔对象，第二种时作为一个函数返回一个布尔值，两者有很大的差别。

```js
const value = new Boolean(false);

if (value) {
  console.log(true);    // true
}

```

上面的代码会打印 `true`, 在条件语句中，任何非 `null` 和 `undefined` 的对象都会被解析为 `true`，所以上面的代码中，会打印一个 `true`。
正是由于这一点，开发中很少用到布尔对象，更多的是将 Boolean 作为函数去使用，`Boolean(expression)` 与 `!!expression` 等价：

```js
const value = Boolean(false);

if (value) {
  console.log(true);
}

```

[https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)
