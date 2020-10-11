## CSS的一些易忘点

### CSS基础

1. **CSS颜色表达方式**：

* 英文字母形式：`color:black`

* 十六进制颜色：`color:#E45A65`

* rgb形式：`color:rgb(212,123,211)`

* rgba：`color:rgb(212,123,211)`，a代表的是**透明度**

  

2. **CSS引入**：`<link rel="stylesheet" type="text/css" href=#/>`

   

3. **选择器**

   1. 常用选择器：class，id

   ```HTML
   <p class="first" id="one"></p>
   ```

   > tip：一个标签可以有**多个class**，但只能有**一个id**

   2. **常用的高级选择器**

   ​          1. 后代选择器

   ​			e.g. ：`p span{}`，代表所有p标签内的所有span标签。

   ​          2. 交集选择器

   ​			e.g. ：`p.wow{}`，代表在所有p标签中，类名为*wow*的标签。

   ​          3. 子选择器

   ​			e.g. ：`p>span`，与后代选择器不同在于，子选择器强调的是子，即仅下一级的span标签。

   ```html
   <p>
     <span>son
       <span>grandson</span>
     </span>
   </p>
   ```

   > 在上面代码中，使用`p span{}`改变的是son和grandson标签的样式；而使用`p>span`仅改变son标签的样式

   ​          4. 并集选择器

   ​			e.g. ：`div main .box .big {}` ，给不同标签或不同类添加相同样式时使用。

   3. 选择器的优先级

      id优先级>class优先级>标签优先级

      

4. **盒模型**

   1. padding：盒模型的内边距

      ```css
      /* 上下左右均为10px */
      padding: 10px;
      
      /* 上下为10px，左右为20px */
      padding: 10px 20px;
      
      /* 四个值依次为：上 右 下 左 */
      padding: 10px 20px 30px 40px;
      ```

      > 计算元素大小的依据的属性：box-sizing，有两个值：
      >
      > > content-box：width，height对应内容的高度；是该属性默认值
      > >
      > > border-box：width = 内容宽度+padding+border，height = 内容宽度+padding+border

   2. border：边框

      ```css
      border: 2px solid blue
      /* 分别对应粗细，样式，颜色 */
      ```

      * 其他的样式：`dashed`为虚线

      * 无边框：`border: none`

      * 圆角属性：`border-radius`

        > 如果一个正方形容器边长为20px，则`border-radius`设置为10px时为圆形

        ```css
        border-top-left-radius: 5px;
        border-top-right-radius: 10px;
        border-bottom-left-radius: 20px;
        border-bottom-right-radius: 15px;
        
        /* 分别对四个角进行设置 */
        ```

      * 阴影：`box-shadow`

        ```css
        box-shadow: 2px 2px 2px 1px rgba(0, 0, 0, 0.2)
        /* x偏移量 | y偏移量 | 阴影模糊半径 | 阴影扩散半径 | 阴影颜色 */
        ```

        > x偏移量：在x轴上移动，向右为正
        >
        > y偏移量：在y轴上移动，向下为正
        >
        > 阴影模糊半径：边线的清晰度
        >
        > 阴影扩散半径：向外伸展的多少
        >
        > 阴影颜色：矩形下面那个矩形的背景色

   3. margin：盒模型的外边距，即两个块之间的距离

      * 两个模型间，水平距离相加，垂直距离取最大

        ```css
        .box1 {
          margin-right: 10px;
          margin-bottom:15px;
        }
        
        /* box2在box1正右方 */
        .box2 {
          margin-left: 20px;
          margin-bottom: 30px;
        }
        
        /* box3在box1正下方 */
        .box3 {
          margin-top: 20px;
        }
        
        /* box4在box2正下方 */
        .box4 {
          margin-top:20px;
        }
        
        /* 可以得到：box1与box2间水平距离为10+20=30px
                    box1与box3间垂直距离为20px
                    box2与box4间垂直距离为30px */
        ```

   4. display属性

      * none：使标签消失

      * block：块元素，可设置宽高，独占一行；例如`<div></div>`

      * inline：行内元素，不可设置宽高，可以设置padding；例如`<span></span>`

      * inline-block：行内块元素

        > 去除行内块元素间的留白：
        >
        > 1. 去除回车，将**div**标签写在一行
        >
        >    `<div class="1"></div><div class="2"></div>`
        >
        > 2. 给父元素添加word-spacing属性，值一般设置小于`-20px`
        >
        > 3. 给父元素设置`font-size： 0`，即文字大小为0；里面有文字时不可用

      

