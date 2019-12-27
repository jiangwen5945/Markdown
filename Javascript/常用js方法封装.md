### 1.截取指定字节数的字符串

```javascript
/**
 * 截取指定字节的字符串
 * @param str 要截取的字符穿
 * @param len 要截取的长度，根据字节计算
 * @param suffix 截取前len个后，其余的字符的替换字符，一般用“…”
 * @returns {*}
 */
function cutString(str, len, suffix) {
  if (!str) return "";
  if (len <= 0) return "";
  if (!suffix) suffix = "";
  var templen = 0;
  for (var i = 0; i < str.length; i++) {
    if (str.charCodeAt(i) > 255) {
      templen += 2;
    } else {
      templen++
    }
    if (templen == len) {
      return str.substring(0, i + 1) + suffix;
    } else if (templen > len) {
      return str.substring(0, i) + suffix;
    }
  }
  return str;
}

```



### 2.常用日期时间函数

```javascript
/*
* 时间戳格式化显示
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



### 3.图片加载失败模块

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



### 4.防抖&节流函数

```javascript
/*
防抖函数: 只执行一次传入的函数(类似于弹簧,只在结束或者开头的时候执行一次) 
fn:需要执行防抖的函数
immediate: 是否立即执行传入的函数
*/
function debounce(fn, wait = 300, immediate = false) {
  let timer,res;
  let myDebounce = function (...args) {
    if (timer) {
      clearTimeout(timer)
    }
    if (immediate) {
      if (!timer) {
        res = fn.apply(this, args)
      }
      timer = setTimeout(() => {
        timer = null
      }, wait);
    } else {
      timer = setTimeout(() => {
        fn.apply(this, args)
      }, wait);
    }
    return res;
  }
  myDebounce.cancel=(()=>{
    clearTimeout(timer)
  })

  return myDebounce
}


/*
节流函数:在一定时间段内执行一次(类似于水龙头每隔500ms滴一滴水) 
*/
// 时间戳方式实现
function thorttle(fn, interval = 500) {
  preTime = Date.now()
  return function (...args) {
    nowTime = Date.now()
    if (nowTime - preTime >= interval) {
      fn.apply(this, args)
      preTime = Date.now()
    }
    // timer = setTimeout(() => {
    //     fn.apply(this, args)
    // }, interval);
  }

}
// 定时器方式实现
function thorttle2(fn, interval = 500) {
  let timer = null;
  return function (...args) {
    if (!timer) {
      timer = setTimeout(() => {
        fn.apply(this, args);
        clearTimeout(timer);
        timer = null
      }, interval);
    }
  }
}
```

