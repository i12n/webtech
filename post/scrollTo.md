# window.scrollTo

`window.scrollTo` 可以用于控制整个页面的滚动，这个兼容性应该是比较好的，jQuery 中 [scrollTop/scrollLeft](
https://github.com/jquery/jquery/blob/98386cfd775fdfa7837ccbec173b04f1e6d57896/src/offset.js#L213) 的实现就是依赖于 `window.scrollTo`. 
而对于元素的滚动，则使用 `scrollLeft` 和 `scrollTop`.


