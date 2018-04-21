# JavaScript 数组去重

如何将一个数组去重？

方法一：遍历数组并去重

```
function uniq(array) {
	var result = [];
	for(var value of array) {
		if (result.indexOf(value) == -1) {
			result.push(value);
		}
	}

	return result;
}

var array = uniq([1,2,3,4,4,5,2,3]);
console.log(array); //  [1, 2, 3, 4, 5]

```

方法二：filter 方法过滤

```
function uniq(array) {
	var result = array.filter((value, index, self) => self.indexOf(value) == index);
	
	return result;
}

var array = uniq([1,2,3,4,4,5,2,3]);
console.log(array); //  [1, 2, 3, 4, 5]
```

方法三：reduce 方法过滤

```
function uniq(array) {
	var result = array.reduce((pre, value) => {
		pre.indexOf(value) == -1 && pre.push(value);
		return pre;
	}, [])	
	return result;
}

var array = uniq([1,2,3,4,4,5,2,3]);
console.log(array); //  [1, 2, 3, 4, 5]
```

方法四：使用 Set 去重 

```
function uniq(array) {
	var result = [...new Set(array)];
	return result;
}

var array = uniq([1,2,3,4,4,5,2,3]);
console.log(array); //  [1, 2, 3, 4, 5]
```

- [https://stackoverflow.com/questions/840781/get-all-non-unique-values-i-e-duplicate-more-than-one-occurrence-in-an-array](https://stackoverflow.com/questions/840781/get-all-non-unique-values-i-e-duplicate-more-than-one-occurrence-in-an-array?page=1&tab=votes#tab-top)
- [https://stackoverflow.com/questions/9229645/remove-duplicate-values-from-js-array](https://stackoverflow.com/questions/9229645/remove-duplicate-values-from-js-array)
