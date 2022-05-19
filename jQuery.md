# jQuery--框架

### 一、什么是jQuery

#### 1. jQuery概述

##### 1-1、Javascript库：

- 即library，是一个封装好的特定的集合（方法和函数）。从封装一大推函数的角度理解库，就是在这个库中，封装了很多预先定义好的函数在里面，比如动画animate、hide、show等。

##### 1-2、jQuery概念：

- jQuery是一个快速、简介的JavaScript库，封装了JavaScript常用的功能代码，优化了DOM操作、事件处理、动画设计和Ajax交互
- Jquery本质：**就是学习调用这些函数（方法）**；

##### 1-3、Jquery的优点：

- 轻量级。核心文件比较小，不会影响页面的加载速度；
- 跨浏览器兼容，基本兼容了现在主流的浏览器；
- 链式编程、隐式迭代
- 对事件、样式、 动画支持，大大简化了DOM操作；
- 支持插件扩展开发。有着丰富的第三方的插件，如：树形菜单、日期控件、轮播图等
- 免费、开源

### 二、如何使用jQuery

#### 1.jQuery的入口函数

##### 1-1、入口函数的使用：

1. 原生

   ```javascript
   $(document),ready(function() {
       ...  // 此处是页面DOM加载完成的入口
   })
   ```

2. 简化

   ```javascript
   $(function() {
       ... // 此处是页面DOM加载完成的入口
   })
   ```

##### 1-2、jQuery使用注意事项：

- 等着DOM结构渲染完毕后执行内部代码，不用等到所有外部资源加载完成，jQuery帮我们完成了封装。
- 相当于原生js的DOMContentLoaded；
- 不同于原生js中的load事件是等页面文档、外部的js文件、css文件、图片加载完毕才执行内部代码；
- 推荐使用简化版的入口函数。

#### 2.jQuery顶级对象$

- 在编写Jquery代码时，可以用$符号代替jQuery；

  ```javascript
  // 1.$  ---- 推荐使用，简洁方便
  	$(function() {
          // 代码块
      })
  // 2.jQuery
  	jQuery(function() {
          // 代码块
      })
  ```

#### 3.DOM对象和jQuery对象

##### 3-1、使用：

1. 用原生JS获取来的对象就是DOM对象

   ```javascript
   var div = document.querySelector('div');
   console.log('原生JS输出')；
   ```

2. jQuery方法获取的元素就是Jquery对象

   ```javascript
   $('div');
   console.log('jQuery对象输出')；
   ```

3. JQuery对象本质是： **利用$对DOM对象包装后产生的对象（伪数组形式存储）**；

##### 3-2、DOM和Jquery相互转化：

1. DOM对象和Jquery对象之间是可以相互转换的；

2. 因为原生JS比jQuery更大，原生的一些属性和方法jQuery没有给我们封装，需要进行转换使用；

3. DOM对象转换成Jquery对象： **$(DOM对象)**

   ```javascript
   $(div)  // 不需要加引号
   ```

4. JQuery对象转换为DOM对象

   ```javascript
   // 1.$(div)[index]  index是索引号
   	$(div)[index]；
   // 2.$(div).get(index)  index是索引号
       $(div).get(index)
   ```

### 三、jQuery常用API

#### 1.常用Jquery选择器

##### 1-1、jQuery基础选择器

- 原生JS获取元素方法很多，很杂，而且兼容性情况不一致，因此jQuery给我们做了封装，使获取元素统一标准；

  ```JavaScript
  $("选择器")   // 里面选择器直接写css选择器即可，但要加上引号
  ```

  | 名称       | 用法            | 描述                     |
  | ---------- | --------------- | ------------------------ |
  | ID选择器   | $("#id")        | 获取指定的ID元素         |
  | 全选选择器 | $("*")          | 匹配所有元素             |
  | 类选择器   | $(".class")     | 获取同一类class的元素    |
  | 标签选择器 | $("div")        | 获取同一类标签的所有元素 |
  | 并集选择器 | $("div,p,li")   | 选择多个元素             |
  | 交集选择器 | $("li.current") | 交集元素                 |

