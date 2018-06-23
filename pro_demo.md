# 实际项目的示例或方法

## 1、 计算`<textarea>`中的行数，每行需按回车键
```
<!DOCTYPE html>
<html>
<head>
  <title>Title</title>
  <script>
    window.onload = function () {
      function onGetLines() {
        var tmp = document.querySelector('#test').value;
        var lines = tmp.split(/\r*\n/);

        var linesCount = lines.length - (navigator.userAgent.indexOf('MSIE') !== -1);
        console.log('当前文本行数', linesCount);
      }

      document.querySelector('#getLines').addEventListener('click', onGetLines, false)
    }
  </script>
</head>
<body>
<textarea name="test" id="test" cols="10" rows="3"></textarea>
<button id="getLines">获取行数</button>
</body>
</html>
```
