<!--
 * @Author: Jason
 * @Date: 2019-08-18 11:02:50
 * @Github: https://github.com/JasonLaii
 * @Description: 
 * @LastEditTime: 2019-08-18 11:45:36
 -->
转载自[https://www.jianshu.com/p/7e04ed3f4bea]

### BFC
BFC(Block Formatting Context) 块级格式化上下文，它规定了内部的块级元素的布局方式，默认情况下只用根元素(body)一个块级上下文

### BFC的布局规则
1.  内部的块级元素会在垂直方向，一个接一个地放置
2.  块级元素垂直方向的距离由margin决定。属于同一个BFC的两个相邻的块级元素会发生margin合并，不属于同一个BFC的两个相邻的块级元素不会发生margin合并
3.  每个元素的margin box的左边，与包含border box的左边相接触(对于从左往右的格式化，否则相反) 即使存在浮动也是如此
4.  BFC的区域不会与float box 重叠
5.  BFC就是页面上一个隔离的独立容器，容器里面的子元素不会影响到外面的元素；外面的元素也不会影响到容器里面的子元素
6.  计算BFC的高度时，浮动元素也参与计算

### 创建一个BFC
一个BFC可以被显示触发，只需满足以下条件 之一 ：
1.  float的值不为none
2.  overflow的值部位visible
3.  position的值为 fixed / absolute
4.  display的值为 table-cell / table-caption / inline-block / flex / inline-flex

### BFC的应用
##### 1.  消除margin合并
  在同一个BFC中，margin会合并，那么我们只需要让需要消除margin合并的两个元素 处于不同的BFC即可。

##### 2.  包含浮动子元素
  因为BFC 在计算高度的时候，浮动元素也参加计算
  

