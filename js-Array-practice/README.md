
## 数组练习
### 1、翻转字符串
    要求：先把字符串转化成数组，再借助数组的reverse方法翻转数组顺序，最后把数组转化成字符串，结果必须是一个字符串。
```
    function reverseString(str){
      var sary=str.split("",str.length);
          str=sary.reverse();
          str=str.join("");
          return str;
    }
    reverseString("hello");
```
    数组中方法解释：
    （1）String.split([separator[, limit]])
          split() 方法,使用指定的分隔符字符串将String分割成数组.如果为("")，则每个字符分割(如上例).当字符串为空，返回空字符数组;若字符串、字符都空，则返回空数组.
          separator：指定表示每个拆分应发生的点的字符串。separator 可以是一个字符串或正则表达式.
          limit:一个整数，限定返回的分割片段数量.若省略，则整个字符串都分割.
     （2）Array.reverse() 方法,将数组中元素的位置颠倒,第一个数组元素成为最后一个数组元素，最后一个数组元素成为第一个.无参数.
     （3）Array.join(separator)方法,将数组（或一个类数组对象）的所有元素连接到一个字符串中.如果 arr.length 为0，则返回空字符串.
          separator：指定一个字符串来分隔数组的每个元素.如果省略，默认为 ",";如果separator是空字符串("")，则所有元素之间都没有任何字符.

          
