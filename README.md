# sass-example-learn
sass样例学习

1. ./start/use variables
2. ./start/nested css rules
3. ./start/import css files
4. ./start/comments

**Sass**是基于**Ruby**语言开发而成的，因此安装Sass前需要Ruby环境。

安装成功后在`cmd`中输入下列命令行来测试Ruby是否安装成功。

```cmd
ruby -v
```

但是因为国内网络的问题导致`gem`源会间歇性中断。让我们的下载体验非常糟糕。
所以我们需要更换`gem`源。


```cmd
//1.删除原gem源
gem sources --remove https://rubygems.org/

//2.添加国内淘宝源
gem sources -a https://ruby.taobao.org/

//3.打印是否替换成功
gem sources -l

```

接下去用命令行安装Ruby并查看是否安装成功。

```cmd
//1.安装sass
gem install sass

//2.查看sass是否安装成功
sass -v
```

sass编译有很多种方式，如命令行编译模式、sublime插件`SASS-Build`、编译软件`koala`、前端自动化软件`codekit`、`Grunt`打造前端自动化工作流`grunt-sass`、`Gulp`打造前端自动化工作流`gulp-ruby-sass`等。


我的命令行编译

```cmd
// 监听单文件input.scss，导出output.css；编译排版类型compact；增加调试map；开启debug信息。
sass --watch  ../sass/input.scss:./output.css --style compact --sourcemap --debug-info
```