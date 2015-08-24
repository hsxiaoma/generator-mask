## generator-mask

<img src="https://gw.alicdn.com/tps/TB1K4zwJXXXXXXwaXXXXXXXXXXX-1178-454.png_600x600.jpg" width="400" />

by 拔赤 bachi@taobao.com

[![NPM version][npm-image]][npm-url]
[![build status][travis-image]][travis-url]
[![Coverage Status](https://coveralls.io/repos/jayli/generator-mask/badge.svg?branch=master&service=github)](https://coveralls.io/github/jayli/generator-mask?branch=master)
[![node version][node-image]][node-url]
[![npm download][npm-download]][download-url]

[![generator-mpi](https://nodei.co/npm/generator-mask.png)](https://npmjs.org/package/generator-mask)

[npm-image]: http://img.shields.io/npm/v/generator-mask.svg?style=flat-square
[npm-url]: http://npmjs.org/package/generator-mask
[bower-image]: http://img.shields.io/bower/v/generator-mask.svg?style=flat-square
[bower-url]: https://github.com/jayli/generator-mask
[travis-image]: https://img.shields.io/travis/jayli/generator-mask.svg?style=flat-square
[travis-url]: https://travis-ci.org/jayli/generator-mask
[node-image]: https://img.shields.io/badge/node.js-%3E=_0.12-green.svg?style=flat-square
[node-url]: http://nodejs.org/download/
[npm-download]: https://img.shields.io/npm/dm/generator-mask.svg?style=flat-square
[download-url]: https://npmjs.org/package/generator-mask


### Generator-Mask 工具简介

[KISSY MINI](http://m.kissyui.com) 是一款面向无线前端研发的 JavaScript 类库，[Generator-Mask](https://github.com/jayli/generator-mask) 是 KISSY MINI 项目脚手架工具，用来生成项目代码骨架，你可以方便的基于此结构来开发你的项目，并享用到 KISSY MINI 的诸多优秀特性。

Generator-Mask 是 Generator-clam 简化开源版本，设计原理完全一致，Clam 绑定了更多阿里内部私有容器技术规范，阿里内部（阿里旅行）的同学请异步[Generator-clam](http://web.npm.alibaba-inc.com/package/generator-clam)

> 注意：[Generator-Mask](https://github.com/jayli/generator-mask) 是项目生成工具，[Generator-Mpi](https://github.com/jayli/generator-mpi) 是 KISSY MINI 模块代码生成工具

### 工具安装

> 如果你在阿里内网，请将 NPM 源指向内网镜像 `sudo npm install -g tnpm --registry=http://registry.npm.alibaba-inc.com`，然后用`tnpm`（阿里内网 NPM）来安装

首先安装三件套：

	npm install -g yo grunt-cli bower

然后安装本地服务和脚手架

	npm install -g here-ssi generator-mask

完成。

### 工具使用

首先创建好一个存放项目的空目录，进入这个空目录，执行

	yo mask

然后根据提示完成项目初始化的工作即可。初始化完成后的目录结构为：

	./
	├── Gruntfile.js 			项目构建主任务
	├── package.json			项目配置文件
	├── README.md				项目自述文件
	├── build/					构建目录
	├── doc/					文档存放目录
	├── grunt/					各构建任务脚本
	│   ├── bower.json			各构建任务脚本安装配置
	│   ├── custom/*.js			自定义任务
	│   └── default/*.js		默认任务
	└── src/					源码目录
		├── config.js			项目config.js
		├── mods/				业务公用模块目录
		│   └── header.html		公用头
		├── widgets/ 			组件目录
		│   ├── bower.json		组件安装源配置(gitlab or github)
		│   ├── cssreset/		Cssrest 种子
		│   │   └── reset.css
		│   └── kissymini/		Kissymini 种子
		│       └── build/mini-min.js
		└── pages/				页面目录		 
			└── home/			Home 页面目录
				├── index.js	Home 下辖的js文件
				├── index.scss	Home 下辖的scss文件
				└── index.html	Home 下辖的html文件

我们始终将项目代码分割为三个部分：pages（页面）、mods（业务公用逻辑）、widgets（组件），其中 widgets 中推荐存放外部依赖的模块，通过 `bower install` 来安装，其中`src/widgets/bower.json`中带有组件安装源的配置，这个配置是通过`yo mask`初始化时输入的。

此外，若要获得可发布代码，则将`src/`目录中的源码构建到`build/`目录中，构建脚本参照项目根目录下的`Gruntfile.js`，其中构建任务配置详情均存放在grunt/default/`目录中。

### 运行 hello world

当初始化完成项目骨架后，要补全本地的node模块，在项目根目录下执行`npm install`

**开启本地Server**：在项目根目录执行

	here

这时直接打开浏览器访问到本地目录，选择`src/pages/home/index.html`，可以看到 “hello world”，项目运行成功。

### 项目构建

在根目录执行

	grunt

将会针对`src/`进行构建，构建完成后的目录结构和`src/`保持一样，是可发布的代码，包括 html 代码和 资源文件（css 和 js），执行`here`开启本地服务后，访问`build/pages/home/index.html`亦可以看到“hello world”。

### Mask 的使用习惯

Mask 生成的代码本质上是一套框架，每个目录具有自己的语义和规范，按照这个规范会写出非常出色的项目代码，在复杂的业务研发中，也能保持项目代码结构的整洁易读。即你要接手别的KISSY MINI 的项目，只需将代码clone到本地，然后进入项目目录执行`npm install`即可，直接就拥有了`here`预览源码和`grunt`构建脚本。

Mask 脚手架工具的边界同样清晰，这些内容不是 Mask 脚手架负责的

1. 代码的发布操作
1. 埋点和数据统计
1. 页面特殊标签的构建

当然如果你足够了解grunt构建工具，完全可以自己定制构建脚本，自行添加的构建参数配置可以放在`grunt/custom/`中。

因此，Mask 实际上仅对 KISSY MINI、Bower、Git、Grunt 有依赖，此外 Mask 还建议所有 css 源码编写使用 sass 或者 less。

### widgets 代码的生成和安装

KISSY MINI 有推荐的模块代码格式，使用[Generator-Mpi](https://github.com/jayli/generator-mpi)来生成，更多内容请参照 [Mpi 官网](https://github.com/jayli/generator-mpi)

<img src="http://gw.alicdn.com/tps/TB13sGbJXXXXXbaXVXXXXXXXXXX-360-196.png" width="200" />

