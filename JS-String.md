# JS String 字符串
## 基本字符串和字符串对象的区别
字符串字面量 (通过单引号或双引号定义) 和 直接调用 String 方法(没有通过 new 生成字符串对象实例)
的字符串都是基本字符串.JavaScript会自动将基本字符串转换为字符串对象，只有将基本字符串转化为字符
串对象之后才可以使用字符串对象的方法.

## 字符串对象的方法
(1) String.prototype.charAt() :返回特定位置的字符;
(2) String.prototype.charCodeAt() :返回表示给定索引的字符的Unicode的值;
(3) String.prototype.codePointAt() :返回使用UTF-16编码的给定位置的值的非负整数;
(4) String.prototype.concat() :连接两个字符串文本，并返回一个新的字符串;
(5) String.prototype.indexOf() :从字符串对象中返回首个被发现的给定值的索引值，如果没有找到则返回-1
(6) String.prototype.lastIndexOf() :从字符串对象中返回最后一个被发现的给定值的索引值，如果没有找到
    则返回-1
(7) String.prototype.match() : 使用正则表达式与字符串相比较。   
(8) String.prototype.repeat() :返回指定重复次数的由元素组成的字符串对象.
(9) String.prototype.replace() :被用来在正则表达式和字符串直接比较，然后用新的子串来替换被匹配的子串
(10) String.prototype.search() ：对正则表达式和指定字符串进行匹配搜索，返回第一个出现的匹配项的下标
(11) String.prototype.slice() :摘取一个字符串区域，返回一个新的字符串
(12) String.prototype.split() :通过分离字符串成字串，将字符串对象分割成字符串数组
(13) String.prototype.substring() :返回在字符串中指定两个下标之间的字符。
(14) String.prototype.toLowerCase():将字符串转换成小写并返回。
(15) String.prototype.toString():返回用字符串表示的特定对象
(16) String.prototype.toUpperCase():将字符串转换成大写并返回.
(17) String.prototype.trim():从字符串的开始和结尾去除空格
(18) String.prototype.valueOf():返回特定对象的原始值
