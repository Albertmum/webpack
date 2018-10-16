## webpack基本使用 
官方网址：https://webpack.docschina.org

    一、基础
    1.创建webpack文件夹
    2.初始化 npm init -y
    3.cnpm install --save-dev webpack-cli
    4.cnpm install --save-dev webpack
    5.调整package.json文件，增加"private": true,保证文件为私有的，移除main.js入口
    6.创建dist文件夹，创建index.html
    7.创建src文件夹，创建index.js
    8.在index.js中写逻辑代码
    9.npx webpack 整合资源自动在dist中创建main.js。
    
    二、如何使用一个配置文件
    1.新建一个webpack.config.js
    2.解析不同文件安装对应的loader即可以less为例
    3.新建一个less文件并在index引入
    4.npm官网搜索less-loader 
        安装less-loader：
        cnpm install --save-dev less-loader less
        cnpm install style-loader --save-dev
        cnpm install --save-dev css-loader
    5.在配置的js文件中增加
        // webpack.config.js
    module.exports = {
        ...
        module: {
            rules: [{
                test: /\.less$/,
                use: [{
                    loader: "style-loader" // creates style nodes from JS strings
                }, {
                    loader: "css-loader" // translates CSS into CommonJS
                }, {
                    loader: "less-loader" // compiles Less to CSS
                }]
            }]
        }
    };
    
    三、配置自动打包 自动刷新页面
        使用 webpack-dev-server 设置以下：
    1.安装：
    npm install --save-devwebpack-dev-server
    2.修改配置文件，告诉开发服务器(dev server)，在哪里查找文件：
    webpack.config.js中增加 
    devServer: {
        contentBase: './dist'
    },
    3.package.json中再添加一个 script 脚本，可以直接运行开发服务器(dev server)：
    "scripts": {
      "test": "echo \"Error: no test 
      "start": "webpack-dev-server --open",
    },
    4.npm run start 即可


    