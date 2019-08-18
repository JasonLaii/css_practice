<!--
 * @Author: Jason
 * @Date: 2019-08-18 13:00:07
 * @Github: https://github.com/JasonLaii
 * @Description:
 * @LastEditTime: 2019-08-18 13:21:07
 -->

#### CSS3 为了区分伪类和伪元素，伪元素采用双冒号写法

-- 常见伪类 :hover :target :checked :link :focus

-- 常见伪元素 ::first-letter ::first-line ::before ::after ::selection

::before 和 ::after 下特有的 content,用于在 css 渲染中向元素逻辑上的头部或尾部添加内容，这些内容不会出现在 DOM 中，不会改变文档内容，不可复制，仅仅在 css 渲染层加入

::before 和 ::after 必须配合 content 属性使用，content 用来定义插入的内容，content 至少为空("")，默认情况下，伪类元素 display 为 inline，可以通过设置来改变 display
  
 属性 content 可以取以下值 
  1. string  
  2. attr()

      通过attr()调用当前元素的属性，比如将图片的alt或者链接的href显示出来
      
    a::after{
      content: "{" attr(href) "}"
    }

  3.  url()/uri()
    用于引用媒体文件

    a::before{
      content: url("https://www.baidu.com/img/abc.gif");
    }

  4.  counter()
    调用计数器，可以不适用列表元素实现序号功能
    配合counter-increment和counter-rest属性使用

    <style>
      body{
        counter-rest: section;
      }
      h1{
        counter-reset: subsection;
      }
      h1:before{
        counter-increment:section;
        content:counter(section) "."
      }
      h2:before{
        counter-increment:subsection;
        content: counter(section) "." counter(subsection) ".";
      }
      </style>
      -------------------------
      <body>
        <h1>HTML</h1>
        <h2>HTML tag practice</h2>
        <h1>JavaScript</h1>
        <h2>JavaScript grammar practice</h2>
      </body>
