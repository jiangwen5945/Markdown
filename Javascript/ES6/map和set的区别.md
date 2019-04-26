# ES6中map和set的区别

- set中存储无序并且不可重复的元素
- map存储的是键值对

## Map:

`Map`是一组键值对的结构key : value,具有极快的查找速度。

```javascript
var m = new Map([['Michael', 95], ['Bob', 75], ['Tracy', 85]]);
m.get('Michael'); // 95
```

## Set:

Set是一组唯一key的集合，但不存储value。