##### 1-2、jQuery层级选择器

| 名称       | 用法         | 描述                                       |
| ---------- | ------------ | ------------------------------------------ |
| 子代选择器 | $("ul > li") | 使用>号，获取亲儿子层级的元素；            |
| 后代选择器 | $("ul li")   | 使用空格，代表后代选择器，获取所有的li元素 |

##### 1-3、jQuery隐式迭代

1. 遍历内部DOM元素(伪数组形式存储)的过程就是**隐式迭代**；
2. 隐式迭代就是给匹配的所有元素进行循环遍历，都执行相应的方法；

##### 1-4、jQuery筛选选择器

| 语法       | 用法              | 描述                                    |
| ---------- | ----------------- | --------------------------------------- |
| :first     | $("li:first")     | 获取第一个li元素                        |
| :last      | $("li:last")      | 获取最后一个li元素                      |
| :eq(index) | $("li:eq(index)") | 获取到li元素中的其中一个，索引号从0开始 |
| :odd       | $("li:odd")       | 获取li元素中，索引为级数的元素          |
| :even      | $("li:even")      | 获取li元素中，索引为偶数的元素          |

##### 1-5、jQuery筛选方法

| 语法               | 用法                           | 说明                                                 |
| ------------------ | ------------------------------ | ---------------------------------------------------- |
| parent()           | $("li").parent()               | 查找父级                                             |
| children(selector) | $("ul").children('li')         | 相当于$("ul>li"),最近一级                            |
| find(selector)     | $('ul').find('li')             | 相当于$("ul li")，后代选择器                         |
| siblings(selector) | $('ul').siblings('li')         | 查找兄弟节点，不包括自己本身                         |
| nextAll([expr])    | $("ul").nextAll()              | 查找当前元素之后所有的同辈元素                       |
| prevAll([expr])    | $('ul').prevAll()              | 查找当前元素之前所有的同辈元素                       |
| hasClass(class)    | $('div').hasClass('protected') | 检查当前元素是否含有某个特定的类，如果有，则返回true |
| eq(index)          | $('li').eq(index)              | 相当于$("li:eq(index)")，索引从0开始                 |

##### 1-6、jQuery排他思想

- 排除其他，留下自己

  ```js
   $(function() {
          // 因为jQuery自带隐式迭代，所以不需要循环遍历
          $('button').click(function() {
              // 为当前元素加上背景色
              $(this).css('background','red');
              // 排除当前元素的兄弟元素
              $(this).siblings('button').css('background','');
          })
      })
  ```

  ‘

##### 1-7、链式编程

```js
// 给当前元素的背景色改为红色，同时清除当前元素兄弟背景色为空
$(this).css("background","red").siblings().css("background",'');
```

#### 2.如何操作jQuery样式

##### 2-1、操作css方法

- jQuery可以使用css方法来修改简单元素样式；也可以操作类，修改多个样式

1. 参数只写属性名，则是返回属性值

   ```js
   $(this).css("color");
   ```

2. 参数是属性名，属性值，**用逗号分割，同样属性名必须加引号**

   ```js
   $(this).css('color','red')
   ```

3. 参数可以是对象形式，方便设置多组样式。属性名和属性值用冒号分割，属性可以不用加引号

   ```js
   $(this).css( {
       width:300,
       height:300,
       backgroundColor:'red'
   })
   ```

##### 2-2、设置类样式方法

- 作用等同于以前的classList，可以操作类样式，注意操作类里面的参数不要加点。

1. 添加类，不影响其他的类名(原生js会覆盖)

   ```js
   $('div').addClass('current');
   ```

2. 删除类，不影响其他的类名(原生js会覆盖)

   ```js
   $('div').removeClass('current');
   ```

3. 切换类

   ```js
   $('div').toggleClass('current');
   ```

#### 3.常用jQuery动画效果

##### 3-1、显示隐藏与切换效果

