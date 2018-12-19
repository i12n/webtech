# 简单模板解析

```
var template=`<p>{{a}}{{ b.c }}{{ d[0] }}{{p.f}}</p>`
var data = {
  a: 1,
  b: {c: 2},
  d: [3, 4, 5]
}

function getData(data, params) {
  return (new Function('data', `try {return data.${params}} catch(e) { }`))(data);
}

function getHTML(template, data) {
  return template.replace(/\{\{\s*(.*?)\s*\}\}/g, function($0, $1) {
    return getData(data, $1)
  })
}

console.log(getHTML(template, data))
```

https://codepen.io/gewenmao/pen/aQgozz?editors=0010