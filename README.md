# Pseudo-classes-Pseudo-element
<h1>css伪类和伪元素详解</h1>
<h2>伪类和伪元素的区分</h2>
<p>伪类和伪元素的根本区别在于：它们是否创造了新的元素(抽象)。从我们模仿其意义的角度来看，如果需要添加新元素加以标识的，就是伪元素，反之，如果只需要在既有元素上添加类别的，就是伪类。而这也是为什么，标准精确地使用 “create” 一词来解释伪元素，而使用 “classify” 一词来解释伪类的原因。一个描述的是新创建出来的“幽灵”元素，另一个则是描述已经存在的符合“幽灵”类别的元素。</p>
<p>前面一个冒号  :   的是伪类，两个冒号   ::    的是伪元素</p>
<h2>伪类</h2>
<h3>1.属性选择器</h3>
  以a为例，选择.main 下相关a元素
  
  
             //匹配属性值开头部分
             .main a[class^=column]{
                background:red;
                }
            //匹配属性值结尾
             .main a[href$=doc]{
                background:green;
              }
            //匹配属性值任意位置
            .main a[title*=box]{
                background:blue;
            }
  

<h3>2.伪类选择器</h3>

:root根节点选择器

        :root {
          background:orange;
        }
        
:not非选择器

       //#main 下除了type="submit"外其他的input标签
       #main input:not([type="submit"]){
          border:1px solid red;
        }

:empty空元素选择器

        //选出内容为空的p标签
        p:empty {
          display: none;
        }

:target 目标选择器
     
           //点击链接#change背景变为红色
          //html
          <a href="#change">点击改变target</a>
          <div id="change">我会变</div>
          //css
          #change:target{
            background:red;
          }
    
:first-child 第一个子代选择器

        //ol第一个子代li的颜色为红色
        ol>li:first-child{
            color:red;
        }
        
    :last-child 最后一个子元素
    
        ol>li:last-child{
           color:red;
        }

子元素选择器

        ol>li:nth-child(2n){
            background:orange;
        }
        .main>p:nth-child(3){
          background: green;
        }
        //选中前5个子元素
         .main>p:nth-child(-n+5){
          background: green;
        }
        //选中后5个子元素
        ol>li:nth-last-child(-n+5){
          background:green
        }
    
:first-of-type  子代特定标签名

      //.wrapper下第一个p标签
      .wrapper > p:first-of-type {
          background: orange;
      }
      // 
      .wrapper > p:nth-of-type(2n){
           background: orange;
       }   
       //倒数第一个某标签
        .wrapper > p:last-of-type{
          background: orange;
        }
        //倒数n个某标签元素
        .wrapper > p:nth-last-of-type(3){
          background: orange;
        }
        :only-child  独生子选择器
        http://www.imooc.com/code/813

:enabled  可用与不可用状态选择器

        input[type="text"]:enabled {
          background: #ccc;
          border: 2px solid red;
        }    
        input[type="text"]:disenabled {
          background: #fff;
          border: 2px solid blue;
        }        
        
:checked状态选择器

        //状态为checked的元素的下一个兄弟节点透明度为1
        input[type="checkbox"]:checked + span {
          opacity: 1;
        } 

:read-only 指定处于只读状态的元素

        input[type="text"]:-moz-read-only{
          border-color: #ccc;
        }
        input[type="text"]:read-only{
          border-color: #ccc;
        }
        //指定非只读状态
        input[type="text"]:-moz-read-write{
          border:2px solid red;
        }
        input[type="text"]:read-write{
          border:2px solid red;
        }
        
 :before（:after同理）
 ```html
 <!DOCTYPE html>
<html>
<head>
<style>
p:before
{
content:"台词：";
}
</style>
</head>

<body>

<p>我是唐老鸭。</p>
<p>我住在 Duckburg。</p>
<p><b>注释：</b>对于在 IE8 中工作的 :before，必须声明 DOCTYPE。</p>

</body>
</html>
 ```
 result
 ```
台词：我是唐老鸭。

台词：我住在 Duckburg。

台词：注释：对于在 IE8 中工作的 :before，必须声明 DOCTYPE。
 ```
<h2>伪元素</h2>
::selection  设置选中状态文字的颜色和背景颜色

        ::-moz-selection {
          background: red;
          color: green;
        }
        ::selection {
          background: red;
          color: green;
        }

::before和::after 给元素的前面或后面（z轴方向）插入内容

         //清除浮动
        .clearfix::before,
        .clearfix::after {
            //content 属性与 :before 及 :after 伪元素配合使用，来插入生成内容
            content: "";
            display: block;
            height: 0;
            visibility: hidden;
        }
        .clearfix:after {clear: both;}
        .clearfix {zoom: 1;}
        
    
