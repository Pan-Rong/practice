# NPM使用介绍(window 系统)[官网](https://www.npmjs.com/)

## NPM的使用场景

NPM随同Node JS一起安装的包管理工具，能解决Node JS代码部署上的很多问题，常见的应用场景：

(1) 允许用户从NPM服务器下载别人编写的第三方包到本地使用

(2) 允许用户从NPM服务器下载并安装别人编写的命令行程序到本地使用

(3)允许用户将自己编写的包或命令行程序上传到NPM服务器供别人使用

首先测试随Node JS一起安装的NPM版本，
```
  npm -v
```
升级该NPM版本的方法：
```
  npm i -g npm
```
其次，查看程序的默认配置，方便以后找文件：

npm config 的使用：
```
     npm config set <key> <value>
     npm config get [<key>]
     npm config delete <key>
     npm config list [--json]
     npm config edit
     npm set <key> <value>
     npm get [<key>]
```
使用以下命令可以看到常用的配置列表，如（默认文件存储位置和缓存位置，）
```
    npm config list
```
一般情况下，npm的默认文件位置和缓存位置都在C盘，可以修改，修改默认配置的方法(注意是双斜杠)：
```
    npm config set prefix "F:\\NPM\\prefix"
```
上述配置后，就将文件的存储位置改了，可以用以下代码验证，是否成功：
```
    npm config get prefix
```
然后就可以安装你想要的模块了(若不需要修改默认路径，则可以不用上述操作)    
 
在命令窗口，打开子文件夹的方法“cd 子文件夹”;

返回上层文件夹用“../”;  
