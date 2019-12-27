###  获取URL的查询参数

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
function unique1 (arr) {
  return Array.from(new Set(arr)) 
    // 或 return [...new Set(arr)]
}

function unique2(arr) {
    return arr.filter((v, i, array) => array.indexOf(v) === i)
}

function unique3(arr){
    return arr.reduce((prev,cur) => prev.includes(cur) ? prev : [...prev,cur],[]);
}

function unique4(arr) {
    var array = [];
    for (var i = 0; i < arr.length; i++) {
        if (array.indexOf(arr[i]) === -1) {
            array.push(arr[i])
        }
    }
    return array;
}

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

### 将页面元素变为可编辑

```javascript
document.body.contentEditable=true
```

### 常用正则

```javascript
// 匹配邮箱
let reg = /^([a-zA-Z]|[0-9])(\w|\-)+@[a-zA-Z0-9]+\.([a-zA-Z]{2,4})$

// (新)匹配手机号
let reg = /^1[0-9]{10}$/;

// (旧)匹配手机号
let reg = /^1(3|4|5|7|8)[0-9]{9}$/;

// 匹配8-16位数字和字母密码的正则表达式
let reg = /^(?![0-9]+$)(?![a-zA-Z]+$)[0-9A-Za-z]{8,16}$/;

// 匹配国内电话号码 0510-4305211
let reg = /\d{3}-\d{8}|\d{4}-\d{7}/;

// 匹配身份证号码
let reg=/(^\d{15}$)|(^\d{18}$)|(^\d{17}(\d|X|x)$)/;

// 匹配腾讯QQ号
let reg = /[1-9][0-9]{4,}/;

// 匹配ip地址
let reg = /\d+\.\d+\.\d+\.\d+/;

// 匹配中文
let reg = /^[\u4e00-\u9fa5]*$/;
```

### 检测平台（设备）类型

```javascript
var WIN = window;
var LOC = WIN["location"];
var NA = WIN.navigator;
var UA = NA.userAgent.toLowerCase();

function test(needle) {
  return needle.test(UA);
}

var IsTouch = "ontouchend" in WIN;
var IsAndroid = test(/android|htc/) || /linux/i.test(NA.platform + "");
var IsIPad = !IsAndroid && test(/ipad/);
var IsIPhone = !IsAndroid && test(/ipod|iphone/);
var IsIOS = IsIPad || IsIPhone;
var IsWinPhone = test(/windows phone/);
var IsWebapp = !!NA["standalone"];
var IsXiaoMi = IsAndroid && test(/mi\s+/);
var IsUC = test(/ucbrowser/);
var IsWeixin = test(/micromessenger/);
var IsBaiduBrowser = test(/baidubrowser/);
var IsChrome = !!WIN["chrome"];
var IsBaiduBox = test(/baiduboxapp/);
var IsPC = !IsAndroid && !IsIOS && !IsWinPhone;
var IsHTC = IsAndroid && test(/htc\s+/);
var IsBaiduWallet = test(/baiduwallet/);
```

### 常用的日期时间函数

``` javascript
/*
* 时间格式化显示
* @param notation: 格式化连接符号,默认以年月日格式显示
* @param timeStamp: 需要格式化的时间戳,默认为当前时间戳 
* @returns String 
*/
function getTimeFormat(notation,timeStamp) {
  let tempStamp = timeStamp || new Date().getTime()
  let date = new Date(tempStamp);
  let Y = date.getFullYear();
  let M =(date.getMonth()+1).toString().padStart(2,'0');
  let D = date.getDate().toString().padStart(2,'0');

  if (!notation) {
    let strTime = `${Y}年${(M)}月${D}日`
     return strTime
    } else {
    let strTime = `${Y}${notation}${(M)}${notation}${D}`
      return strTime
    }
}

// 倒计时时间格式化
function format_time(timeStamp) {
    let day = Math.floor(timeStamp / (24 * 3600 * 1000));
    let leave1 = timeStamp % (24 * 3600 * 1000);
    let hours = Math.floor(leave1 / (3600 * 1000));
    let leave2 = leave1 % (3600 * 1000);
    let minutes = Math.floor(leave2 / (60 * 1000));
    let leave3 = leave2 % (60 * 1000);
    let seconds = Math.floor(leave3 / 1000);
    if (day) return day + "天" + hours + "小时" + minutes + "分";
    if (hours) return hours + "小时" + minutes + "分" + seconds + "秒";
    if (minutes) return minutes + "分" + seconds + "秒";
    if (seconds) return seconds + "秒";
    return "时间到！";
}
```

###  跨端事件处理

``` javascript
// 是否支持触摸事件
let isSupportTouch = ("ontouchstart" in document.documentElement) ? true : false;

//禁用Enter键表单自动提交
document.onkeydown = function(event) {
    let target, code, tag;
    if (!event) {
        event = window.event; //针对ie浏览器
        target = event.srcElement;
        code = event.keyCode;
        if (code == 13) {
            tag = target.tagName;
            if (tag == "TEXTAREA") { return true; }
            else { return false; }
        }
    }
    else {
        target = event.target; //针对遵循w3c标准的浏览器，如Firefox
        code = event.keyCode;
        if (code == 13) {
            tag = target.tagName;
            if (tag == "INPUT") { return false; }
            else { return true; }
        }
    }
};
```

