# axios 跨域问题
[官方文档1](https://www.kancloud.cn/yunye/axios/234845)
[参考2](https://www.cnblogs.com/Upton/p/6180512.html)
安装
```
npm install axios
```
导入方式及示例
```
import axios from 'axios';

function Post(){
  return axios({
            method: 'post',
            url: url,
            data: data,
            headers: { 'WWW-Authenticate': 'text' },
        })
            .then(result => result.data)
            .catch(function (error) {
                console.log(error);
            });
}

function Get(){
  return axios.get(url)
            .then(result => result.data)
            .catch(function (error) {
                console.log(error);
            });
}

```

