<!--
 * @Author: Jason
 * @Date: 2019-08-18 14:27:26
 * @Github: https://github.com/JasonLaii
 * @Description: 
 * @LastEditTime: 2019-08-18 15:11:07
 -->

该文章参考转载自[https://github.com/chokcoco/iCSS/issues/56]

### IFC、BFC、GFC、FFC

*FC 即为 Formatting Contexts, 格式化上下文。
*FC 可称作为视觉格式化模型。CSS视觉格式化模型是用来处理文档 将它显示在视觉媒体上的机制。这是CSS的一个基础概念。

常见的是 CSS2.1 规范中的 IFC(Inline Formatting Contexts)与BFC(Block Formatting Contexts)。
而 GFC(Grid Formatting Contexts) 和FFC(Flex Formatting Contexts) 是CSS3新增规范。

*FC是CSS视觉渲染的一部分，用于决定盒模型的布局、其子元素将如何定位以及与其他元素的关系

### Box

Box是CSS布局的对象和基本单位，直观的说就是一个页面是由很多Boxes组成的，元素的类型和display属性决定了Box的类型。
  1.  block-level Box   --- 块级盒
  2.  inline-level Box  --- 行内级盒
  3.  flex-level Box    --- 弹性容器
  4.  grid-level Box    --- 栅格容器

#### BFC(Block Formatting Contexts)
[关于BFC的布局规则请看这里](/消失的边界线问题/README.md)

#### IFC(Inline Formatting Contexts)

IFC 只有在一个块级元素中仅包含内联级别元素时才会生出

##### 布局规则
  1.  内部盒子会在水平方向，一个接一个的放置。
  2.  这些盒子垂直方向的起点从 包含块盒子 的顶部开始
  3.  摆放这些盒子的时候，他们在水平方向上的    padding、border、margin 所占用的空间都会被考虑在内。
  4.  在垂直方向上，这些框可能会以不同形式来对齐，他们可能会使用底部或顶部对齐，也可能通过其内部文本基线(baseline) 对齐。
  5.  能把在一行上的框都完全包含进去的一个矩形区域， 被称为该行的行框。 行框的宽度是由包含块 盒存在的浮动来决定的
  6.  IFC中的line box 一般左右边都贴紧其包含块，但是会因为float元素的存在发生变化。float元素会位于IFC 与 line box 之间，使得 line box 宽度缩短
  7.  IFC中的 line box 高度由CSS行高计算规则来确定，同个 IFC下的 多个line box 高度可能不同

  8.  ***当 inline-level boxes 的总宽度少于包含他们的 line box 时，其水平渲染规则由 text-align属性来确定，如果取值为justify，那么浏览器会对inline-boxes(注意不是inline-table 和 inline-block boxes) 中的文字和空格作出拉伸***
  9.  ***当一个 inline box 超过 line box 的宽度时，它会被分割成多个boxes，这些boxes被分布在多个line box里。如果一个 inline box 不能被分割（比如只包含单个字符，或word-breaking机制被禁用，或该行内框售white-space属性值为nowrap或pre影响），那么这个inine box 将溢出这个line box***
  
##### IFC的用法
  1.  水平居中：当一个块元素要在环境中水平居中时，设置其为inline-block 则会在外层产生IFC，通过设置text-align则可以使其居中

    值得注意的是，设置一个块为inline-block，会在内部生成一个BFC。

  2.  垂直居中：创建一个IFC，用其中一个元素撑开父元素的高度，设置其为vertical-align: middle, 其他行内元素则可以在此父元素下垂直居中