5. **CSS定位**

   1. *position*属性

      * `position: static`；静态位置，为该属性默认值

      * `position: relative`；相对定位

        ```css
        .box {
          position: relative;
          left: 20px;
          top: 20px
        }
        /* 表示距离自己原来的位置左侧20px，顶部20px */
        ```

        >  left、right、top、bottom 的调整都是相对于当前元素`static`布局位置进行的调整

      * `position: absolute`；绝对定位

        > `absolute`被称为**绝对定位**，绝对定位不为元素预留空间，通过指定元素相对于*最近的**非 static** 定位祖先元素*的偏移，来确定元素位置

      * `position: fixed`；固定定位

        有该属性的元素不会随着页面滚动而消失，会固定在原来的位置。

        > 可以理解为距离浏览器窗口的位置是不变的，比如一些网站的顶部菜单栏会一直在顶部，不会随着往下翻页面而消失

        元素覆盖问题：使用z-index属性可以解决。

        > 1. 默认非 static 元素的`z-index`都为 0
        > 2. `z-index`越大，则越在最上面，离观察者越近 
        > 3. 同样的`z-index`， 在 HTML 中的元素越靠后，则越在最上面，离观察者越近

      * `position: sticky`；粘性布局。效果是窗口中间的元素，当滚动窗口使该元素触碰到顶部时，会一直滞留在顶部，窗口拉回顶部时，该元素又会回到原来的位置

        >该布局了解即可

   2. *float*属性

      ```css
      float: left;
      /* 元素向左浮动 */
      
      float: right;
      /* 元素向右浮动 */
      ```

      

6. **CSS背景**

   * 渐变色背景

   ```css
   div {
     background:linear-gradient(to right,#d94747,#b9191a);
     }
   /* 该属性表示，渐变方向向右，由'#d94747'渐变为'#b9191a' */
   ```

   上述代码实现如下效果：

   <div style="width:300px; height:50px; background:linear-gradient(to right,#d94747,#b9191a);"></div>

   ```css
   div {
     background: linear-gradient(to right, #d94747 30%, #b9191a 70%);
   }
   /* 30% 和 70% 代表渐变开始和结束的位置
   ```

   上述代码实现如下效果：

   <div style="width:300px; height:50px; background:linear-gradient(to right,#d94747 30%,#b9191a 70%);"></div>

   





### CSS进阶

1. **CSS伪元素** **：**`::after | ::before`

   伪元素就是利用css代码在标签内部的前面，或者后面添加一个行内元素，这个行内元素可以理解为span。

   ```html
   <div class="outer"></div>
   ```

   ```css
   .outer {
     width: 300px;
     height: 50px;
     background: blue;
   }
   
   div::before {
     /* 使用空白符号占位 */
     content: '';
     display: block;
     background: yellow;
     width:50px;
     height: 30px;
   }
   ```

   上述代码实现如下效果：

   <div style="position:relative; width: 300px; height: 50px;
     background: blue;">
       <div style="position: absolute; left: 0;background: yellow;
     width:50px; height: 30px;">  
       </div>
   </div>

   

   > before和after本质上是一样的，当需要第二个行内元素时，即可使用after

   

