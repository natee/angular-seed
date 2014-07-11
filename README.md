# AngularJS应用种子项目

这是一个典型的[AngularJS](http://angularjs.org/)应用程序框架。你可以用它快速地创建angular webapp项目和这些项目需要的开发环境。

这个种子包含了一个示例AngularJS应用程序，并且通过预配置来安装Angular框架和一堆开发测试工具来满足即时web开发。

这个种子项目仅仅展示了如何把两个controller和view连接起来。

## 起步

你可以从克隆angular-seed仓库并且安装一些依赖开始：

### 准备条件

你需要用git来克隆angular-seed仓库，你可以从[http://git-scm.com/](http://git-scm.com/)获取。

我们使用一系列的node.js工具来初始化和测试angular-seed，因此你必须安装node.js和node.js的包管理工具（npm）。你可以从[http://nodejs.org/](http://nodejs.org/)获取它们。

### 克隆angular-seed

用[git][git]克隆angular-seed仓库：

```
git clone https://github.com/angular/angular-seed.git
cd angular-seed
```

### 安装依赖

这个项目中有两类依赖：工具和angular框架代码。工具帮助我们管理和测试应用程序。

* 我们通过[node包管理器][npm] `npm` 获取工具。
* 我们通过[客户端代码包管理器][bower] `bower` 获取angular代码。

我们已经提前配置了 `npm` 来自动运行 `bower` ，因此我们可以仅仅通过执行：

```
npm install
```

在这个命令的背后会执行 `bower install` ，因此你的项目中应该能看见两个新的文件夹。

* `node_modules` - 包含我们所需要用到的npm工具包
* `app/bower_components` - 包含angular框架文件

*注意到 `bower_components` 文件夹会被安装到根目录，但是angular-seed通过 `.bowerrc` 文件改变了它的位置，把它放到了app文件夹中，因此它能够更容易通过一个Web服务器提供文件服务。*

### 运行应用程序

我们用一个简单的开发环境web server预配置了这个项目，启动服务器最简单的方法就是：

```
npm start
```

现在通过访问 `http://localhost:8000/app/index.html` 来浏览这个app。



## 目录结构

    app/                --> all of the files to be used in production
      css/              --> css files
        app.css         --> default stylesheet
        pure.css        --> pure.css framework
      img/              --> image files
      index.html        --> app layout file (the main html template file of the app)
      index-async.html  --> just like index.html, but loads js files asynchronously
      js/               --> javascript files
        app.js          --> application
        controllers.js  --> application controllers
        directives.js   --> application directives
        filters.js      --> custom angular filters
        services.js     --> custom angular services
      partials/             --> angular view partials (partial html templates)
        partial1.html
        partial2.html

    test/               --> test config and source files
      protractor-conf.js    --> config file for running e2e tests with Protractor
      e2e/                  --> end-to-end specs
        scenarios.js
      karma.conf.js         --> config file for running unit tests with Karma
      unit/                 --> unit level specs/tests
        controllersSpec.js      --> specs for controllers
        directivessSpec.js      --> specs for directives
        filtersSpec.js          --> specs for filters
        servicesSpec.js         --> specs for services


## 测试

angular-seed应用程序中有两类测试：单元测试和端对端测试。

### 运行单元测试

angular-seed自带了单元测试，这是用[Jasmine][jasmine]写的，需要用[Karma测试运行器][karma]来运行。我门提供了一个Karma配置文件来运行它们。

* 配置文件在 `test/karma.conf.js` 目录下。
* 单元测试在 `test/unit/` 目录下。

运行单元测试最简单的方法就是使用附带的npm script:

```
npm test
```

这一段脚本会启动Karma运行器来执行单元测试，Karma会监视源文件和测试文件，一旦有任何变动，Karma就会重新运行测试代码。这是一个推荐的做法，当你每次保存一个文件时，如果你的单元测试正在运行，不论任何修改而打破了预期代码的功能，你都可以收到一个及时反馈。

你也可以让Karma做一个单一测试，然后退出，这个在你想检测特定版本代码是否按照预期运行时是非常有用的。这个项目包含一个预定义的脚本来做到这一点：  

```
npm run test-single-run
```


### 端对端测试

angular-seed自带的端对端测试也是用[Jasmine][jasmine]写的，这些测试通过端对端测试运行器[Protractor][protractor]运行的，它使用原生事件并且对Angular应用有着特殊的功能。

* 配置文件在 `test/protractor-conf.js` 目录下。
* 端对端测试代码在 `test/e2e/` 目录下。

Protractor可以模拟我们web应用的交互并且验证应用是否正确响应，因此，我们的web服务器需要为应用程序提供服务从而让Protractor可以和它进行交互。

```
npm start
```

除此之外，由于Protractor是基于WebDriver创建的，所以我们还需要安装webdriver。angular-seed包含了一个预定义的脚本来做这个工作：

```
npm run update-webdriver
```

这个命令会下载并安装最新版本的独立的WebDriver工具。

一旦你确保了托管我们应用程序的开发web服务器启动了并且在运行，而且WebDriver也是最新版本的，你就可以使用附带的npm脚本来运行端对端测试。

```
npm run protractor
```

当应用程序被托管在开发服务器上时，这个脚本就会执行端对端测试。

## 更新Angular

以前我们推荐你把对angular-seed所做的修改合并到你自己的分支项目中。
现在angular框架的库代码和和工具都是通过包管理工具（npm和bower）来获取，你可以用这个工具来代替更新这些依赖。

你可以通过运行下面的命令来更新工具依赖：

```
npm update
```

这个命令将会在 `package.json` 文件中找到匹配指定版本号范围内的最新版本进行更新。  

你可以通过运行下面的命令来更新Angular的依赖：

```
bower update
```

这个命令将会在 `bower.json` 文件中找到匹配指定版本号范围内的最新版本进行更新。

## 异步加载Angular

angular-seed项目支持异步加载Angular框架和应用程序脚本， `index-async.html` 就是用来支持这种加载方式而写的。为了让它能够正常跑起来，你必须注入一系列的Angular JavaScript到HTML页面中。这个项目有一段预定义的脚本来做这个事情：

```
npm run update-index-async
```

这个命令会复制 `angular-loader.js` 库文件的内容到 `index-async.html` 页面中。   
每次你要更新你正在使用的Angular版本时你就可以用这个命令了。

## 服务于应用程序文件

Angular是一种客户端技术，这可以创建一个不需要后端服务器的Angular webapp。我们建议用一个本地的web服务器来服务于这个项目的文件以避免浏览器的安全限制（sandbox）问题，sandbox在不同浏览器表现出来是各异的，但是当一个页面通过 `file://` 模式代替 `http://` 打开时，它经常会阻止类似cookies、xhr等事情的正常工作。

### 运行开发过程中的App

angular-seed自带了一个本地开发服务器，它是node.js的一个工具，叫做[http-server][http-server]。你可以用 `npm start` 命令来启动这个web服务器，但是你应该把这个工具安装在全局中：

```
sudo npm install -g http-server
```

这时你就可以启动你自己的开发web服务器，你可以用它来从一个文件夹中提供一些静态文件，通过下面的命令来运行：

```
http-server
```

另外，你也可以选择配置你自己的web服务器，比如apache，或者nginx。只需要把服务于你的项目文件的服务器配置到 `app/` 目录下。

### 运行产出过程的App

这取决于你的应用有多复杂和你系统的整体架构，但是最基本的一点就是你必须把产出的应用所用到的所有文件都放到 `app/` 目录下。   
其它的都可以不管。

Angular应用仅仅是需要一堆静态的html、css和js文件放在一个浏览器可以访问的地方。   

如果你的Angular应用需要通过xhr或是其它方式与后端打交道，你必须搞清楚什么是符合同源策略的承载静态文件的最佳方法，以及是否适用。通常这是由后端服务器或是通过反向代理中的后端服务器或是web服务器托管文件来完成。

## 持续集成

### Travis CI

[Travis CI][travis]是一个可以让你持续集成服务， 它可以监视GitHub上你的仓库发生的代码提交，并且执行一些诸如创建应用程序或者运行测试的脚本。ngular-seed项目包含一个Travis配置文件 `.travis.yml` ，当你提交代码到GitHub上时它就会让Travis来运行测试。   

你需要启用Travis和GitHub之间的集成，你可以到Travis官网上获取如何使用Travis的教程。

### CloudBees

CloudBees已经提供了一个CI/deployment设置:

<a href="https://grandcentral.cloudbees.com/?CB_clickstart=https://raw.github.com/CloudBees-community/angular-js-clickstart/master/clickstart.json">
<img src="https://d3ko533tu1ozfq.cloudfront.net/clickstart/deployInstantly.png"/></a>

一旦你运行这段代码，你就会获取这个仓库的克隆版本来作为你私人的git仓库进行开发工作，同时你也会获取一个可以在Firfox和Chrome中运行单元测试和端对端测试的CI服务。


## 联系方式

获取更多关于AngularJS的信息请访问[http://angularjs.org/](http://angularjs.org/)

[git]: http://git-scm.com/
[bower]: http://bower.io
[npm]: https://www.npmjs.org/
[node]: http://nodejs.org
[protractor]: https://github.com/angular/protractor
[jasmine]: http://pivotal.github.com/jasmine/
[karma]: http://karma-runner.github.io
[travis]: https://travis-ci.org/
[http-server]: https://github.com/nodeapps/http-server