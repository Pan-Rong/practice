# 通过url的id传输数据的方法

传送页面代码：
```
url:'editorPage.html?id = "XXXX" & type="AAA"'
```

接受页面代码：

```
getUrlParam("type"); // 获得url中type对应的值
getUrlParam("id") ; //获得url中id对应的值

//跳转页面获取 id 或是 type等
function getUrlParam(label) {
  var reg = new RegExp('(^|&)' + label + '=([^&]*)(&|$)', 'i');  //构造一个含有目标参数的正则表达式对象
  var r = window.location.search.substr(1).match(reg); //匹配目标参数
  if (r != null) {
    return unescape(r[2]);
  }
  return null; //返回参数值
}

```
