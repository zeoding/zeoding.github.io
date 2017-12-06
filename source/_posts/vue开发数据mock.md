---
title: vue开发数据mock
---
> 我们常常在前端开发的时候需要用到各种各样的数据，这个时候我们往往会想到找后端的同事获取接口。如果在项目中前后端同时开发的情况下，我们做一些页面的时候就不能同步的获得到接口数据，这个时候我们就需要和后端同事协调好字段，进行数据mock来进行页面的继续开发

- 下面以vue官方提供的命令行工具来进行配置：

``` bash
没有安装vue官方命令的童鞋请到此链接出安装： https://cn.vuejs.org/v2/guide/installation.html#NPM
```
- 初始化后获得以下目录结构

![image](http://i4.bvimg.com/523028/e0434a3c5dbe9a73.png)

- 然后在更目录下创建一个叫 mock 的文件夹，在建立一个js文件


``` bash
命令行执行npm 安装 faker 和 lodash

npm install faker
npm install lodash
```
- 在mock文件夹下的js文件中添加以下代码就能快速的生成用户数据,更多的API使用查看[faker文档](https://github.com/FotoVerite/Faker.js)
``` bash
module.exports = function() {
  var faker = require("faker");
  faker.locale = "zh_CN";
  var _ = require("lodash");
  return {
    people: _.times(10, function(n) {
      return {
        id: n,
        name: faker.name.findName(),
        avatar: faker.internet.avatar()
      };
    }),
  };
};

```
- 在config下面配置我们的接口代理

![image](http://i4.bvimg.com/523028/b3300aa76b139e04.png)

- 打开package.json文件 配置“scripts” 加入以下代码 

``` bash
"mock": "json-server mock/data.js",
"mockdev": "npm run mock | npm run dev"
```
![image](http://i1.bvimg.com/523028/bbb92d57ef9168df.png)
###### 上面的代码是启动vue服务和生成mock数据的服务

``` bash
命令行执行 npm run mockdev 启动服务

在vue文件中使用http://localhost:3000/people链接就能获取到数据
```

![image](http://i1.bvimg.com/523028/b93e1a237ed83850.png)



