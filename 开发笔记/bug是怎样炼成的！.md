### 问题描述：通过append在页面生成之后添加元素挂载事件无效

### 解决方法：

​	通过jQuery的事件代理方法`on()`添加第二个参数

### 示例：

```javascript
// .content是append内容的容器，添加元素节点前已存在； 
// .after-child是添加后需要绑定事件的节点
$(".content").on('click','.after-child',function(){ 
    //...do something
})
```



---

