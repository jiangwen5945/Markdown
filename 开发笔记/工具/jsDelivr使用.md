> *jsDelivr* 是国外的一家优秀的公共 CDN 服务提供商



## 使用方法记录(github资源作为CDN引用)

1.在github项目中点击`releases`进行发布,并在该页面中填写项目对应版本号

2.在该项目的`branches/tags`中将默认的`branch`选项切换到`tags`,并选择发布版本

3.将该项目资源作为CDN引用

```javascript
// GitHub中的项目资源地址
https://github.com/jiangwen5945/happyGo/blob/v1.1/assets/layui/layui.js

// 使用jsdelivr将该资源作用CDN访问的地址(不设置版本号默认引用最新版本)
https://cdn.jsdelivr.net/gh/jiangwen5945/happyGo@v1.1/assets/layui/layui.js 
```

