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

在这个命令的背后也会执行 `bower install` ，因此你的项目中应该能看见两个新的文件夹。

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

The angular-seed app comes preconfigured with unit tests. These are written in
[Jasmine][jasmine], which we run with the [Karma Test Runner][karma]. We provide a Karma
configuration file to run them.

* 配置文件在 `test/karma.conf.js`
* 单元测试在 `test/unit/`。

运行单元测试最简单的方法就是使用附带的npm script:

```
npm test
```

This script will start the Karma test runner to execute the unit tests. Moreover, Karma will sit and
watch the source and test files for changes and then re-run the tests whenever any of them change.
This is the recommended strategy; if your unit tests are being run every time you save a file then
you receive instant feedback on any changes that break the expected code functionality.

You can also ask Karma to do a single run of the tests and then exit.  This is useful if you want to
check that a particular version of the code is operating as expected.  The project contains a
predefined script to do this:

```
npm run test-single-run
```


### 端对端测试

The angular-seed app comes with end-to-end tests, again written in [Jasmine][jasmine]. These tests
are run with the [Protractor][protractor] End-to-End test runner.  It uses native events and has
special features for Angular applications.

* the configuration is found at `test/protractor-conf.js`
* the end-to-end tests are found in `test/e2e/`

Protractor simulates interaction with our web app and verifies that the application responds
correctly. Therefore, our web server needs to be serving up the application, so that Protractor
can interact with it.

```
npm start
```

In addition, since Protractor is built upon WebDriver we need to install this.  The angular-seed
project comes with a predefined script to do this:

```
npm run update-webdriver
```

This will download and install the latest version of the stand-alone WebDriver tool.

Once you have ensured that the development web server hosting our application is up and running
and WebDriver is updated, you can run the end-to-end tests using the supplied npm script:

```
npm run protractor
```

This script will execute the end-to-end tests against the application being hosted on the
development server.


## Updating Angular

Previously we recommended that you merge in changes to angular-seed into your own fork of the project.
Now that the angular framework library code and tools are acquired through package managers (npm and
bower) you can use these tools instead to update the dependencies.

You can update the tool dependencies by running:

```
npm update
```

This will find the latest versions that match the version ranges specified in the `package.json` file.

You can update the Angular dependencies by running:

```
bower update
```

This will find the latest versions that match the version ranges specified in the `bower.json` file.


## Loading Angular Asynchronously

The angular-seed project supports loading the framework and application scripts asynchronously.  The
special `index-async.html` is designed to support this style of loading.  For it to work you must
inject a piece of Angular JavaScript into the HTML page.  The project has a predefined script to help
do this.

```
npm run update-index-async
```

This will copy the contents of the `angular-loader.js` library file into the `index-async.html` page.
You can run this every time you update the version of Angular that you are using.


## Serving the Application Files

While angular is client-side-only technology and it's possible to create angular webapps that
don't require a backend server at all, we recommend serving the project files using a local
webserver during development to avoid issues with security restrictions (sandbox) in browsers. The
sandbox implementation varies between browsers, but quite often prevents things like cookies, xhr,
etc to function properly when an html page is opened via `file://` scheme instead of `http://`.


### Running the App during Development

The angular-seed project comes preconfigured with a local development webserver.  It is a node.js
tool called [http-server][http-server].  You can start this webserver with `npm start` but you may choose to
install the tool globally:

```
sudo npm install -g http-server
```

Then you can start your own development web server to serve static files from a folder by
running:

```
http-server
```

Alternatively, you can choose to configure your own webserver, such as apache or nginx. Just
configure your server to serve the files under the `app/` directory.


### Running the App in Production

This really depends on how complex is your app and the overall infrastructure of your system, but
the general rule is that all you need in production are all the files under the `app/` directory.
Everything else should be omitted.

Angular apps are really just a bunch of static html, css and js files that just need to be hosted
somewhere they can be accessed by browsers.

If your Angular app is talking to the backend server via xhr or other means, you need to figure
out what is the best way to host the static files to comply with the same origin policy if
applicable. Usually this is done by hosting the files by the backend server or through
reverse-proxying the backend server(s) and webserver(s).


## Continuous Integration

### Travis CI

[Travis CI][travis] is a continuous integration service, which can monitor GitHub for new commits
to your repository and execute scripts such as building the app or running tests. The angular-seed
project contains a Travis configuration file, `.travis.yml`, which will cause Travis to run your
tests when you push to GitHub.

You will need to enable the integration between Travis and GitHub. See the Travis website for more
instruction on how to do this.

### CloudBees

CloudBees have provided a CI/deployment setup:

<a href="https://grandcentral.cloudbees.com/?CB_clickstart=https://raw.github.com/CloudBees-community/angular-js-clickstart/master/clickstart.json">
<img src="https://d3ko533tu1ozfq.cloudfront.net/clickstart/deployInstantly.png"/></a>

If you run this, you will get a cloned version of this repo to start working on in a private git repo,
along with a CI service (in Jenkins) hosted that will run unit and end to end tests in both Firefox and Chrome.


## Contact

For more information on AngularJS please check out http://angularjs.org/

[git]: http://git-scm.com/
[bower]: http://bower.io
[npm]: https://www.npmjs.org/
[node]: http://nodejs.org
[protractor]: https://github.com/angular/protractor
[jasmine]: http://pivotal.github.com/jasmine/
[karma]: http://karma-runner.github.io
[travis]: https://travis-ci.org/
[http-server]: https://github.com/nodeapps/http-server