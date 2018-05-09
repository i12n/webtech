# 用 css 画一棵组织树

![](/image/organization_tree.png)

先介绍几个要用到的 CSS 选择器:

- `+` 相邻兄弟选择器

- `>` 子元素选择器

- `:first-child` 第一个子元素

- `:last-child` 最后一个子元素

- `:only-child` 唯一子元素

实现组织树需要使用上面的选择器来设置样式。

HTML 如下：

```html
<ul class="org-tree">
  <li class="org-li">
    <div class="org-item">
      <span class="org-item__text">集团</span>
    </div>
    <ul>
      <li class="org-li">
        <div class="org-item">
          <span class="org-item__text">公司1</span>
        </div>
        <ul>
          <li class="org-li">
            <div class="org-item">
              <span class="org-item__text">部门A</span>
            </div>
          </li><li class="org-li">
            <div class="org-item">
              <span class="org-item__text">部门B</span>
            </div>
          </li>
        </ul>
      </li><li class="org-li">
        <div class="org-item">
          <span class="org-item__text">公司2</span>
        </div>
      </li><li class="org-li">
        <div class="org-item">
          <span class="org-item__text">公司3</span>
        </div>
      </li>
    </ul>
  </li>
</ul>
```
CSS 如下

```css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

.org-tree {
    display: inline-block;
    padding: 16px;
    white-space: nowrap;
}

.org-tree li {
    display: inline-block;
    vertical-align: top;
    position: relative;
    white-space: normal;
    text-align: left;
}

.org-item__text {
    display: inline-block;
    width: 184px;
    height: 36px;
    background: #666666;
    border-radius: 2px;
    padding: 8px;
    font-size: 14px;
    color: #FFFFFF;
    line-height: 20px;
    vertical-align: middle;
}

.org-tree .org-li:first-child:before {
    content: '';
    margin-left: 91px;
    display: block;
    height: 0;
    border-top: 1px dashed #cccccc;
}

.org-tree .org-li:last-child:before {
    content: '';
    width: 91px;
    display: block;
    height: 0;
    border-top: 1px dashed #cccccc;
}

.org-tree > .org-li:only-child:before {
  width: 0;
}


.org-tree .org-li:before {
    content: '';
    display: block;
    height: 0;
    border-top: 1px dashed #cccccc;
}

.org-item {
  padding: 0 16px 0 0;
}

.org-item:before {
    content: '';
    display: block;
    margin-left: 91px;
    height: 16px;
    border-left: 1px dashed #cccccc;
    width: 0;
}

.org-tree > .org-li > .org-item:before {
    border: none;
}

.org-item:after {
    content: '';
    display: block;
    margin-left: 91px;
    height: 16px;
    border-left: 1px dashed #cccccc;
    width: 0;
}

.org-li .org-item:only-child:after {
  border: none;
}
```

[代码示例](https://codepen.io/anon/pen/rvJBLd?editors=1100)

也可以参考 [ant.design 树形组件](http://2x.ant.design/components/tree-cn/)