###### 3-1-1、show()显示效果

1. **show([][][speed]、[easing]、[fn])**
2. **参数**：
   1. speed：预设速度的字符串（’slow‘-'normal'-'or'-'fast')或者表示动画时长的毫秒数值(如：1000)
   2. easing：用来指定切换效果，默认是"swing"，可用“linear”；
   3. fn：回调函数，在动画完成时执行函数，每个元素执行一次；

###### 3-1-2、hide()隐藏效果

1. **hide([speed]、[easing]、[fn])**
2. **参数：**
   1. speed：预设速度的字符串（’slow‘-'normal'-'or'-'fast')或者表示动画时长的毫秒数值(如：1000)
   2. easing：用来指定切换效果，默认是"swing"，可用“linear”；
   3. fn：回调函数，在动画完成时执行函数，每个元素执行一次；4.操作jQuery属性

###### 3-1-3、toggle()切换效果

1. **toggle([speed]、[easing]、[fn])**
2. 参数
   1. speed：预设速度的字符串（’slow‘-'normal'-'or'-'fast')或者表示动画时长的毫秒数值(如：1000)
   2. easing：用来指定切换效果，默认是"swing"，可用“linear”；
   3. fn：回调函数，在动画完成时执行函数，每个元素执行一次；4.操作jQuery属性

##### 3-2、滑动效果

###### 3-2-1、slideDown()下滑效果

1. **slideDown([speed]、[easing]、[fn])**
2. 参数
   1. speed：预设速度的字符串（’slow‘-'normal'-'or'-'fast')或者表示动画时长的毫秒数值(如：1000)
   2. easing：用来指定切换效果，默认是"swing"，可用“linear”；
   3. fn：回调函数，在动画完成时执行函数，每个元素执行一次；4.操作jQuery属性

###### 3-2-2、sildeUp()上滑效果

1. **slideUp([speed]、[easing]、[fn])**
2. 参数
   1. speed：预设速度的字符串（’slow‘-'normal'-'or'-'fast')或者表示动画时长的毫秒数值(如：1000)
   2. easing：用来指定切换效果，默认是"swing"，可用“linear”；
   3. fn：回调函数，在动画完成时执行函数，每个元素执行一次；4.操作jQuery属性

###### 3-2-3、slideToggle()切换滑动

1. **slideToggle([speed]、[easing]、[fn])**

2. 参数
   1. speed：预设速度的字符串（’slow‘-'normal'-'or'-'fast')或者表示动画时长的毫秒数值(如：1000)
   2. easing：用来指定切换效果，默认是"swing"，可用“linear”；
   3. fn：回调函数，在动画完成时执行函数，每个元素执行一次；4.操作jQuery属性
   
3. ```js
   <script>
       $(function() {
           $('button').eq(0).click(function() {
               // 下滑效果
               $('div').slideDown(1000)
           })
           $('button').eq(1).click(function() {
               // 上滑效果
               $('div').slideUp(2000)
           })
           $('button').eq(2).click(function() {
               // 滑动切换
               $('div').slideToggle(1000)
           })
       })
   </script>
   ```

   

##### 3-3、事件切换

- **hover([over],out)**: 事件切换。就是鼠标经过和离开的复合写法

  ```js
   // $('.box>li').hover(function() {
              //     // 下滑
              //     $(this).children('ul').slideDown(500);
              // },function() {
              //     // 上滑
              //     $(this).children('ul').slideUp(400);
              // })
              	// 滑动切换
              $('.box>li').hover(function() {
                  $(this).children('ul').slideToggle();
              })
  ```

##### 3-4、停止队列(排队)

- **stop()**
  1. stop()方法用于停止动画或效果
  2. stop()要写**到动画或者效果的前面，相当于停止结束上一次动画**

##### 3-5、淡入淡出效果

###### 3-5-1、淡入效果