2. **CSS伪类**

   1. 清除浮动

      ```html
      <div class="father1">
        <div class="son1"></div>
        <div class="son2"></div>
        <div class="son3"></div>
      </div>
      
      <div class="father2"></div>
      ```

      ```css
      .son1 {
        height: 100px;
        width: 33.3%;
        float: left;
        background: red;
      }
      
      .son2 {
        height: 100px;
        width: 33.3%;
        float: left;
        background: yellow;
      }
      
      .son3 {
        height: 100px;
        width: 33.3%;
        float: left;
        background: blue;
      }
      
      .father2 {
        height: 150px;
        background: black;
      }
      ```

      上述代码实现如下：

      <div class="father1">  <div class="son1" style="height: 100px; width: 33.3%; float: left; background: red;"></div>  <div class="son2" style="height: 100px; width: 33.3%; float: left; background: yellow;"></div>  <div class="son3" style="height: 100px; width: 33.3%; float: left; background: blue;"></div></div>  <div class="father2" style="height: 150px; background: black;"></div>

      > 可以发现，当给子元素添加浮动属性时，会导致父元素无法包裹住子元素，导致父元素的兄弟元素受到影响；例如这里`father2`为`father1`的兄弟元素，由于`son1，2，3`有浮动属性，导致father2的上100px高度被遮在下面，只显示了50px高度

      所以要添加清除浮动属性，添加如下代码：

      ```css
      .father1::after {
        content: '';
        display: block;
        /* 清除浮动 */
        clear: both;
      }
      ```

      新的效果如下：

      <div class="father1">  <div class="son1" style="height: 100px; width: 33.3%; float: left; background: red;"></div>  <div class="son2" style="height: 100px; width: 33.3%; float: left; background: yellow;"></div>  <div class="son3" style="height: 100px; width: 33.3%; float: left; background: blue;"></div></div>  <div class="father2" style="height: 250px; background: black;"></div>

      > 要点：哪个元素的子元素有浮动，就在**该元素**上添加清除浮动

   2. 事件伪类

      | 伪类名称 |             效果             |   书写样式    |                备注                 |
      | :------: | :--------------------------: | :-----------: | :---------------------------------: |
      |  hover   | 鼠标移动上去时，改变元素样式 | div:hover {}  |                                     |
      |  active  |   鼠标点击时，改变元素样式   | div:active {} |                                     |
      |  focus   |  获取到焦点后，改变元素样式  | input:focus{} | 一般用于具有焦点的元素，比如`input` |

      ```html
      <!DOCTYPE html>
      <html>
      	<head>
      		<meta charset="UTF-8">
      		<title></title>
      		<style type="text/css">
                  nav{
                      width: 100px;
                      height: 100px;
                      background: white;
                      border: 1px solid red;
                      border-radius: 5px;
                  }
                  nav:hover {
                      background: black;
                  }
                  nav:active {
                      background: yellow;
                  }
      		</style>
      	</head>
      	<body>
      		<nav></nav>
      	</body>
      </html>
      ```

      上述代码实现如下：

      <!DOCTYPE html>
      <html>
      	<head>
      		<meta charset="UTF-8">
      		<title>wow</title>
      		<style type="text/css">
                  aside{
                      width: 100px;
                      height: 100px;
                      background: white;
                      border: 1px solid red;
                      border-radius: 5px;
                  }
                  aside:hover {
                      background: black;
                  }
                  aside:active {
                      background: yellow;
                  }
      		</style>
      	</head>
      	<body>
      		<aside class="one" id="test-box"></aside>
      	</body>
      </html>


      > 鼠标放在白盒子上会变黑，点击会变黄

   3. 列表伪类

      ```
      <ul>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
      </ul>
      ```

      * `ul>li:first-child{}`：改变第一个li标签样式
      * `ul>li:last-child{}`：改变最后一个li标签样式
      * `ul>li:nth-child(2){}`：改变第二个li标签样式

      

