# JSON sringify

JSON.sringify 将 json 数据转化为字符串([JSON.stringify](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify)), 
仔细读文档可以发现 JSON.stringify(value[, replacer [, space]) 有三个参数，其中，第二个参数 replacer 对数据做一些调整，在某些场景下可以用一下。例如，当通过后端接口获取数据之后，如果数据的某些字段不需要时，可以通过 replacer 过滤掉。

```js
var obj = {'name': 'abc', data: {type: 1}};
JSON.stringify(obj, ['name', 'data']); // "{"name":"abc","data":{}}"
JSON.stringify(obj, ['name', 'data', 'type']); // "{"name":"abc","data":{"type":1}}"
```