1. **fadeIn([speed]、[easing]、[fn])**
2. 参数
   1. speed：预设速度的字符串（’slow‘-'normal'-'or'-'fast')或者表示动画时长的毫秒数值(如：1000)
   2. easing：用来指定切换效果，默认是"swing"，可用“linear”；
   3. fn：回调函数，在动画完成时执行函数，每个元素执行一次；4.操作jQuery属性

###### 3-5-2、淡出效果

1. **fadeOut([speed]、[easing]、[fn])**
2. 参数
   1. speed：预设速度的字符串（’slow‘-'normal'-'or'-'fast')或者表示动画时长的毫秒数值(如：1000)
   2. easing：用来指定切换效果，默认是"swing"，可用“linear”；
   3. fn：回调函数，在动画完成时执行函数，每个元素执行一次；4.操作jQuery属性

###### 3-5-3、淡入淡出切换

1. **fadeToggle([speed]、[easing]、[fn])**
2. 参数
   1. speed：预设速度的字符串（’slow‘-'normal'-'or'-'fast')或者表示动画时长的毫秒数值(如：1000)
   2. easing：用来指定切换效果，默认是"swing"，可用“linear”；
   3. fn：回调函数，在动画完成时执行函数，每个元素执行一次；4.操作jQuery属性

###### 3-5-4、修改透明度

1. **fadeTo([speed]、opacity，[easing]、[fn])**
2. 参数
   1. speed：预设速度的字符串（’slow‘-'normal'-'or'-'fast')或者表示动画时长的毫秒数值(如：1000)
   2. opacity透明度，取值0~1之间；必须写；
   3. easing：用来指定切换效果，默认是"swing"，可用“linear”；
   4. fn：回调函数，在动画完成时执行函数，每个元素执行一次；4.操作jQuery属性

<script>
        $(function() {
            // 淡入效果
            $('button').eq(0).click(function() {
                $('div').fadeIn(1000);
            })
            //淡出效果
            $('button').eq(1).click(function() {
                $('div').fadeOut(1000);
            })
            // 淡入淡出切换
            $('button').eq(2).click(function() {
                $('div').fadeToggle(1000);
            })
            // 修改透明度
            $('button').eq(3).click(function() {
                $('div').fadeTo(1000,.4);
            })
        })
    </script>

##### 3-6、自定义动画animate

1. **animate(params，[speed]、[easing]、[fn])**

2. 参数

   1. speed：预设速度的字符串（’slow‘-'normal'-'or'-'fast')或者表示动画时长的毫秒数值(如：1000)
   2. params：想要改变的样式属性，以对象形式传递，必须写。属性名可以不用带引号，如果是复合属性则需要采取驼峰命名法；
   3. easing：用来指定切换效果，默认是"swing"，可用“linear”；
   4. fn：回调函数，在动画完成时执行函数，每个元素执行一次；4.操作jQuery属性

3. 注意： **需要给要加动画的元素加上定位**

4. ```js
   <script>
           $(function() {
               $('button').click(function() {
                   $('div').animate({
                       left:500,
                   },500);
               });
           })
       </script>
   ```

#### 4.jQuery属性操作

##### 4-1、设置或获取元素固有属性值prop()

###### 4-1-1、获取元素属性

- **prop(“属性”)**

  ```js
  console.log($('a').prop('href'));
  ```

###### 4-1-2、设置元素属性

- **prop("属性"，“属性值”)**

  ```js
  $('a').prop('title','百度网');
  ```

##### 4-2、设置或获取元素自定义属性值attr()

- 用户自己给元素添加的属性，我们就称为自定义属性

###### 4-2-1、获取自定义属性

- **attr("属性")**

  ```js
  console.log($('div').attr('index')); // 类似于原生js的  getAttribute
  ```

###### 4-2-2、设置自定义属性

- **attr(“属性”，“属性值”)**

  ```js
  $('div').attr('index',4)； // 类似于原生js的 setAttribute
  ```

##### 4-3、数据缓存data()

- 在指定的元素上存取数据，并不会修改DOM元素结构，一旦页面刷新，之前存放的数据都将被移除

