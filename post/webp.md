# webp 简介

## webp特点

- 减少图片的大小，提升网页加载速度，节省网络带宽 

- 部分游览器或 webview 不支持 webp

## 兼容性检测

```js 
var WebP = new Image();
WebP.onload = WebP.onerror = function(){
    window.supportWebP = WebP.height == 1;
};
WebP.src = "data:image/webp;base64,UklGRiYAAABXRUJQVlA4IBoAAAAwAQCdASoBAAEAAAAMJaQAA3AA/v89WAAAAA==";
```

```js
var WebP = new Image();
var isWebp = Cookie.get('isWebp');
WebP.onload = function() {
    if(isWebp != 1) {
        Cookie.set('isWebp', 1, expireTime, domain);
    }
};

WebP.onerror = function() {
	if(isWebp != 0) {
	    Cookie.set('isWebp', 0, expireTime, domain);
	};
}

WebP.src = "data:image/webp;base64,UklGRiYAAABXRUJQVlA4IBoAAAAwAQCdASoBAAEAAAAMJaQAA3AA/v89WAAAAA==";
```


## 参考

- https://isux.tencent.com/introduction-of-webp.html
- https://github.com/tjuking/blog/issues/5
- http://zmx.im/blog?bname=webp