3. **CSS装饰**

   1. cursor——移动在元素上时**鼠标指针**变化

      关于cursor的属性和效果：

      * pointer

        <div style="width:200px;height:30px;background: #53B7FA;cursor:pointer;"> </div>

      * default

        <div style="width:200px;height:30px;background: #53B7FA;cursor:default;"> </div>

      * text

        <div style="width:200px;height:30px;background: #53B7FA;cursor:text;"> </div>

      * move

        <div style="width:200px;height:30px;background: #53B7FA;cursor:move;"> </div>

      * grab

        <div style="width:200px;height:30px;background: #53B7FA;cursor:grab;"> </div>

      * zoom-in

        <div style="width:200px;height:30px;background: #53B7FA;cursor:zoom-in;"> </div>

      * zoom-out

        <div style="width:200px;height:30px;background: #53B7FA;cursor:zoom-out;"> </div>

   2. 文字阴影

      `text-shadow: 0px 0px 10px rgba(0,0,0,0.5);`

      效果如下：

      <span style="font-size:15px;text-shadow: 0px 0px 10px rgba(0,0,0,0.11);">不会吧不会吧f</span>
      
      
   
4. **flex布局**

   1. flex基础

      使原来上下排列的块元素变为水平排列。

      e.g.

      ```html
      <div class="outer">
        <div class="inner"></div>
        <div class="inner"></div>
        <div class="inner"></div>
      </div>
      ```

      ```css
      .outer {
      /* 设置为flex布局 */
        display: flex;
        width: 600px;
        height: 200px;
        background: white;
        border: 1px solid black;
      }
      
      .inner {
        width: 150px;
        height: 100px;
        background: orange;
        margin: 10px;
      }
      ```

      上述代码实现如下：

      <div style="display: flex;
        border: 1px solid black;">
          <div style=" width: 150px;height: 100px;background: orange;margin:10px;"></div>
          <div style=" width: 150px;height: 100px;background: orange;margin:10px;"></div>
          <div style=" width: 150px;height: 100px;background: orange;margin:10px;"></div>
      </div>

      > 当一元素设为flex布局后，子元素的float，clear和vertical-align属性将失效

   2. flex的属性

      * `justify-content/align-items`

        justify-cotent决定项目的水平排列方式。

        |    属性值     |              效果              |                备注                 |
        | :-----------: | :----------------------------: | :---------------------------------: |
        |  flex-start   | 默认值；项目向水平方向起点对齐 |                                     |
        | space-between |      在每行上均匀分配项目      |  项目间距为x，首尾元素与边缘无间距  |
        |   flex-end    |     项目向水平方向终点对齐     |                                     |
        | space-around  |      在每行上均匀分配项目      | 项目间距为2x，首尾元素与边缘间距为x |
        |    center     |      项目在水平方向上居中      |                                     |
        | space-evenly  |      在每行上均匀分配项目      |  项目间距和首尾元素与边缘间距均为x  |

        align-items决定项目的垂直排列方式。

        |   属性值   |                          效果                          |
        | :--------: | :----------------------------------------------------: |
        | flex-start |                项目向垂直方向的起点对齐                |
        |  stretch   | 默认值；项目在垂直方向上被拉伸到与容器相同的高度或宽度 |
        |  flex-end  |                项目向垂直方向的终点对齐                |
        |  baseline  |              按项目的第一行文字的基线对齐              |
        |   center   |                  项目在垂直方向上居中                  |

      * flex-wrap

        flex容器中，默认情况下项目是不会换行的；所以当项目总宽度超过容器宽度，那项目的宽度会被自动压缩，设定了的宽度此时就不奏效了；所以需要设置`flex-wrap`的值改善这种情况。

        flex-wrap: nowrap | wrap | wrap-reverse

        * nowrap：默认值；不换行
        * wrap：换行，第一行在上方
        * wrap-reverse：换行，第一行在下方

      * flex：1 | none

        在一行排不下所有项目的情况下，要求项目既能排在一行，宽度又不被压缩；此时就要调整**flex**属性。

        flex：none；不允许项目放大和压缩。

        flex：1；项目自动填充剩余空间。

        > 可以指定任意的单个项目使其充满剩余空间，只需给该项目设置`flex：1`即可
        >
        > `flex：1`还可以实现网页自适应浏览器宽度的效果

      * flex-direction

        改变flex-direction的值可以改变项目排列的方式。

        ```css
        /* 默认值；项目水平正向排列 */
        flex-direction: row;
        
        /* 项目水平逆向排列 */
        flex-direction: row-reverse;
        
        /* 项目垂直正向排列 */
        flex-direction: column;
        
        /* 项目垂直逆向排列 */
        flex-direction: column-reverse;
        ```

        e.g.

        没设置flex-direction时：

        <div style="display:flex;">
            <div style="width:100px;height:100px;background:blue;margin:25px;"></div>
            <div style="width:100px;height:100px;background:blue;margin:25px;"></div>
            <div style="width:100px;height:100px;background:blue;margin:25px;"></div>
        </div>

        设置`flex-direction: column`：

        <div style="display:flex;flex-direction:column">
            <div style="width:100px;height:100px;background:blue;margin:25px;"></div>
            <div style="width:100px;height:100px;background:blue;margin:25px;"></div>
            <div style="width:100px;height:100px;background:blue;margin:25px;"></div>
        </div>

        