###### 4-3-1、附加数据

- **data("name","value")**  // 向被选元素附加数据

###### 4-3-2、获取数据

- **data("name")** //向被选元素获取数据

#### 5.jQuery内容文本值

- 针对元素的内容还有表单的值操作

##### 5-1、普通元素内容html()

- 相当于原生js中的innerHTMl

1. 获取元素的内容：**html()**
2. 设置元素的内容：**html(”内容“)**

##### 5-2、普通元素文本内容text()

- 相当于原生js中的innerText

1. 获取元素文本的内容：**text()**
2. 设置元素文本的内容：**text(”内容“)**

##### 5-3、表单的值val()

- 相当于原生value

1. 获取表单的内容：**val()**
2. 设置表单的内容：**val(”内容“)**

#### 6.jQuery元素操作

- 主要进行遍历、创建、添加、删除元素的操作

##### 6-1、遍历元素

- jQuery隐式迭代是对同一类元素做了同样的操作，如果想要给同一类元素做不同操作，就需要用到遍历

###### 6-1-1、语法一：

​	**$('元素').each( function(index,domEle) ){ })** 

```js
   $(function() {
        var arr = ['red','block','pink','blue']
        $('div').each(function(i,domEle) {
            $(domEle).css("color",arr[i])
        })
    })
```

###### 6-1-2、语法二:

​	**$.each(object,function(index,element) ){ } )**

1. $.each()方法可用于遍历任何对象，主要用于数据处理，比如：数组、对象

2. 里面的两个参数：index是每个元素的索引号；element遍历的内容

   ```js
    $.each(arr,function(i,ele) {
               console.log(i);
               console.log(ele);
           })
       })
   ```

##### 6-2、创建元素

```js
$("<li>动态创建元素</li>")
```

##### 6-3、添加元素

1. 内部添加到目标元素后面

   ```js
   $('ul').append(li);
   ```

2. 内部添加到目标元素前面

   ```js
   $('ul').prepend(li);
   ```

3. 外部添加到目标元素后面

   ```js
   $('.current').after(div);
   ```

4. 外部添加到目标元素前面

   ```js
   $('.current').before(div);
   ```

- **内部添加元素属于父子关系；**
- **外部添加元素属于兄弟关系；**

##### 6-4、删除元素

1. 删除元素本身

   ```js
   $('ul').remove();
   ```

2. 删除元素里的子节点

   ```js
   $('ul').empty();
   $('ul').html('');
   ```

#### 7.操作jQuery元素尺寸、位置

##### 7-1、jquery元素尺寸

| 语法                                 | 用法                                                  |
| ------------------------------------ | ----------------------------------------------------- |
| width() / height()                   | 取得匹配元素宽度和高度值，只算宽度/高度               |
| innerWidth() / innerHeight()         | 取得匹配元素宽度和高度值，包含padding                 |
| outerWidth() / outerHeight()         | 取得匹配元素宽度和高度值，包含padding、border         |
| outerWidth(true) / outerHeight(true) | 取得匹配元素宽度和高度值，包含padding、border、margin |

- 以上参数为空，则是获取相应值，返回的是数字型
- 如果参数为数字。则是修改相应值
- 参数可以不必写单位

##### 7-2、jQuery元素位置

- 位置主要有：**offset()、position()、scrollTop()/scrollLeft()**

###### 7-2-1、offset()设置或获取元素偏移

1. offset()方法设置或返回被选元素相对于文档的偏移坐标，和父级没有关系
2. 该方法有2个属性left、top。 
   1. offset().left用于获取距离文档左侧的距离；
   2. offset().top用于获取距离文档顶部的距离；
3. 可以设置偏移量： 如：offset({ top:10, left:10 })

###### 7-2-2、position()获取元素偏移

- 获取距离带有定位父级位置（偏移）， 如果该元素没有带有定位的父级，则以文档为准
- 只能获取，不能进行设置；

###### 7-2-3、scrollTop()/scrollLeft()设置或获取元素被卷去的头部和左侧

