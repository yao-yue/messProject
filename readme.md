vue开发环境构建。。。

npm i -D webpack webpack-cli   //webpack包

npm i -D html-webpack-plugin   //把webpack打包出来的js文件自动引入到html中，并自动修改js文件名

clean-webpack-plugin   //清除dist文件夹中上次残留的打包文件

npm i -D style-loader css-loader  //css文件解析
npm i -D less less-loader         //less文件解析

npm i -D postcss-loader autoprefixer  //为css文件添加浏览器前缀

npm i -D mini-css-extract-plugin  //拆分css
npm i -D extract-text-webpack-plugin@next  //拆分多个css

npm i -D babel-loader @babel/preset-env @babel/core  //babel转译js
npm i @babel/polyfill                       //新api的转换 例如(promise、Generator、Set、Maps、Proxy

npm i -D vue-loader vue-template-compiler vue-style-loader  
                    //vue-loader用于解析.vue文件 vue-template-compiler用于编译模板
npm i -S vue  

npm i -D webpack-dev-server   //进行热更新



### 区分开发环境和生产环境
实际应用到项目中，我们需要区分开发环境与生产环境，我们在原来webpack.config.js的基础上再新增两个文件
webpack.dev.js   开发环境配置文件
开发环境主要实现的是热更新,不要压缩代码，完整的sourceMap
webpack.prod.js  生产环境配置文件
生产环境主要实现的是压缩代码、提取css文件、合理的sourceMap、分割代码

需要安装以下模块:
npm i -D  webpack-merge copy-webpack-plugin optimize-css-assets-webpack-plugin uglifyjs-webpack-plugin
 
webpack-merge 合并配置
copy-webpack-plugin 拷贝静态资源
optimize-css-assets-webpack-plugin 压缩css
uglifyjs-webpack-plugin 压缩js


#### webpack mode设置production的时候会自动压缩js代码。
- 原则上不需要引入uglifyjs-webpack-plugin进行重复工作。但是optimize-css-assets-webpack-plugin压缩css的同时会破坏原有的js压缩，所以这里我们引入uglifyjs进行压缩


### webpack优化
- webpack 打包速度优化
1. 合理的mode参数和devtool参数
2. 缩小文件的搜索范围
3. 使用happyPack开启多线程loader转换
4. 使用webpack-parallel-uglify-plugin增强代码压缩
5. 抽离第三方模块
6. 配置缓存


- webpack 打包体积优化
1.  引入webpack-boundle-analyzer分析打包后的文件
2.  externals 
3.  tree-shaking


参考地址:[掘金文章](https://juejin.im/post/5de87444518825124c50cd36#heading-31)