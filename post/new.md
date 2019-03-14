# new 相关

构造函数带有返回值

```js
function Person(name) {
    this.name = name
    return name;
}
let p = new Person('Tom'); // {name: 'Tom'}

function Person(name) {
    this.name = name
    return {}
}
let p = new Person('Tom'); // {}
```