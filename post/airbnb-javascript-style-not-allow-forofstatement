# Airbnb JavaScript 代码规范不允许使用 for ... of

主要原因如下：

> iterators/generators require regenerator-runtime, which is too heavyweight for this guide to allow them. Separately, loops should be avoided in favor of array iterations.

迭代器的实现依赖于 `Symbol`，浏览器完全支持 `Symbol` 成本较高
