# graphviz

此repository保存了用graphviz画图的源文件。

## 下载graphviz

地址：http://graphviz.org/Download..php

目前最新版是2.38。

Windows中用的版本：http://graphviz.org/pub/graphviz/stable/windows/graphviz-2.38.msi

安装graphviz之后，将dot命令所在的路径添加到全局变量中。例如，在windows中，
dot.exe所在目录：`C:\Program Files (x86)\Graphviz2.38\bin`

检查一下dot是否可以使用，`-V`可以查看dot的版本，如果能看到版本信息，那么可以开始使用了。

```
$ dot -V
dot - graphviz version 2.38.0 (20140413.2041)
```

## 将.gv生成图片

使用参数`-T`指定输出格式，`-O`表示在原始的.gv文件名上加上`-T`指定的后缀。例如，
```language
dot -Tpng -O xxx.gv
```
生成名字为xxx.gv.png的图片。

例如：
```language
dot -Tpng -O bindService_onBind_process_already_exists.gv
```

如果生成的图片太大了，可以使用`-s`参数（scale）缩小图片：

```language
dot -Tpng -O -s90 bindService_onBind_create_process.gv
```
例如，未使用`-s`时，生成的图片`bindService_onBind_create_process.png`的像素是11864 x 6221，使用`-s90`之后，生成的图片`bindService_onBind_create_process_small.png`（我加了_small以示区分）的像素为7200 x 3776。

对于对图片大小有限制的网站来说，使用`-s`参数，就可以生成一张小点的图了。

## graphviz的一些语法知识

### `clusterrank=none`

`graph`属性中多了`clusterrank=none`，这样图中的所有节点的rank值是按照一条线下来的。具体看后面的例子和图片。

## `bindService_flow_create_process`目录

`bindService_onBind_create_process.gv`是bindService时，提供service的进程还没有创建时，代码的执行流程，即要先创建进程。

同目录中的图片是由.gv文件生成的图片。

## `bindService_flow_process_already_exists`目录

`bindService_onBind_process_already_exists.gv`是bindService时，提供service的进程已经存在了，这时的代码执行流程。

同目录中的图片是由.gv文件生成的图片。

`bindService_onBind_process_already_exists_flow.gv`与`bindService_onBind_process_already_exists.gv`的区别是，前者的`graph`属性中多了`clusterrank=none`。