### 四、jQuery事件

#### 1、jQuery事件注册

##### 1-1、事件处理on()绑定事件

- 方法在匹配元素上绑定一个或多个事件处理函数

```js
element.on(events,[selector],fn);

// 1.events 一个或多个用空格分隔的事件类型。如：‘click keydown’
// 2.selector 元素的子元素选择器
// 3.fn回调函数，即绑定在元素身上的侦听函数
```

```js
<script>
    $(function() {
        // 绑定多个事件on方法
        // 方法一：
        $('div').on({
            click:function() {
                $(this).css('background','yellow')
            },
            mouseover:function() {
                $(this).css('background','red')
            },
            mouseout:function() {
                $(this).css('background','pink')

            }
        })

        // 方式二“
        $('div').on('mouseover mouseout',function() {
            $(this).toggleClass('current')

        })
    })
</script>
```

#### 2、jQuery事件处理

##### 2-1、事件委派

```js
<script>
    $(function() {
        // 事件委派的语法
        $('ul').on('click','li',function() {
            console.log(11);
        })
    })
</script>
```

##### 2-2、事件解绑off()

```js
<script>
    $(function( ) {
        $('div').on('click',function() {
            alert(11);
        })
        // 事件解绑
        $('div').off();
    })
</script>
```

##### 2-3、事件单次绑定one()

```js
<script>
    $(function( ) {
       // 事件绑定，隐式迭代，多次触发
        // $('ul').on('click','li',function() {
        //     alert('true')
        // })
        // 事件只触发一次
        $('ul').one('click','li',function() {
            alert('true')
        })
    })
</script>
```

##### 2-4、自动触发事件

- **元素.事件（）**
- **元素.trigger('事件')**
- **元素.triggerHandler('事件')**， 不会触发事件的默认行为

```js
<script>
    $(function() {
        $('div').on('click',function() {
            alert('true');
        });
        // 自动触发
        // 1 元素.事件（）
        $('div').click();
        // 2 元素.trigger('事件')
        $('div').trigger('click');
        // 3 元素.triggerHandler('事件')  , 不会触发元素的默认行为，如表单光标
        $('div').triggerHandler('click');

        $('input').on('focus',function() {
            $(this).val('how are you');
        })
        $('input').trigger('focus');
    })
</script>
```

#### 3、jQuery事件对象

- 事件被触发，就会有事件对象的产生

  ```js
  element.on(events,function(event) {})
  ```

  - 阻止默认行为：event.preventDefault() 或 return false
  - 阻止冒泡：event.stopPropagation( )

### 五、jQuery其他方法

##### 1、jQuery拷贝对象

- 如果想要把某个对象拷贝给另外一个对象使用，此时可以使用**$.extend()**方法；

- ```js
  $.extend([deep],target,object1,...)
  ```

  - deep: 如果为true则为深拷贝，为false是浅拷贝，默认浅拷贝；
  - target： 要拷贝的目标对象
  - object1： 待拷贝的第一个对象的对象；
  - .... ： 待拷贝的所有对象的对象；

- 浅拷贝是把被拷贝的对象复杂数据类型中的地址拷贝给目标对象，修改目标对象会影响被拷贝对象；

- 深拷贝，属于完全克隆，拷贝的是对象，不是 地址。修改目标对象不会影响被拷贝对象；

##### 2、多库共存

- jQuery使用$作为标识符，随着jQuery的流行，其他js库也会用$作为标识符，这样会引起冲突；
- 解决：
  1. 把里面的$符号同一**修改为jQuery**，比如说jQuery(’div);
  2. jQuery变量规定新的名称**$.noConflict()**,  例：var xxx = $.noConflict();

##### 3、jQuery插件

1. 常用插件网站：
   - **http://www.jq22.com/**
   - **http://www.hymleaf.com/**
2. 图片懒加载
   - 在jQuery插件库中找插件，来使用；
3. 全屏滚动
   - **http://www.dowebok.com/demo/2014/77/**