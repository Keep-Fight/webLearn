## HTML & CSS 学习总结

## HTML

### 简介

1. 什么是HTML：HTML 是用来描述网页的一种语言。
2. HTML使用标记标签来描述网页

### 基本格式

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <!-- 设置字符格式 -->
    <meta charset="UTF-8"> 
    <!-- 兼容IE -->
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <!-- 标题 -->
    <title>Document</title>
</head>
<body>
    
</body>
</html>
```



### 常用元素

#### 1. 文本元素

```html
<body>
        <!-- h 标题元素-->
        <h1>1级标题</h1>
        <h2>2级标题</h2>
        <h3>3级标题</h3>
        <h4>4级标题</h4>
        <h5>5级标题</h5>
        <h6>6级标题</h6>

		<!-- p 段落元素-->
        <p>段落内容</p>

		<!-- span 无语义-->
		<span style="color:red">红</span>
		<span style="color:green">绿</span>
		<span style="color:blue">蓝</span>

     	<!-- pre 预格式化文本元素-->
		<!-- 在pre元素内部出现的内容，会按照源代码格式显示到页面上，不会将首尾空格消除 -->
        <code style="white-space:pre">
            var i = 2;
            if(i){
                console.log(i);
            }
        </code>
    
</body>
```

#### 2. 超链接

- href属性

```html
<!--
普通链接
-->
<a href="https://douyu.com">百度</a>

<!--
锚链接
实现标题到段落的跳转
-->
<a href="#chapter1">章节1</a>
<a href="#chapter2">章节2</a>
<a href="#chapter3">章节3</a>

<h2 id="chapter1">章节1</h2>
<p>长段部内容</p>
<h2 id="chapter2">章节1</h2>
<p>长段部内容</p>
<h2 id="chapter3">章节1</h2>
<p>长段部内容</p>

<!--
功能链接
-->

<!--弹窗-->
<a href="javascript:alert('你好！')">弹出：你好！</a>
<!--发送邮件-->
<a href="mailto:1292048531@qq.com">点击给我发送邮件</a>
```

- target属性

```html
<!--
 _self：在当前页面窗口中打开，默认值
 _blank: 在新窗口中打开
-->

<a href="https://baidu.com" target="_blank" title="百度">斗鱼直播</a>

```

#### 3. 图片元素

```html
 <img usemap="#solarMap" src="./img/solar.jpg" alt="这是一张太阳系的图片">
```

#### 4. 多媒体元素

-  video 视频元素 audio 音频元素
-  controls: 控制控件的显示，取值只能为controls
- 某些属性，只有两种状态：1. 不写  2. 取值为属性名，这种属性叫做布尔属性
- 布尔属性，在HTML5中，可以不用书写属性值
- autoplay: 布尔属性，自动播放
- muted: 布尔属性，静音播放
- loop: 布尔属性，循环播放
- **兼容性：不同浏览器以及相同浏览器不同版本都会有兼容性不一致的问题**

```html
<audio src="./media/shamoluotuo.mp3" controls autoplay loop muted></audio>

<video controls autoplay muted loop style="width:500px;">
        <source src="media/open.mp4">
        <source src="media/open.webm">
        <p>
            对不起，你的浏览器不支持video元素，请点击这里下载最新版本的浏览器
        </p>
</video>

```

#### 5. 列表元素

属性：reversed：倒置排序（布尔属性）

- 有序列表 (ol)

```html
<ol reversed>
    <li>列表单元</li>
    <li>列表单元</li>
    <li>列表单元</li>
</ol>    
```

- 无序列表 (ul)

```html
<ul reversed>
    <li>列表单元</li>
    <li>列表单元</li>
    <li>列表单元</li>
</ul>
```

- 定义列表

**dl**: definition list（定义列表）

**dt**: definition title（属于标题）

**dd**: definition description  （术语的描述）

```html
<dl>
       <dt>HTML</dt>
       <dd>
            超文本标记语言，XXXXXX
       </dd>

       <dt>元素</dt>
       <dd>
            组成HTML文档的单元，每个xxxxx
       </dd>
</dl>
 
```

#### 6. 容器元素

**header**: 通常用于表示页头，也可以用于表示文章的头部

**footer**: 通常用于表示页脚，也可以用于表示文章的尾部

**article**: 通常用于表示整篇文章

**section**: 通常用于表示文章的章节

**aside**: 通常用于表示侧边栏

 ```html
 <!--基本排版-->
 <article>
     <header>
     </header>
     <section></section>
     <section></section>
     <section></section>
     <section></section>
     
 </article>
 
 <aside>
 </aside>
 
 <footer>
 </footer>
 ```

#### 7. 表单元素

#####  1. **input** 输入框

```html
<!-- type属性:输入框类型

- type: text， 普通文本输入框
- type：password，密码框
- type: date, 日期选择框，兼容性问题
- type: search, 搜索框，兼容性问题
- type: number，数字输入框
- type: checkbox，多选框
- type: radio，单选框

- 当type值为reset、button、submit时，input表示按钮。
-->

