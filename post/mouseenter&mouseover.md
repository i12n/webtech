
# mouseenter 与 mouseover 区别

mouseenter 不能冒泡，mouseover 能够冒泡。虽然 mouseenter 不能冒泡，但是父元素同样会触发 mouseenter 事件，而且这个事件用 `stopPropagation` 和 `preventDefault`
无法阻止的。

具体可见文档细节参考 [MDN mouseenter 事件](https://developer.mozilla.org/zh-CN/docs/Web/API/Element/mouseenter_event)