5. 文本超出省略

   1. 单行文本超出省略

      为文本设置如下属性：

      ```css
      /* 强制不换行 */
      white-space: nowrap;
      /* 隐藏超出部分 */
      overflow: hidden;
      /* 用省略号代替剩余内容 */
      text-overflow: ellipsis;
      ```

   2. 多行文本超出省略

      目前只有WebKit内核的浏览器支持CSS实现多行文本溢出省略：

      ```css
      /* 隐藏超出部分 */
      overflow : hidden;
      /* 文本超出就用省略号 */
      text-overflow: ellipsis;
      /* 把对象作为弹性伸缩盒子模型显示 */
      display: -webkit-box;
      /* WebKit内核的浏览器的私有属性，设置文本超出2行就用省略号 */
      -webkit-line-clamp: 2;
      /* WebKit内核的浏览器的私有属性，设置或检索伸缩盒对象的子元素的排列方式 */
      -webkit-box-orient: vertical;
      ```

      > 非WebKit内核浏览器可以使用JavaScript来实现😁

      

6. **CSS预处理器：Scss**

   SASS是一款CSS的预编译器，为CSS增加了一些编程的特性；当使用这类语言时，代码需被编译成CSS才能被浏览器理解。

     

   SASS比CSS更像一门编程语言，包含了变量，函数，控制语句，导入，嵌套等高级功能。

     

   Scss是Sass为了兼容CSS3而引入的新的语法；其语法完全兼容CSS3，并且继承了Sass的强大功能。也就是说，任何标准的CSS3样式表都是具有相同语义的有效的Scss文件。

     

   1. 变量

      ```scss
      $width: 10px;
      
      div {
        width: $width;
      }
      ```

      编译为CSS后：

      ```css
      div {
        width: 10px;
      }
      ```

      > 变量同样可以是其他类型数据，如字符串，布尔值等

      * 插值法

        ```scss
        $param: "block";
        
        div {
        /* #{}形式的插值 */
          display: inline-#{$param};
        }
        ```

        编译为CSS后:

        ```css
        div {
          display: inline-block;
        }
        ```

   2. 嵌套

      * 常规嵌套：

        ```scss
        div {
          display: inline-block;
          
          p {
            font-size: 12px
            
            span {
              font-weight: 600;
            }
          }
        }
        ```

        编译为CSS后：

        ```css
        div {
            display: inline-block;
        }
        
        div>p {
            font-size: 12px;
        }
        
        div p span {
            font-weight: 600;
        }
        ```

      * 父选择器：**&**

        ```scss
        div{
          background: blue;
          
          &:hover {
            background: green;
          }
        }
        
        ul>li {
          font-size: 12px;
          
          &:nth-child(2){
            font-size: 18px;
          }
        }
        ```

        编译为CSS后：

        ```css
        div {
          background: blue;
        }
        
        div:hover {
            background: green;
        }
        
        ul>li {
            font-size:12px;
        }
        
        ul>li:nth-child(2) {
            font-size: 18px;
        }
        ```

        > tips：比如.box中有一个.box_double类同样可以使用：`&_double`

   3. 复用：`mixin/include`

      * 基础复用

        ```scss
        //定义复用代码块
        @mixin square {
            width: 10px;
            height: 10px;
        }
        
        .box1 {
            @include square;
        }
        
        .box2 {
            @include square;
        }
        ```

        编译为CSS后：

        ```css
        .box1 {
            width: 10px;
            height: 10px;
        }
        
        .box2 {
            width: 10px;
            height: 10px;
        }
        ```

      * 有参数的复用

        ```scss
        @mixin square($size) {
            width: $size;
            height: $size;
        }
        
        //还可以设置参数的默认值
        @mixin fontStyle($size: 12px) {
            font-size: $size;
            text-align: center;
        }
        
        .box {
            @include square(50px);
        }
        
        .line1 {
            @include fontStyle;
        }
        
        .line2 {
            @include fontStyle(20px);
        }
        ```

        编译为CSS后：

        ```css
        .box {
            width: 50px;
            height: 50px;
        }
        
        .line1 {
            fonr-size: 12px;
            text-align: center;
        }
        
        .line2 {
            font-size: 20px;
            text-align: center;
        }
        ```

        

