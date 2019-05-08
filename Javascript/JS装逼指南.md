### ☆ 获取URL的查询参数

```javascript
let q = {};	// 创建查询结果对象
location.search.replace(/([^?&=]+)=([^&]+)/g,(_,k,v)=>q[k]=v);
```

### 创建特定大小的数组

```javascript
[...Array(3).keys()]	// [0, 1, 2]
```

### 数组去重

```javascript
[...new Set(arr)]
```

### 数组混淆

```javascript
arr.sort(()=>Math.random() - 0.5)
```

### 生成随机十六进制代码（生成随机颜色）

```javascript
'#'+ Math.floor(Math.random()*0xffffff).toString(16).padEnd(6,'0')
```

### 生成随机11位ID

```javascript
Math.random().toString(36).substring(2,13)	// hg7znok52x
```

### 将浏览器变为文本编辑器

```javascript
document.body.contentEditable=true
```



