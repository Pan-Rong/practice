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
### 2、检查回文字符串
    如果给定字符串是回文，返回true;反子，返回false;若一个字符串忽略标点符号、大小写和空格，正着读和反着读一模一样，那么这个字符串就是回文(palindrome)
```
    function palindrome(str){
        var pstr=str.replace(/\W/g,"");//\W包含下划线，需单独列出
            pstr=pstr.replace("_","");
            pstr=pstr.toLowerCase();//全部转化成小写
            str=pstr.split("",pstr.length);
            str=str.reverse();
        var pstr1=str.join("");
        if(pstr==pstr1){
            return true;
        }else{
            return false;
        }
    }
    palindrome("0_0 (: /-\ :) 0-0");
```
    字符串中方法解释：
    （1）replace() 方法返回一个由替换值替换一些或所有匹配的模式后的新字符串。模式可以是一个字符串或者一个正则表达式, 替换值可以是一个字符串或者一个每次匹配都要调用的函数。不改变原字符串。

    (2)正则表达式
       RegExp 构造函数创建了一个正则表达式对象，用于将文本与一个模式匹配。    
       语法：/pattern/flags; new RegExp(pattern [, flags]); RegExp(pattern [, flags])
replace详细解释[点击连接](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/replace)
正则表达式详情[点击连接](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/RegExp)   
### 3、找出最长单词
    找出最长单词并返回该单词的长度
```
    function findLongestWord(str){
        var nary=str.split(" ");
        var lary=[];
            for(var i-0;i<nary.length;i++){
                lary[i]=nary[i].length;
            }
            lary=lary.sort(function(a,b){return b-a;})
            return lary[0];
    }
    findLongestWord("The quick brown fox jumped over the lazy dog");
```
    数组方法解释：
    （1）sort(compareFunction) 方法在适当的位置对数组的元素进行排序，并返回数组。参数可选，默认排序顺序是根据字符串Unicode码点.原数组已经被排序后的数组代替。
[详情](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/sort)
### 4、句中单词首字母大写
    字符串首字母大写，其余小写
```
    function titleCase(str){
        var nstr=str.split(" ");
            for(var i-0;i<nstr.length;i++){
                var nnstr=nstr[i].split("");
                nstr[i]=nnstr[0].toUpperCase()+nnstr.splice(1,nnstr.length-1).join("").toLowerCase();
            }
            return nstr.join(" ");
    }
    titleCase(I'm a little tea pot);
```
    数组中函数解释
    array.splice(start, deleteCount, item1, item2, ...)方法通过删除现有元素和/或添加新元素来更改一个数组的内容.
    start指定修改的开始位置（从0计数）。如果超出了数组的长度，则从数组末尾开始添加内容；如果是负值，则表示从数组末位开始的第几位（从1计数）；若只使用start参数,表示删除[start，end]的元素.
    deleteCount(可选)，整数，表示要移除的数组元素的个数。
    item1(可选)，要添加进数组的元素,从start 位置开始。
    返回值：由被删除的元素组成的一个数组。
### 5、找出多个数组中的最大数
    找出多个数组中的最大数，然后把他们串联起来，形成一个新数组
```
    function largest(arr){
        var newarry=[];
            for(var i=0;i<arr.length;i++){
                arr[i]=arr[i].sort(function(a,b){return b-a;});//实现从大大小排列
                newarry[i]=arr[i][0];
            }
            return newarry;
    }
    largest([[1,3,5,2],[22,43,13,87,90],[67,35,85,23]]);
```
### 6、检查字符串结尾
    判断一个字符串是否以指定的字符串(target)结尾，若是返回true，否则返回false.
```
    function confirmEnding(str,target){
        /*
            .substr方法，返回一个字符串从指定位置开始到指定字符数的字符；
            str.substr(start[,length])
            start开始提取字符的位置。若为负，则看作strlength-start；
            length（可选）
        */
        var nstr=str.substr(-(target.length));
            if(nstr===target){
                return true;
            }else{
                return false;
            }
    }
    confirmEnding("Bastian","n");
```
### 7、截断字符串
    若字符串的长度比指定的参数num长，则把多余的部分用...来表示。插入到字符串尾部的三个点也会计入字符串的长度
    若指定字符串的参数num小于或等于3，则添加的三个点不会计入字符串长度
```
    function truncate(str,num){
        var nstr="";
            if(str.length>num){
                if(num>3){
                    nstr=nstr.slice(0,num-3);
                }else{
                    nstr=str.slice(0.num);
                }
                str=nstr+"...";
            }
            return str;  
    }
```
    数组中方法
    slice(),提取一个字符串的一部分，并返回一个新的字符串
    slice(beginSlice[,endSlice])
    从该索引（以0为基数）处开始提取原字符串的字符
    若值为负，则看作sourceLength+beginSlice(此处的begin为负)
    end可选，若省略，一直提到末尾；若为负，同begin
