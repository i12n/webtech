# Events

## DOMContentLoaded

DOMContentLoaded: 当HTML document 被完全的加载和解析的时候被触发，而不需要等待样式、图片、frame 完成加载；这时 DOM 树已经建成，但是一些资源没有加载完成。注意以下事项：
  
- script 标签会暂停 DOM 的构建，所以 DOMContentLoaded 会等待加载执行完成才被触发；当 script 加了`async` 属性之后，script 以加载完成的顺序执行，DOMContentLoaded 不会等待 script 执行完成后再触发；当 script 加了`defer` 属性之后，script 会按文档的顺序执行，但是要等到 document 加载和解析完成之后执行 script，执行完 这些 script 触发 DOMContentLoaded 事件

- 浏览器的form表单的自动填充（autofill）也是监听了 DOMContentLoaded 事件；例如用户名和密码等自动填充到 form 表单要等到 DOMContentLoaded 触发之后进行。
- 对于样式，如果 `link` 标签后面有 `script` 标签，则需要加载完 `link` 标签 才能执行 script 标签脚本，执行完之后才会触发 DOMContentLoaded

参考

- https://javascript.info/onload-ondomcontentloaded
- https://molily.de/domcontentloaded/

## orientationchange

orientationchange: 水平或垂直翻转设备时触发；例如当用户在浏览网页时，设备旋转网页由竖屏变为横屏，这时需要进行一些适配

```js
	var evt = 'orientationchange' in window ? 'orientationchange' : 'resize';
	window.addEventListener('evt', function(e) {
		e.preventDefault();
		document.documentElement.style.fontSize = 50 * (document.documentElement.clientWidth / 750 / 2) + 'px';
	}, false)
```

## click

click: 在移动端点击事件有300ms的延迟，出现延迟的原因是，浏览器需要判断是否是双击事件，因为在移动端浏览器中，双击会对页面进行缩放。解决方法如下：

- 禁止页面缩放 `initial-scale=1`、`user-scalable=no`, 针对 Android Chrome
- 使用 touchstart、touchend 模拟 click 事件, 例如 [fastclick](https://github.com/ftlabs/fastclick)、[zepto](https://github.com/mattt/MsgPackSerialization/wiki/%E7%A7%BB%E5%8A%A8%E7%AB%AFclick%E5%BB%B6%E8%BF%9F%E5%8F%8Azepto%E7%9A%84%E7%A9%BF%E9%80%8F%E7%8E%B0%E8%B1%A1)

## touch

   [about touch](http://gewenmao.github.io/2019/web/about-touchevent)

## focus

   [about focus](https://github.com/gewenmao/webtech/blob/master/post/focus-event.md)