<!-- 
- value属性：输入框的值
- placeholder属性：显示提示的文本，文本框没有内容时显示
-->


- value属性：输入框的值
- placeholder属性：显示提示的文本，文本框没有内容时显示

 <input type="text" placeholder="请输入账号">


```



##### 2. **select** 下拉选择框元素

```html
<!--
selected:默认选择
-->
<select>
	<option>选项1</option>
	<option>选项2</option>
	<option selected>选项3</option>
</select>
```



##### 3. **textarea ** 文本域元素

```html
请填写简介：
<textarea style="width:500px;height:300px;" placeholder="请输入简介"></textarea>
```

##### 4. button 按钮元素

```html
<!--
type属性：reset(重置)、submit、button，默认值submit(提交)
-->

<button type="button">这是一个按钮</button>
```

##### 5. label  标签元素

```html
<p>
        请选择性别：
        <label>
            <input name="gender" type="radio">
            男
        </label>
        <label>
            <input name="gender" type="radio">
            女
        </label>
</p>
```

#### 8. 其他元素

- abbr :缩写词

- time: 提供给浏览器或搜索引擎阅读的时间

- b : 以前是一个无语义元素，主要用于加粗字体

- br:主要用于在文本中换行

- hr: 主要用于分割

- meta: 还可以用于搜索引擎优化（SEO）

-  link: 链接外部资源（CSS、图标）

   rel属性：relation，链接的资源和当前网页的关系

   type属性：链接的资源的MIME类型

## CSS

### 简介

- **CSS** 指的是层叠样式表* (*C*ascading *S*tyle *S*heets)
- CSS 描述了如何在屏幕、纸张或其他媒体上显示 HTML 元素

### 基础

#### 1. 添加样式

- **CSS** = 选择器+声明块

```css
选择器名{
    声明块
}
```

- **选择器**

	1. ID选择器：选中的是对应id值的元素
	1. 元素选择器: 所有元素都被选择
	1. 类选择器

- **声明块**：声明块中包含很多声明（属性），每一个声明（属性）表达了某一方面的样式。

- **书写位置**

```html
<!--内部样式表-->
<div style=""> </div>

<!--元素样式表-->
<style>
    样式内容
</style>

<!--外部样式表-->
<link rel="stylesheet" href="./css/index.css">
```

#### 2. 常用样式声明

- **color** : 元素内部的**文字颜色**
- **background-color**:元素背景颜色
- **font-size**：元素内部文字的尺寸大小
- **font-weight**：文字粗细程度，可以取值数字，可以取值为预设值
- **text-decoration**：文本修饰，给文本加线
- **text-indent**：首行文本缩进
- **line-height**：每行文本的高度，该值越大，每行文本的距离越大。
- **width**：宽度
- **height**：高度
- **letter-space**：文字间隙
- **text-align**：元素内部文字的水平排列方式

更多样式可查询W3C在线教程 https://www.w3school.com.cn/

#### 3. 选择器

-  ID选择器

```css
#id名称{
    声明块
}

#app{
    height:100px;
}
```

- 元素选择器

```css
元素名{
    声明块
}

div{
    height:100px;
}
```

- 类选择器

```css
.class名称{
    声明块
}

.app{
    height:100px;
}
```



- 通配符选择器：* 选中所有元素

```css
*{
    height:100px;
}
```

- 属性选择器：根据属性名和属性值选中元素

```css
[href="values"]{
    height:100px;
}
```

- 伪类选择器

```css
1）link: 超链接未访问时的状态

2）visited: 超链接访问过后的状态

3）hover: 鼠标悬停状态

