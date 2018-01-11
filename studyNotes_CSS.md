# css简介

**1、CSS选择器**

    CSS选择器即通过某种规则来匹配相应的标签，并为其设置CSS样式，常用的有类选择器、标签选择器、ID选择器、后代选择器、群组选择器
    伪类选择器(before/after)、兄弟选择器(+~)、属性选择器等等。
    
**2、CSS Reset**


    HTML在不设置任何样式的情况下，也会有一个默认的CSS样式，这是因为浏览器自带的。而不同的浏览器对于这个默认样式的CSS设置也不同，
    这就会导致代码兼容的问题。为了保证代码的兼容性，通常需要在初始化时，将其统一；
    用通标符(*)可以实现,这就是CSS样式的Reset。例：*{margin:0;padding:0}

**3、盒子布局**

    盒子模型是CSS布局的基石。常见的盒子模型有块级盒子(block)和行内盒子(inline-block),与盒子相关的几个属性：
    margin、border、padding和content等，这些属性的作用是设置盒子与盒子之间的关系以及盒子与内容之间的关系。其中，只有普通文档流
    中块级盒子的垂直外边距才会发生合并，而行内盒子、浮动盒子或绝对定位之间的外边距不会合并。另外，box-sizing属性的设置会影响盒子
    的width和height的计算
    
**4、浮动布局**


    设置元素的float属性值为left或right，就能使该元素脱离普通文档流，向左或向右浮动。一般在宫格布局时会用到，如果子元素全部设置
    位浮动，则父元素是塌陷的，这时就需要清除浮动，清除浮动的方法也很多，常用的方法是在元素的末尾加空元素设置clear:both;
    更高级一点的就给父容器设置before/after来模拟一个空元素，还可以直接设置overflow属性为auto/hidden来清除浮动。初浮动可以实现
    宫格布局，行内盒子(inline-block)和table也可以实现同样的效果。
     
 **5、定位布局**    


    设置元素的position属性值为relative/absolute/fixed,就可以使该元素脱离文档流，并以某种参照坐标进行偏移。
    其中，
    relative是相对定位，它以自己原来的位置进行偏移，偏移后，原来的空间不会被其他元素占用；
    absolute是绝对定位，它以离自己最近的定位父容器作为参照进行偏移；为了对某个元素进行定位，常用的方式就是设置父容器的
    position:relative,因为相对定位元素在不设置top和left值时，不会对元素位置产生影响；
    fixed是固定定位，它则以浏览器窗口为参考物，PC网页底部悬停的banner一般都是可以通过fixed定位来实现，但fixed属性在移动端
    有兼容性问题，因此不推荐使用，可替代的方案是：绝对定位+内部滚动
      
 **6、弹性布局**     


    弹性布局即Flex布局，定义了flex容器一个可伸缩容器，首先容器本身会根据容器中的元素动态设置自身大小；然后当Flex容器被应用一
    个新尺寸时(width和height),将会自动调整容器中的元素适应新尺寸。Flex容器也可以设置伸缩比例和固定宽度，还可以设置容器中元素
    的排列方向(横向和纵向)和是否支持元素的自动换行。有了这个神器，做页面布局的可以方便很多。注：设为Flex布局后，子元素的float、
    clear和vertical-align属性将失效
      
 **7、CSS3动画**


    CSS3中规范引入了两种动画，分别是transition和animation,transition可以让元素的CSS属性值变化在一段时间内平滑的过度，形成
    动效果，为了使元素的变换更加丰富多彩，CSS3还引入了transfrom属性，它可以通过对元素进行平移(translate)、旋转(rotate)、放
    大缩小(scale)、倾斜(skew)等操作，来实现2D和3D变化效果。transition还有一个结束事件，transitionEnd,该事件是在CSS完成过渡
    后触发，如果过渡在完成之前被移除，则不会触发transitionEnd。
      
    animation需要设置一个@keyframes，来定义元素以哪种形式进行变换，然后再通过动画函数让这种变化平滑的进行，从而达动画效果，动画
    可以被设置成永久循环演示。设置animation-play-state:paused可以暂停动画，设置animation-fill-mode:forwards可以让动画完成后
    定格在最后一帧。另外，还可以通过JS监听animation的开始、结束和重复播放时的状态，分别对应三个事件，即animationStart、
    animationEnd、animationIteration.当播放次数设置为1时，不会触发animationIteration。
      
    和transition相比，animation设置动画效果更灵活更丰富，还有一个区别是：transition只能通过主动改元素的css值才能触发动画效果，
    而animation一旦被应用，就开始执行动画。另外，HTML5还新增了一个动画API，即requestAnimationFrame,它通过JS来调用并按照屏幕
    的绘制频率来改变元素的css属性，从而达到动画效果
      
 **BFC**(目前还没有遇到过，等到了再补充)
 
 
 **Sprite**
 
    对于大型站点，为了减少http请求次数，一般会将常用的小图标排到一个大图中，页面加载时，只需请求一次网络，然后在css中通过设置
    background-position来控制显示所有需要的小图标，这就是Sprite图
    
      
    
    
    
