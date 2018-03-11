# Flex布局[参考1](http://www.ruanyifeng.com/blog/2015/07/flex-grammar.html)[参考2](http://www.ruanyifeng.com/blog/2015/07/flex-examples.html)

## Flex布局是什么？
Flex是Flexible Box的缩写，意为“弹性布局”，用来为盒模型提供最大的灵活性。
任何一个容器都可以指定为Flex布局

Webkit内核的浏览器，必须加上`-webkit`前缀

***注***
设为Flex布局后，子元素的float,clear 和vertical-align属性将失效。

## 基本概念
采用 Flex 布局的元素，称为 Flex 容器（flex container），简称"容器"。
它的所有子元素自动成为容器成员，称为 Flex 项目（flex item），简称"项目"。

## 容器的属性
容器有6个属性：

(1) flex-direction : 决定主轴的方向(即项目的排列方向),可取值(row(默认值，水平方向)，row-reverse,
    column,column-reverse)

(2) flex-wrap : 决定是否换行，可取值(nowrap[默认值],wrap,wrap-reverse)

(3) flex-flow : 是flex-direction 和flex-wrap属性的简写形式

(4) justify-content : 项目在主轴方向上的对齐方式，可取值(flex-start[左对齐，默认],flex-end,center,
    space-between[两端对齐],space-around[每个项目两侧的间隔相等])

(5) align-items : 项目在交叉轴上的对齐方式，可取值(flex-start,flex-end,center,
    baseline[项目的第一行文字的基线对齐],stretch[若项目为设高度或设为auto,将占满整个容器的高度])

(6) align-content : 定义多根轴线的对齐方式。若项目只有一根轴线，该属性不起作用；可取值(flex-start,
    flex-end,center,space-between,space-around,stretch[默认值])
    
## 项目的属性
项目也有6个属性

(1) order :定义项目的排列顺序。数值越小，越靠前，默认为0.

(2) flex-grow :定义放大比例，默认为0，即若存在剩余空间，也不放大 

(3) flex-shrink ：定义项目缩小比例，默认为1，若空间不足，该项目将缩小。

(4) flex-basis ：定义在分配多余空间之前，项目占据的主轴空间，默认为auto,即项目本来大小

(5) flex ：是flex-grow,flex-shrink,flex-basis的简写，默认是 0 1 auto.后两个属性可选。

(6) align-self ：允许单个项目有与其他项目不一样的对齐方式，可覆盖align-items属性。默认值为auto.
    表示继承父元素的align-items。若没有父元素，则等同于stretch。可取值(auto,flex-start.flex-end,center,baseline,stretch);
    
