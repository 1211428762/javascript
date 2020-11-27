# package.json阅读

####  1.gulp

1. [npm](https://www.npmjs.com/package/gulp)
2. [文档](https://www.gulpjs.com.cn/docs/api/concepts/)
3. [github](https://github.com/gulpjs/gulp)
4. 作用:gulp是工具链，构建工具，可以配合各种插件做JS压缩，CSS压缩，less编译替代手动实现自动化工作.

​	前端的构建工具常见的有Grunt、Gulp、Webpack三种，Grunt比较老旧，功能少，更新少，插件少。

Gulp侧重于前端开发的控制管理

webpack侧重于模块依赖 

#### 2.gulp-autoprefixer

1. [npm](https://www.npmjs.com/package/gulp-autoprefixer)
2. [github](https://github.com/sindresorhus/gulp-autoprefixer)
3. 作用:根据浏览器的不同版本自动处理浏览器的前缀，实现css浏览器的兼容。（特别是移动页面的开发）
4. 使用 ` gulp autoFx` 自动添加css浏览器兼容前缀，并将添加后的最终.css文档保存在dist文件夹中

#### 3.gulp-cssmin

1. [npm](https://www.npmjs.com/package/gulp-cssmin)
2. [文档](https://developer.aliyun.com/mirror/npm/package/gulp-cssmin)
3. [github](https://github.com/pdehaan/gulp-cssmin)
4. 作用:压缩css,作用同**gulp-clean-css**

#### 4.gulp-sass

1. [npm](https://www.npmjs.com/package/gulp-sass)
2. [github](https://github.com/dlmanning/gulp-sass#readme)
3. 作用:编译sass文件,作用同**gulp-ruby-sass**,前者需要node环境,后者需要**ruby**环境

####  5.gulp-sass

1. [官网](https://highlightjs.org/)
2. [npm](https://www.npmjs.com/package/highlight.js)
3. [github](https://github.com/highlightjs/highlight.js/)
4. 作用:用于在任何web页面上着色显示各种示例源代码语法的JS项目。自动检测语言种类;支持多语言混合的代码高亮;兼容任意js框架;支持使用任何HTML标记

#### 6.html-webpack-plugin

1. [npm](https://www.npmjs.com/package/html-webpack-plugin)

2. [github](https://github.com/jantimon/html-webpack-plugin)

3. 作用:生成.html文件

   ```js
   {
     entry: 'index.js',
     output: {
       path: 'dist',
       filename: 'index_bundle.js'
     },
     plugins: [
       new HtmlWebpackPlugin(), // Generates default index.html 
       new HtmlWebpackPlugin({  // Also generate a test.html 
         filename: 'test.html',
         template: 'src/assets/test.html'
       })
     ]
   }
   ```

#### 7.json-loader

1. [npm](https://www.npmjs.com/package/json-loader)
2. [文档](https://www.webpackjs.com/loaders/json-loader/)
3. [github](https://github.com/webpack-contrib/json-loader#readme)
4. 作用:允许导入json文件

#### 8.json-templater

1. [npm](https://www.npmjs.com/package/json-templater)
2. [文档](https://developer.aliyun.com/mirror/npm/package/json-templater)
3. [github](https://github.com/lightsofapollo/json-templater)
4. 作用:require json文件时,可以使用{{}}模版语法

#### 9.karma

1. [npm](https://www.npmjs.com/package/karma)
2. [官网](http://karma-runner.github.io/latest/index.html)
3. [github](https://github.com/karma-runner/karma)
4. 作用:是一个简单的javascript测试工具，它允许在多个真正的浏览器执行JavaScript代码.

#### 10.karma-chrome-launcher

1. [npm](https://www.npmjs.com/package/karma-chrome-launcher)
2. [github](https://github.com/karma-runner/karma-chrome-launcher#readme)
3. 作用:用vue-cli生成项目时，如果选择了单元测试，那么会采用karma+mocha作为单元测试框架，默认使用的浏览器是PhantomJs。使用需要配置

修改配置
**karma.conf.js**
  browsers:['Chrome']

修改浏览器配置。

运行查看

  \#karma start test/unit/karma.conf.js

  成功启动Chrome浏览器

#### 11.karma-coverage

1. [npm](https://www.npmjs.com/package/karma-coverage)
2. [文档](https://www.zybuluo.com/wangxingkang/note/790416#karma%E6%8F%92%E4%BB%B6%E4%B9%8Bkarma-coverage)
3. [github](https://github.com/karma-runner/karma-coverage)
4. 作用:测试代码覆盖率以检测测试质量。

#### 12.karma-mocha

1. [npm](https://www.npmjs.com/package/karma-mocha)
2. [github](https://github.com/karma-runner/karma-mocha#readme)
3. 作用:一个单元测试框架/库，它可以用来写测试用例

#### 13.karma-sinon-chai

1. [npm](https://www.npmjs.com/package/karma-sinon-chai)
2. [翻译文档](https://www.jianshu.com/p/f200a75a15d2)
3. [github](https://github.com/kmees/karma-sinon-chai)
4. 作用:一个测试断言库，所谓断言，就是对组件做一些操作，并预言产生的结果。如果测试结果与断言相同则测试通过。

#### 14.karma-sourcemap-loader

1. [npm](https://www.npmjs.com/package/karma-sourcemap-loader)
2. [github](https://github.com/demerzel3/karma-sourcemap-loader)
3. 作用:加载`.map`文件与js文件作为映射

#### 15.karma-spec-reporter

1. [npm](https://www.npmjs.com/package/karma-spec-reporter)
2. [文档](https://developer.aliyun.com/mirror/npm/package/karma-spec-reporter)
3. [github](https://github.com/mlex/karma-spec-reporter)
4. 作用:输出单元测试结果

#### 16.karma-webpack

1. [npm](https://www.npmjs.com/package/karma-webpack)
2. [github](https://github.com/ryanclark/karma-webpack)
3. 作用:单元测试主依赖包

#### 17.markdown-it

1. [npm](https://www.npmjs.com/package/markdown-it)
2. [文档](http://markdown-it.docschina.org/)
3. [github](https://github.com/markdown-it/markdown-it)
4. 作用:vscode中编辑markdown文件

#### 18.markdown-it-anchor

1. [npm](https://www.npmjs.com/package/markdown-it-anchor)
2. [github](https://github.com/valeriangalliat/markdown-it-anchor)
3. 作用:markdown文件中的锚点链接

​    使用方式:`“[名称](#id)”`

#### 19.markdown-it-chain

1. [npm](https://www.npmjs.com/package/markdown-it-chain)
2. [webpack-chain文档](https://github.com/Yatoo2018/webpack-chain/tree/zh-cmn-Hans)
3. [github](https://github.com/ULIVZ/markdown-it-chain)
4. 作用:允许使用webpack-chain API

#### 20.markdown-it-container

1. [npm](https://www.npmjs.com/package/markdown-it-container)
2. [github](https://github.com/markdown-it/markdown-it-container)
3. 作用:用于创建简化的块级定制容器的插件,Markdown  解析器的Fenced容器插件

#### 20.mini-css-extract-plugin

1. [npm](https://www.npmjs.com/package/mini-css-extract-plugin)

2. [github](https://github.com/webpack-contrib/mini-css-extract-plugin)

3. 作用:将css单独打包成一个文件的插件，它为每个包含css的js文件都创建一个css文件。它支持css和sourceMaps的按需加载。

   目前只有在webpack V4版本才支持使用该插件

#### 21.mocha

1. [npm](https://www.npmjs.com/package/mocha)
2. [官网](https://mochajs.cn/)
3. [github](https://github.com/mochajs/mocha)
4. 作用:是一个功能丰富的javascript测试框架，运行在[node.js](https://nodejs.org/)和浏览器中，使异步测试变得简单有趣。Mocha测试连续运行，允许灵活和准确的报告，同时将未捕获的异常映射到正确的测试用例。

#### 22.node-sass

1. [npm](https://www.npmjs.com/package/node-sass)
2. [github](https://github.com/sass/node-sass)
3. 作用:是一个库，它将Node.js绑定到LibSass（流行样式表预处理器Sass的C版本）。快速将scss文件本地编译为css，并通过连接中间件自动编译。

#### 23.optimize-css-assets-webpack-plugin

1. [npm](https://www.npmjs.com/package/optimize-css-assets-webpack-plugin)
2. [github](https://github.com/NMFR/optimize-css-assets-webpack-plugin)
3. 作用:主要是用来压缩css文件
   webpack4.x以上,可以默认压缩js文件,一般压缩css

#### 24.postcss

1. [npm](https://www.npmjs.com/package/postcss)
2. [文档](https://github.com/postcss/postcss/blob/master/docs/README-cn.md)
3. [github](https://github.com/postcss/postcss)
4. 作用:允许使用 JS 插件转换样式的工具。 这些插件可以检查（lint) CSS，支持 CSS Variables 和 Mixins， 编译尚未被浏览器广泛支持的先进的 CSS 语法，内联图片...
   PostCSS 的 [Autoprefixer](https://github.com/postcss/autoprefixer) 插件是最流行的 CSS 处理工具之一。

#### 25.progress-bar-webpack-plugin

1. [npm](https://www.npmjs.com/package/progress-bar-webpack-plugin)
2. [github](https://github.com/clessg/progress-bar-webpack-plugin)
3. 作用:编译进度条插件(控制台)

#### 26.rimraf

1. [npm](https://www.npmjs.com/package/rimraf)

2. [github](https://github.com/isaacs/rimraf)

3. 作用:使用webpack build文件项目时每次都会生成一个dist目录，有时需要把dist目录里的所以旧文件全部删掉，除了可以使用rm -rf /dist/命令删除外，还可以使用rimraf /dist/命令；

   `rimraf <path> [<path> ...]`

#### 27.sass-loader

1. [npm](https://www.npmjs.com/package/sass-loader)
2. [文档](https://www.webpackjs.com/loaders/sass-loader/)
3. [github](https://github.com/webpack-contrib/sass-loader)
4. 作用:用于js加载sass

#### 28.select-version-cli

1. [npm](https://www.npmjs.com/package/select-version-cli)
2. 作用:选择发布版本(git控制台)

#### 29.sinon

1. [npm](https://www.npmjs.com/package/sinon)
2. [官网](https://sinonjs.org/)
3. [github](https://github.com/sinonjs/sinon)
4. 作用:创建`test-doubles`从而帮助我们减少测试项编写的复杂度

#### 30.sinon-chai

1. [npm](https://www.npmjs.com/package/sinon-chai)
2. [github](https://github.com/domenic/sinon-chai)
3. 作用:配合sinon完成前端代码测试

#### 31.style-loader

1. [npm](https://www.npmjs.com/package/style-loader)
2. [文档](https://www.webpackjs.com/loaders/style-loader/)
3. [github](https://github.com/webpack-contrib/style-loader)
4. 作用:配合[`css-loader`](https://github.com/webpack/css-loader) 编译css
   建议将 `style-loader` 与 [`css-loader`](https://github.com/webpack/css-loader) 结合使用,本身不能单独使用

#### 32.transliteration

1. [npm](https://www.npmjs.com/package/transliteration)
2. [github](https://github.com/dzcpy/transliteration)
3. 作用:音译,将文字转译为拼音

#### 33.uglifyjs-webpack-plugin

1. [npm](https://www.npmjs.com/package/uglifyjs-webpack-plugin)
2. [github](https://github.com/webpack-contrib/uglifyjs-webpack-plugin)
3. 作用:用来缩小（压缩优化）js文件，至少需要`Node v6.9.0和Webpack v4.0.0版本`。

#### 34.uppercamelcase

1. [npm](https://www.npmjs.com/package/uppercamelcasen)

2. [github](https://github.com/samverschueren/uppercamelcase)

3. 作用:将代码变成大驼峰

   ```js
   const upperCamelCase = require('uppercamelcase');
   upperCamelCase('foo-bar');
   //=> FooBar
   upperCamelCase('foo_bar');
   //=> FooBar
   upperCamelCase('Foo-Bar');
   //=> FooBar
   upperCamelCase('--foo.bar');
   //=> FooBar
   upperCamelCase('__foo__bar__');
   //=> FooBar
   upperCamelCase('foo bar');
   //=> FooBar
   ```

#### 35.uppercamelcase

1. [npm](https://www.npmjs.com/package/uppercamelcasen)
2. [github](https://github.com/samverschueren/uppercamelcase)
3. 作用:将代码变成大驼峰

#### 36.url-loader

1. [npm](https://www.npmjs.com/package/url-loader)
2. [github](https://github.com/webpack-contrib/url-loader)
3. 作用:可以将html以及css中的图片打包成base64
   base64编码的图片不能像正常的图片可以进行缓存

#### 37.vue-template-compiler

1. [npm](https://www.npmjs.com/package/vue-template-compiler)
2. [github](https://github.com/vuejs/vue)
3. 作用:将Vue 2.0模板预编译为呈现函数，以避免运行时编译开销和CSP限制。在大多数情况下，应该将它与vue-loader一起使用，只有在编写具有非常特定需求的构建工具时才会单独使用它。

#### 38.vue-loader

1. [npm](https://www.npmjs.com/package/vue-loader)
2. [文档](https://vue-loader.vuejs.org/zh/guide/)
3. [github](https://github.com/vuejs/vue-loader)
4. 作用:基于webpack的一个的loader，解析和转换 .vue 文件，提取出其中的逻辑代码 script、样式代码 style、以及 HTML 模版 template，再分别把它们交给对应的 Loader 去处理，核心的作用，就是提取

#### 39.vue-template-es2015-compiler

1. [npm](https://www.npmjs.com/package/vue-template-es2015-compiler)
2. [github](https://github.com/vuejs/vue-template-es2015-compiler)
3. 作用:支持es6语法

#### 40.webpack

1. [npm](https://www.npmjs.com/package/webpack)
2. [文档](https://www.webpackjs.com/)
3. [github](https://github.com/webpack/webpack)
4. 作用:前端资源加载/打包工具。它将根据模块的依赖关系进行静态分析，然后将这些模块按照指定的规则生成对应的静态资源。

#### 41.webpack-cli

1. [npm](https://www.npmjs.com/package/webpack-cli)
2. [github](https://github.com/webpack/webpack-cli)
3. 作用:webpack脚手架

#### 42.webpack-dev-server

1. [npm](https://www.npmjs.com/package/webpack-dev-server)
2. [文档](https://www.webpackjs.com/configuration/dev-server/)
3. [github](https://github.com/webpack/webpack-dev-server)
4. 作用:用于快速开发应用程序,配置相关访问端口

#### 43.webpack-node-externals

1. [npm](https://www.npmjs.com/package/webpack-node-externals)
2. [github](https://github.com/liady/webpack-node-externals)
3. 作用:允许定义外部文件(不是捆绑模块的文件)



