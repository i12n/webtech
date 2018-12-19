# Chrome DevTools Extension

[文档](https://developer.chrome.com/devtools/docs/integrating#devtools_chrome_extensions)

## chrome.devtools.panels

使用 `chrome.devtools.panels` API 可以在 DevTools 自定义控制面板。

```
chrome.devtools.panels.create(
  "Custom Panel",
  null,
  "devtool/panel.html",
  function(panel, result) {
    // onShown, onHidden, onSearch
  }
);
```

可以添加 SideBar, 包含两种 elements sidebar 和  sources sidebar

- elements sidebar

	```
	//  Create a new elements sidebar
	chrome.devtools.panels.elements.createSidebarPane("Custom Sidebar", function(sidebar)
	{ 
	  var showChild = getChildren(sidebar);
	  showChild();
	  chrome.devtools.panels.elements.onSelectionChanged.addListener(showChild);
	});
	```

- sources sidebar

	```
	// Create a new sources sidebar
	chrome.devtools.panels.sources.createSidebarPane("Custom Sidebar", function(sidebar)
	{
	  sidebar.setPage('devtool/peppa.html');
	  sidebar.setHeight("800px");
	});
	```

具体见文档 [https://developer.chrome.com/extensions/devtools_panels](https://developer.chrome.com/extensions/devtools_panels)

## chrome.devtools.inspectedWindow

- 执行 JS 代码
		
	```
	chrome.devtools.inspectedWindow.eval('console.log("inspectedWindow.eval");');
	```
	
- 获取所有资源	
	
	```
	chrome.devtools.inspectedWindow.getResources(function (res) {
	  chrome.devtools.inspectedWindow.eval('console.log(' + JSON.stringify(res)+ ');');
	})
	```

- 重新加载
	
	```
	chrome.devtools.inspectedWindow.reload()
	```
	
- 监听资源
	
	```
	// 更改 source 文件时候触发
	chrome.devtools.inspectedWindow.onResourceContentCommitted.addListener(function(resource, content) {
	  resource.getContent(function(_content, _encoding) {
	    chrome.devtools.inspectedWindow.eval('console.log(' + JSON.stringify(_content) + ');');
	  })
	  chrome.devtools.inspectedWindow.eval('console.log(' + JSON.stringify(content) + ');');
	})
	```

具体文档 [https://developer.chrome.com/extensions/devtools_inspectedWindow](https://developer.chrome.com/extensions/devtools_inspectedWindow)

应用示例 [https://github.com/NV/chrome-devtools-autosave](https://github.com/NV/chrome-devtools-autosave)

## chrome.devtools.network

- 获取请求的 HAR（HTTP Archive） 信息

	```
	chrome.devtools.network.getHAR(function(result) {
	  chrome.devtools.inspectedWindow.eval('console.log(' + JSON.stringify(result) + ')');
	});
	```
	
	> [har 相关介绍](http://www.softwareishard.com/blog/har-12-spec/#headers)
	
- 添加请求头

	```
	chrome.devtools.network.addRequestHeaders({
	  "X-PROXY-HOSTNAME": "HOSTNAME"
	});
	```
	
- 事件监听

	```
	chrome.devtools.network.onRequestFinished.addListener(function(request) {
		chrome.devtools.inspectedWindow.eval('console.log(unescape("' + escape(request.request.url) + '"))');
	});

	chrome.devtools.network.onNavigated.addListener(function(request) {
	  	chrome.devtools.network.getHAR(function(result) {
			var entries = result.entries;
			chrome.devtools.inspectedWindow.eval('console.log(' + JSON.stringify(result) + ')');
		});
	}
	```

## 相关文档

- [https://developer.chrome.com/extensions](https://developer.chrome.com/extensions)
- [https://developer.chrome.com/extensions/devtools](https://developer.chrome.com/extensions/devtools)



