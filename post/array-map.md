# 实现 Array.map 

1. 关于 Array.map 参数：

```
// 有两个参数 callback、thisArg
var new_array = arr.map(function callback(currentValue[, index[, array]]) {
    // Return element for new_array
}[, thisArg])
```

2. 实现如下（未处理 thisArg）：

```
Array.prototype.map = function(excutor) {
  var arr = new Object(this);
  var result = [];
  
  for (var i = 0; i < arr.length; i++) {
    result[ i ] = excutor(arr[i], i, arr);
  }
  
  return result;
};

[1, 2, 3].map(function(item, index, array) {
  return item + 1;
});
```

[代码示例](https://codepen.io/gewenmao/pen/WYaNJq?editors=1011)

[array.map](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)