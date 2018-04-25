# focus 事件

当元素获得焦点时，会触发 focus 事件。与其他事件相比，focus 事件有一些比较特殊的点，主要体现在以下两个方面：

1. 并不是所有的元素都能够触发 focus 事件
2. focus 事件只能支持事件捕获，不支持事件冒泡

## focusable 元素

能够获得焦点的元素被称为 focusable 元素，focusable 元素获得焦点的方式有三种：

- **鼠标点击**：元素被鼠标点击可以获得焦点
- **tab 键**：tab 键可切换可以使元素获得焦点
- **调用 focus() 方法**：调用元素的 focus() 方法使元素获得焦点

focusable 元素在获得焦点时会触发 focus 事件，例如表单元素 \<input> 等；非 focusable 元素由于不能获得焦点，因此也无法触发 focus 事件，例如 \<div> 元素等。focusable 元素包括以下几种：

- **window**：当页面窗口从隐藏变成前置可见时，focus 事件就会触发
- **表单元素(form controllers)**：input/option/textarea/button
- **链接元素(links)**：a标签、area标签（必须要带 href 属性，包括 href 属性为空）
- **设置了 tabindex 属性（tabindex 值非-1）的元素**
- **设置了 contenteditable = "true" 属性的元素**

将一个非 focusable 元素转换为 focusable 元素只需要设置它的 tabindex 属性 或者 contenteditable 属性。

```
<!-- html -->
<div id="content" tabindex="1"></div>

/* 
* 由于设置了 tabindex 属性，
* div 成为一个 focusable 元素，
* 当元素获得焦点时，focus 事件被触发 
*/
var target = document.getElementById('content');
target.addEventListener('focus', function() {
  console.log('focus');
})
```

## 事件委托

focus 事件只能支持事件捕获，不支持事件冒泡；在对 focus 进行事件委托的时候，
需要在捕获阶段进行响应事件。

```
<ul tabIndex="1" id="content">
	<li tabIndex="1"></li>
	<li tabIndex="2"></li>
	<li tabIndex="3"></li>
	<li tabIndex="4"></li>
</ul>

var target = document.getElementById('content');
target.addEventListener('focus', function() {
  console.log('focus');
}, true); // true 表示在事件捕获阶段调用事件处理函数
```

另外，某些浏览器支持这两个事件 `focusin` 和 `focusout`，这两个事件是可以冒泡的，可用 `focusin` 和 `focusout` 代替 `focus` 和 `blur` 事件。


资料

- [https://developer.mozilla.org/en-US/docs/Web/Events/blur](https://developer.mozilla.org/en-US/docs/Web/Events/blur)
- [https://segmentfault.com/a/1190000003942014](https://segmentfault.com/a/1190000003942014)
