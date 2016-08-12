# Pseudo-classes-Pseudo-element
<h1>css伪类和伪元素详解</h1>


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
        
