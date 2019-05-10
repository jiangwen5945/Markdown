## HTML

---

- [x] 语义化

  - 页面结构更加清晰和可读性，有利于团队开发和维护
  - 方便其他设备解析
  - 有利于SEO，搜索引擎根据标签来确定上下文和各个关键字的权重
  - 易于用户阅读，样式丢失的时候能让页面呈现清晰的结构

  

- [x] H5新增标签特性

  |    标签名    |                             说明                             |
  | :----------: | :----------------------------------------------------------: |
  |  <article>   |                定义文章，规定独立的自包含内容                |
  |   <aside>    |                    定义页面内容之外的内容                    |
  |  <section>   |                    定义文档中的小节、区段                    |
  |   <header>   |                   定义section或page的页眉                    |
  |   <footer>   |                   定义section或page的页脚                    |
  |    <main>    |                      定义文档的主要内容                      |
  |    <nav>     |                         定义导航链接                         |
  |    <bdi>     |       定义文本的文本方向，使其脱离其周围文本的方向设置       |
  |   <canvas>   |                         定义图形画布                         |
  |  <command>   |              定义命令按钮  (仅ie9支持这个标签)               |
  |  <datalist>  |                定义下拉列表（配合input使用）                 |
  |  <details>   | 定义元素的细节:页面只显示summary里的内容，点击之后才显示详细内容 |
  |  <summary>   |                为<details>元素定义可见的标题                 |
  |   <embed>    |                    定义外部交互内容或插件                    |
  | <figcaption> |                     定义figure元素的标题                     |
  |   <figure>   |                           定义媒介                           |
  |   <keygen>   |                         定义生成密钥                         |
  |    <mark>    |                       定义有记号的文本                       |
  |   <meter>    |                    定义预定义范围内的度量                    |
  |   <output>   |                      定义输出的一些类型                      |
  |  <progress>  |                   定义任何类型的任务的进度                   |
  |   <audio>    |              定义声音内容，比如音乐或其他音频流              |
  |   <source>   |                          定义媒介源                          |
  |   <dialog>   |                       定义对话框或窗口                       |
  |    <time>    |                        定义日期/时间                         |
  |   <track>    |                定义用在媒体播放器中的文本轨道                |
  |   <video>    |                           定义视频                           |
  |    <wbr>     |                  定义英文字符自动进行软换行                  |

  > tip : 对于一段主题性的内容，则就适用`section`，而假如这段内容可以脱离上下文，作为完整的独立存在的一段内容，则就适用 `article`  

  

- [x] input和textarea的区别

  - 有无value属性
  - 是否闭合标签

  

- [x] 用div模拟textarea的实现

  ```css
  .editBox {
              width: 400px;
              min-height: 100px;
              max-height: 300px;
              _height: 100px; /* IE6 */
              padding: 3px;
              outline: 0;
              border: 1px solid #a0b3d6;
              overflow-y: auto; /* 超过最大高度就出现滚动条 */
              _overflow-y: visible;
          }
  
  <div class="editBox" contenteditable></div>
  ```

  

- [x] 移动设备忽略将页面的数字识别为电话号码

  <meta name = "format-detection" content = "telephone=no">





## CSS

---

## 

- [x] 盒模型

  - 盒模型由内而外为：内容（content）、内边距（padding）、边框（border）、外边距（margin）
  - CSS的盒子模型分为：IE 盒模型和标准 W3C 盒模型
  - **区别**：设置宽度时标准模型只包含内容（content），而IE盒模型还包含内边距（padding）和边框（border）
  
  
  
- [x] flex弹性布局

  - **基本概念：**采用 Flex 布局的元素，称为 Flex 容器（flex container）；它的所有子元素自动成为容器成员，称为 Flex 项目（flex item）

  容器属性：

  | 属性名          | 说明介绍                              | 默认值      |
  | --------------- | ------------------------------------- | ----------- |
  | flex-direction  | 项目的排列方向                        | row         |
  | flex-wrap       | 项目是否换行                          | nowrap      |
  | flex-flow       | `flex-direction`和`flex-wrap`简写组合 | row  nowrap |
  | justify-content | 项目在主轴上的对齐方式                | flex-start  |
  | align-items     | 项目在交叉轴上如何对齐                | stretch     |
  | align-content   | 定义多根轴线的对齐方式（单轴线无效）  | stretch     |

  项目属性：

  | 属性名      | 说明介绍                                         | 默认值                              |
| ----------- | ------------------------------------------------ | ----------------------------------- |
  | flex-grow   | 项目的放大比例                                   | 0：即使剩余空间，该项目也不放大     |
  | flex-shrink | 项目的缩小比例                                   | 1：如果空间不足，该项目将缩小       |
  | flex-basis  | 分配多余空间之前，项目占据的主轴空间             | autoC即项目的本来大小               |
  | flex        | `flex-grow`, `flex-shrink` 和 `flex-basis`的简写 | 0  [1]  [auto] ：后两个属性可选     |
  | align-self  | 允许单个项目有与其他项目不一样的对齐方式         | auto：继承父元素的`align-items`属性 |
  | order       | 项目的排列顺序                                   | 0 ：数值越小，排列越靠前            |
  
  > tip ：`flex`属性有两个快捷值：auto `(1 1 auto)` 和 none `(0 0 auto)` ；
  > 	    `flex：1`、`flex：auto`、`flex：1 1 auto`三者表达的意思相同 ；
  
  


- [x] css单位

- [x] css选择器
- [x] BFC清除浮动

- [x] 层叠上下文

- **什么是层叠上下文：**元素拥有z轴叠层环境
- **什么是层叠等级：**
  1. 简单理解拥有层叠上下文环境 层叠等级高与普通元素；
  2. 处于同一个层叠上下文中(层叠环境)，比较层叠等级；否则比较他们所处的层叠上下文(层叠环境)的层叠等级。
- **如何产生层叠上下文：**
  1. 根元素html
  2. 普通元素设置`position`属性为**非**`static`值并设置`z-index`属性为具体数值
  3. CSS3中的新属性也可以产生层叠上下文
- **“层叠上下文”和“层叠等级”是一种概念，而这里的“层叠顺序”是一种规则**


- **层叠顺序**：正z-index > 定位元素 > 内联元素 > 浮动元素 > 块级元素 > border > background > 负z-index

> 参考链接：[彻底搞懂CSS层叠上下文、层叠等级、层叠顺序、z-index](https://www.jianshu.com/p/0f88946a0746)


- [x] 常用页面布局
- [x] 响应式布局
- [x] CSS预处理（sass、less）、后处理（postcss）
- [x] css3新特性
- [x] display有哪些取值
- [x] 相邻的两个inline-block节点为什么会出现间隔，怎么解决
- [x] meta viewport移动端适配
- [x] CSS实现宽度自适应100%，宽高16:9的比例矩形
- [x] rem单位布局的优缺点
- [x] 画三角形
- [x] 1像素边框问题