7. **媒体查询**

   指在只有满足特定条件的时候，才使用对应的CSS属性块。

   ```css
   @media screen and (max-width: 1000px) {
     .box {
       display: none;
     }
   }
   ```

   上述代码的意思是，在浏览器宽度小于等于1000px时，使`.box`消失。

   > screen：告知设备在打印页面时使用衬线字体，在屏幕上显示时用无衬线字体。如果网页不需要考虑用户去打印，就可以去掉

   使用`min-width`时，即当宽度大于该值时，使用特定布局。

   不同条件间使用`and`连接：

   ```css
   @media screen and (max-width: 1000px) and (min-width: 500px) {
      /* 大于等于500px，小于等于1000px时应用的布局 */
   }
   ```

   * 断点：条件中的值（如1000px，500px）称作断点

     当遇到冲突的查询条件时，由于CSS中，越往后的样式优先级越高，所以需要遵循一定的规则。

     1. 使用max-width表示条件时，大的断点放上面
     2. 使用min-width表示条件时，小的断点放上面



### Other style

* Grid layout

  Using meta tag to declare responsive supported page:

  ```html
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  ```

  Grid layout example:

  ```html
  <div class="grid">
  	<header>header</header>
      <nav>nav</nav>
      <main>main</main>
      <section id="fir">section one</section>
      <section id="sec">section two</section>
      <footer>footer</footer>
  </div>
  ```

  ```css
  * {
      margin: 0;
      padding:0;
  }
  
  .grid {
      display: grid;
      grid-template-columns: 1fr;
      /* grid-template-rows only necessary when require certain number of rows */
      grid-template-rows: 1fr 1fr 1fr 1fr 1fr 1fr;
      /* Using grid-area name already set to display layout */
      grid-template-areas: 
      "header"
      "nav"
      "main"
      "fir-section"
      "sec-section"
      "footer";
      grid-gap: 10px; /* grid-gap sets the gap between each cell of the grid o*/
  
  header {
      /* Set grid area name for each tag  */
      grid-area: header;
      background: red;
  }
  
  nav {
      /* This attribute allow the parent surround innreHTML and align left | right | center */
      /* justify-self: start | end |center; */
      grid-area: nav;
      background: blue;
  }
  
  main {
      grid-area: main;
      background: yellow;
      
  }
  
  #fir {
      grid-area: fir-section;
      background: aqua;
  }
  
  #sec {
      grid-area: sec-section;
      background: blueviolet;
  }
  
  footer {
      grid-area: footer;
      background: antiquewhite;
  }
  
  /* Set media query to cater to large devices like a labtop */
  @media screen and (min-width: 736px) {
      .grid {
          display: grid;
          grid-template-columns: 1fr 500px 500px 1fr;
          /* grid-template-rows only necessary when require certain number of rows */
          grid-template-rows: 1fr 1fr 1fr 1fr 1fr;
          /* Using grid-area name already set to display layout */
          grid-template-areas: 
          ". header header ."
          ". nav nav ."
          ". main main ."
          ". fir-section sec-section ."
          ". footer footer .";
      }
  }
  ```