###  移动端适配方案

``` javascript
(function (doc, win) {
    var docEl = doc.documentElement,
        resizeEvt = 'orientationchange' in window ? 'orientationchange' : 'resize',
        recalc = function () {
            var clientWidth = docEl.clientWidth;
            var fontSize = 20;
            docEl.style.fontSize = fontSize + 'px';
            var docStyles = getComputedStyle(docEl);
            var realFontSize = parseFloat(docStyles.fontSize);
            var scale = realFontSize / fontSize;
            console.log("realFontSize: " + realFontSize + ", scale: " + scale);
            fontSize = clientWidth / 667 * 20;
            if(isIphoneX()) fontSize = 19;
            fontSize = fontSize / scale;
            docEl.style.fontSize = fontSize + 'px';
        };
    // Abort if browser does not support addEventListener
    if (!doc.addEventListener) return;
    win.addEventListener(resizeEvt, recalc, false);
    doc.addEventListener('DOMContentLoaded', recalc, false);

    // iphoneX判断
    function isIphoneX(){
        return /iphone/gi.test(navigator.userAgent) && (screen.height == 812 && screen.width == 375)
    }
})(document, window);
```

### xss预防方式

``` javascript
// 敏感符号转义
function entities(s) {
    let e = {
        '"': '&quot;',
        '&': '&amp;',
        '<': '&lt;',
        '>': '&gt;'
    }
    return s.replace(/["<>&]/g, m => {
        return e[m]
    })
}
```

### 节流 / 防抖函数

``` javascript
/**
 * 节流函数: 规定在一个单位时间内，只能触发一次函数。如果这个单位时间内触发多次函数，只有一次生效。
 */
function throttle(fun, delay) {
    let last, deferTimer
    return function (args) {
        let that = this
        let _args = arguments
        let now = +new Date()
        if (last && now < last + delay) {
            clearTimeout(deferTimer)
            deferTimer = setTimeout(function () {
                last = now
                fun.apply(that, _args)
            }, delay)
        }else {
            last = now
            fun.apply(that,_args)
        }
    }
}

/**
 * 防抖函数: 在事件被触发n秒后再执行回调，如果在这n秒内又被触发，则重新计时
 */
 function debounce(fun, delay) {
    return function (args) {
        let that = this
        clearTimeout(fun.id)
        fun.id = setTimeout(function () {
            fun.call(that, args)
        }, delay)
    }
}
```

### 观察者模式

``` javascript
let Observer = (function(){
  let t__messages = {};
  return {
    regist: function(type, fn) {
      if(typeof __messages[type] === 'undefined') {
        messages[type] = [fn];
      }else {
        __messages[type].push(fn);
      }
    },
    fire: function(type, args) {
      if(!__messages[type]){
        return
      }
      let events = {
        type: type,
        args: args || {}
      },
      i = 0,
      len = __messages[type].length;
      for(;i<len;i++){
        __messages[type][i].call(this, events);
      }
    },
    remove: function(type, fn) {
      if(__messages[type] instanceof Array){
        let i = __messages[type].length -1;
        for(;i>=0;i--){
          __messages[type][i] === fn && __messages[type].splice(i, 1)
        }
      }
    }
  }
})();
```

### 模板渲染方法

``` javascript
 function formatString(str, data) {
   return str.replace(/\{\{(\w+)\}\}/g, function(match, key) {
     return typeof data[key] === undefined ? '' : data[key]
   })
 }
```

### 置换函数

``` javascript
function swap(arr, indexA, indexB) {
    [arr[indexA], arr[indexB]] = [arr[indexB], arr[indexA]];
}
```

###  惰性载入函数

``` javascript
// 原函数
function foo(){
    if(a !== b){
        console.log('aaa')
    }else{
        console.log('bbb')
    }
}

// 惰性载入优化后的函数
// ps: 第一次运行之后就会覆写这个方法，下一次再运行的时候就不会执行判断了
function foo(){
    if(a != b){
        foo = function(){
            console.log('aaa')
        }
    }else{
        foo = function(){
            console.log('bbb')
        }
    }
    return foo();
}
```

### 一次性函数

``` javascript
var sca = function() {
    console.log('msg')
    sca = function() {
        console.log('foo')
    }
}
sca()        // ==>msg
sca()        // ==>foo
sca()        // ==>foo
```

### 图片加载失败模块

```javascript
// html代码
<img src="./1.webp" data-placeholder="placeholder">
  
  
// javascript代码
let imgList = {
  default: 'default.jpg' ,
  base64: 'data:image/jpeg;base64,/9j/BLAD/4QEr',
  placeholder: 'placeholder.jpg'
}

window.addEventListener('error',function(e){
  // 获取当前元素(对象解构赋值)
  let {target} = e;
  // 获取标签名和自定义属性对象
  let {tagName,dataset} = target;
  // 获取自定义属性对象默认的time和自定义的placeholder
  let {time=1,placeholder} = dataset;
	// 判断是否为图片元素
  if (tagName === 'IMG') {
    // 当默认和自定义图片都加载失败3次以上则加载本地base64图片
    if (time<3) {
      target.src = imgList[placeholder || 'default'];
      dataset.time = time+1
    }else{
      target.src = imgList['base64']
    }
  }
},true)
```

