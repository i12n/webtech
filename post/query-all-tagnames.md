# 获取页面内所有标签

是 [getElementsByTagName](https://developer.mozilla.org/zh-CN/docs/Web/API/Document/getElementsByTagName) 的一个特殊用法： 

```js
const tags = document.getElementsByTagName('*');
const tagNames = [];
const len = tags.length;

for(let i = 0; i < len; i += 1) {
  tagNames.push(tags[i].tagName)
}

console.log(tagNames)

```