4）active：激活状态，鼠标按下状态
```

```css
a:link {
    color: chocolate;
}
```

- 伪元素选择器: before  after

```css
span::before {
    content: "《";
    color: red;
}
```

- **选择器的组合**

```css
1. 后代元素 ——  空格
2. 子元素 ——  >
3. 相邻兄弟元素 ——  +
4. 后面出现的所有兄弟元素 ——  ~
5. 多个选者器并列用 , 隔开
```

#### 4. 层叠

- **比较重要性**

​     作者样式表中的**!important样式** > 作者样式表中的**普通样式**>浏览器**默认样式表**中的样式

- **比较特殊性**

​	总体规则：选择器选中的范围**越窄**，越**特殊**

​	**stysle>id>.class>元素**

​	**link > visited > hover > active**

- **比较源次序**:代码书写靠后的胜出

- **应用**: 重置样式表(覆盖默认样式)   

#### 5. 继承

- 子元素会继承父元素的某些CSS属性
- 通常，跟文字内容相关的属性都能被继承

#### 6. 属性值计算

- 一个元素，从所有属性都没有值，到所有的属性都有值，这个计算过程，叫做属性值计算过程
- inherit：手动（强制）继承，将父元素的值取出应用到该元素
- initial：初始值，将该属性设置为默认值

#### 7.盒模型

**box**：盒子，每个元素在页面中都会生成一个矩形区域（盒子）

**盒子类型**：

1. **行盒**，display等于inline的元素 
2. **块盒**，display等于block的元素

浏览器默认样式表设置的块盒：容器元素、h1~h6、p

常见的行盒：span、a、img、video、audio

##### **盒子的组成部分**

- **内容  content**

​			width、height，设置的是盒子内容的宽高

​			内容部分通常叫做整个盒子的**内容盒 content-box**

- **填充(内边距)  padding** ：盒子边框到盒子内容的距离

​			填充区+内容区 = **填充盒 padding-box**

- **边框  border**：

​			边框 = 边框样式 + 边框宽度 + 边框颜色

​			边框样式：border-style

​			边框宽度：border-width

​			边框颜色：border-color

​			边框+填充区+内容区 = **边框盒 border-box**

- **外边距  margin**：边框到其他盒子的距离

​			

#### 8. 常规流

- 布局

​			**规则**：块盒独占一行，行盒水平依次排列

​			**包含块（containing block）**：每个盒子都有它的包含块，包含块决定了盒子的排列区域。

1. 每个块盒的总宽度，必须刚好等于包含块的宽度

​			宽度的默认值是auto

​			margin的取值也可以是auto，默认值0

​			**auto**：将剩余空间吸收掉

​			width 吸收能力强于margin

​			若宽度、边框、内边距、外边距计算后，仍然有剩余空间，该剩余空间被margin-right全部吸收

​			在常规流中，块盒在其包含快中居中，可以定宽、然后左右margin设置为auto。



2. 每个块盒垂直方向上的auto值

​			**height**: auto， 适应内容的高度

​			**margin**: auto， 表示0



3. 百分比取值

​		高度的百分比：

​		1）. 包含块的高度是否取决于子元素的高度，设置百分比无效

​		2）. 包含块的高度不取决于子元素的高度，百分比相对于父元素高度



4.  上下外边距的合并

​			1）两个常规流块盒，上下外边距相邻，会进行合并。

​			2）两个外边距取最大值。

#### 9. 浮动(float)

- **浮动的基本特点**

​			float: left =>左浮动，元素靠上靠左

​			float: right =>右浮动，元素靠上靠右

​			默认值为**none**

​			1) 当一个元素浮动后，元素必定为块盒(更改display属性为block)

​			2) 浮动元素的包含块，和常规流一样，为父元素的内容盒

- **盒子尺寸**

			1) 宽度为auto时，适应内容宽度
			1) 高度为auto时，与常规流一致，适应内容的高度
			1) margin为auto，为0.
			1) 边框、内边距、百分比设置与常规流一样

- **盒子排列**

1. 左浮动的盒子靠上靠左排列

2. 右浮动的盒子考上靠右排列

3. 浮动盒子在包含块中排列时，会避开常规流块盒

4. 常规流块盒在排列时，无视浮动盒子

5. 行盒在排列时，会避开浮动盒子

6. 外边距合并不会发生

- **高度坍塌**

高度坍塌的原因：常规流盒子的自动高度，在计算时，不会考虑浮动盒子

清除浮动，涉及css属性：clear

```css
 .clearfix::after {
        content: "";
        display: block;
        clear: both;
  }
/*
- 默认值：none
- left：清除左浮动，该元素必须出现在前面所有左浮动盒子的下方
- right：清除右浮动，该元素必须出现在前面所有右浮动盒子的下方
- both：清除左右浮动，该元素必须出现在前面所有浮动盒子的下方
*/
```

#### 10. 定位 (position)

##### 1. **position属性**

- 默认值：static，静态定位（不定位）

- relative：相对定位

- absolute：绝对定位

- fixed：固定定位

​	一个元素，只要position的取值不是static，认为该元素是一个定位元素。

​	定位元素会脱离文档流（相对定位除外）



一个脱离了文档流的元素：

1. 文档流中的元素摆放时，会忽略脱离了文档流的元素
2. 文档流中元素计算自动高度时，会忽略脱离了文档流的元素

##### 2. **相对定位**

​	不会导致元素脱离文档流，只是让元素在原来位置上进行偏移。

​	可以通过四个CSS属性对设置其位置：

- left
- right
- top
- bottom

​	盒子的偏移不会对其他盒子造成任何影响。

##### 3. **绝对定位**

- 宽高为auto，适应内容

- 包含块变化：找祖先中第一个定位元素，该元素的填充盒为其包含块。若找不到，则它的包含块为整个网页（初始化包含块）

##### 4. **固定定位**

​		其他情况和绝对定位完全一样。

​		包含块不同：固定为视口（浏览器的可视窗口）

##### 5. **定位下的居中**

 	某个方向居中：

- 定宽（高）

- 将左右（上下）距离设置为0

- 将左右（上下）margin设置为auto

​	绝对定位和固定定位中，margin为auto时，会自动吸收剩余空间

##### 6.**多个定位元素重叠时**

​	堆叠上下文

​	设置z-index，通常情况下，该值越大，越靠近用户

​	只有定位元素设置z-index有效

​	z-index可以是负数，如果是负数，则遇到常规流、浮动元素，则会被其覆盖

##### 7. **注意**

- 绝对定位、固定定位元素一定是块盒
- 绝对定位、固定定位元素一定不是浮动
- 没有外边距合并













