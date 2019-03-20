# bridge

在 APP 中存在大量的页面是用 H5 实现的，这些 H5 页面是通过 UIWebView 在 APP 中打开，那么是否能实现 H5 与 native 之间进行交互呢？答案是可以的，使用 [WebViewJavaScriptBridge](https://github.com/marcuswestin/WebViewJavascriptBridge) 能够实现这样的功能

WebViewJavaScriptBridge 实现桥协议的关键是在于，UIWebView 提供了执行 js 字符串的接口，也就是说在 oc 中可以通过这个接口来执行 js 代码；而 UIWebViewDelegate 可以捕获到页面中发出的请求，根据捕获的 url 请求作出相应的处理。

> 在 native 中 `stringByEvaluatingJavaScriptFromString` 可以执行 js 字符串；iOS7 开始引入了 JavaScriptCore, 其中的 `evaluateScript` 可以执行 js 代码

![http://img.my.csdn.net/uploads/201211/21/1353503436_3530.png](http://img.my.csdn.net/uploads/201211/21/1353503436_3530.png)

基本原理：
[WebViewJavascriptBridge_JS.m](https://github.com/marcuswestin/WebViewJavascriptBridge/blob/master/WebViewJavascriptBridge/WebViewJavascriptBridge_JS.m)(也就是示意图中的WebViewJavascriptBridge.js) 中定义了一段生成 `window.WebViewJavascriptBridge` 的 js 代码. `window.WebViewJavascriptBridge` 维护一个队列，队列中存储着 Web Page 端和 Native Code 之间交互的数据，以及回调函数信息。`window.WebViewJavascriptBridge` 通过 frame 的 src 发送请求， Native Code 会拦截 url，做出处理。 Native Code 中也会调用 `window.WebViewJavascriptBridge` 中的方法和队列，完成一系列操作。 