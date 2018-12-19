# 双向数据绑定
```
<div id="app">
	<input data-modal="counter"/>
	<span data-bind="counter"></span>
</div>
```

```
function update(dom, data) {
	var children = dom.children;
	for (var i = 0; i < children.length; i++ ) {
		var key = children[i].getAttribute('data-modal') || children[i].getAttribute('data-bind');
		if (key in data && data[ key ] !== children[i].value) {
      if ('value' in children[i]) {
        children[i].value = data[key];
      } else {
        children[i].innerHTML = data[key];
      }
		}
	}
	
}
function Bind() {
  var dom = document.getElementById('app');

  var data = {
	  counter: 0
  }
	var children = dom.children;
	var proxy = new Proxy(data, {
		get: function(target, name) {
        	return target[name];
   		},
   		set: function(obj, name, value) {
   			 obj[name] = value;
   			 update(dom, proxy)
   		}
	})
	update(dom, proxy)
	dom.addEventListener('input', function(e) {
    var key = e.target.getAttribute('data-modal');
		
		if (key) {
			proxy[key] = e.target.value;
		}
	})
	
	return  proxy;
}

data = new Bind();
data.counter = 1;
```

[代码示例](https://codepen.io/gewenmao/pen/RqOpmj)