# h5 default - H5 多入口单页面前端脚手架

---

## GETTING STARTED

### 下载项目代码

### 修改 package

打开 package.json 根据项目情况修改以下部分
```json
{
  "name": "h5-default",    // 项目名称
  "description": "H5 多入口单页面前端脚手架",  // 描述
  "version": "1.0.0", // 版本
  "author": {  // 作者
    "name": "xujian1",
    "email": "xujian1@guazi.com"
  },
  ...
  ...
  "keywords": [  // 关键词
      "spa",
      "h5",
      "template"
  ],
  ...
}
```

### 修改全局配置
打开 global.config.js 按照说明修改成自己项目的设置

### 添加 entry

```yarn run addentry```

### 安装依赖
```shell
yarn
```

### 启动服务
```shell
yarn start
```

---

## 项目说明

### 目录结构
```
.
├── README.md
├── build  --  构建相关配置
│   ├── postcss.config.js
│   ├── template-loader.js
│   ├── webpack.analyzer.js
│   ├── webpack.dev.js
│   └── webpack.prod.js
├── global.config.js  --  项目级别全局配置
├── package.json
└── src  --  项目源码
    ├── common-tpl  --  公共 tpl
    ├── common-vue  --  公共 vue 组件
    ├── css  --  公共 css
    │   ├── base
    │   ├── ui-c2c
    │   ├── ui-c2c.less
    │   └── utils.less
    ├── entry  --  入口 js 和 html
    │   ├── entry1.html
    │   ├── entry1.js
    │   ├── entry2.html
    │   └── entry2.js
    ├── modules  --  模块
    │   ├── entry1
    │   └── entry2
    └── util  --  常用工具和通用逻辑
        ├── date-util.js
        ├── entry-util.js
        ├── mock-router.js
        ├── network-util.js
        ├── status-util.js
        ├── url-util.js
        └── vue-util.js

```



### 规范及约束
-    业务中每个页面应该有且只有一个对应的entry入口文件。
-    编写css时，为提高样式模块的可复用性，多复用样式应该单独目录且css中用到的静态文件（图片、字体……）应与其同目录。
-    强制使用 eslint 作为 js 代码规范


### 模块化
##### js

采用 es6 语法
```javascript
    
    import Widget from 'blusher/lib/widget'
    let widget = Widget.define({
           events : {},
           init : function(){
               //do something
           }
    });
    export default widget

```
tips: [es6特性 - Export 和 Import](http://es6-features.org/#ValueExportImport)

##### css
-    使用 less
-    通用 css 放在 ```src/css``` 下,  基于 vue 的模块 css 写在 vue 模板中, 通过拆分 vue 组件进行复用
-    基于 widget 的模块, 业务相关 css 放置在 模块目录中



### command line

-    ```yarn run build``` 产品环境编译
-    ```yarn run watch``` 开发模式 watch
-    ```yarn start``` 开发模式 server
-    ```yarn run analyzer``` 分析 webpack 打包结构
-    ```yarn run mock``` mock 请求模式运行 server



### 优化

#### CommonsChunkPlugin
抽离多个模块公用且在于 node_modules 下的 js 部分, 这部分 js 改变频率比较低, 可以尽可能利用浏览器缓存

#### ExtractTextPlugin
抽离 css 到单独文件