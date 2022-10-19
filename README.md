# 微信小程序([黑马](https://www.bilibili.com/video/BV1834y1676P?p=1))

[Toc]

## 项目结构

### 项目目录

    .
    ├── README.md
    ├── app.js：项目入口
    ├── app.json：全局配置
    ├── app.wxss：全局样式
    ├── pages: 页面
    │   ├── index: 每个页面都以单独的文件夹存放
    │   │   ├── index.js：页面数据、事件处理函数
    │   │   ├── index.json：页面配置，配置页面外观，表现
    │   │   ├── index.wxml：页面模板结构
    │   │   └── index.wxss：页面样式表
    │   └── logs
    │       ├── logs.js
    │       ├── logs.json
    │       ├── logs.wxml
    │       └── logs.wxss
    ├── project.config.json：项目配置
    ├── project.private.config.json
    ├── sitemap.json：小程序及其页面是否运行被微信索引
    └── utils：工具模块
        └── util.js

### JSON 配置文件

1. app.json

    ```js
    {
    "pages": [    //所有页面路径
        "pages/index/index",    //启动页面
        ...
    ],
    "window": {   //全局定义背景色、字体颜色等
        "backgroundTextStyle": "light",
        "navigationBarBackgroundColor": "#fff",
        "navigationBarTitleText": "Weixin",
        "navigationBarTextStyle": "black"
    },
    "style": "v2",    //全局组件样式版本
    "sitemapLocation": "sitemap.json" //sitemap.json位置
    }
    ```

2. preject.config.json

    ```js
    {
    "description": "项目配置文件",
    ...
    "setting": {  // 对应 `开发者工具` 的 本地设置
        ...
    },
        ...
    "appid": "wx2a955d42769a1899",    //appid
    "projectname": "miniprogram-92",  //项目名称
        ...
    }
    ```

3. sitemap.json 页面是否允许微信索引/SEO

    ```js
    {
    "desc": ...",
    "rules": [{
    "action": "allow",    // disallow 不允许微信索引
    "page": "*"
    }]
    }
    ```

4. /pages/index.json   index页面配置

### wxml 模板

1. 标签名称不同
    html (`div`, `span`, `img`, `a`)
    wxml (`view`, `text`, `image`, `navigator`)
2. 属性节点不同
    html (`a.href`)
    wxml (`navigator.url`)
3. `wxml` 提供了类似 `Vue` 的模板语法
    * 数据绑定
    * 列表渲染
    * 条件渲染

### wxss 样式

1. rpx 单位
    * 像素单位换算 css (`rem`) => wxss (`rpx`)
2. 提供全局样式和局部样式
    * 全局样式: app.wxss
    * 局部页面样式: /pages/index.wxss
3. wxss 仅支持部分 css 选择器
    * `.class` 和 `#id`
    * `element`
    * 并集选择器, 后代选择器
    * `::after` 和 `::before` 等伪类选择器

### js 逻辑交互

1. app.js

    ```js
    App({   // 启动小程序
    onLaunch() {
        ...
    }
    })
    ```

2. /pages/\*/\*.js

    ```js
        Page({  //创建并允许页面
            ...
        })
    ```

3. utils/\*.js

    ```js
    // 公共函数或属性
    const formatTime = date => {
        ...
    }

    module.exports = {
    formatTime
    }
    ```

## 宿主环境: 程序运行所必须依赖的环境

### 1. 通信模型

1. 通信主体
   * 逻辑层: `wxml`, `wxss`
   * 渲染层: `js`
2. 通信模型
   * 渲染层和逻辑层
   * 逻辑层和第三方服务

### 2. 运行机制

1. 启动过程
   * 下载代码到本地
   * 解析 app.json
   * 执行 app.js, 调用app()创建实列
   * 渲染首页
2. 渲染过程
   * 加载 json
   * 记在 wxml 和 wxss
   * 执行 js, 调用page()创建实列

### 3. 组件

1. 视图容器
   1. view
      * 普通视图区域
      * 类似 div
      * 常用于实现页面的布局效果
   2. scroll-view
      * 可滚动的视图区域
      * 常用来实现列表效果
   3. swiper 和 swiper-item
      * 轮播图容器和轮播图 Item

2. 基础内容
   1. text
      * 文本组件
      * 类似于 HTML 中的 span,是一个行内元素
   2. rich-text
      * 富文本组件
      * 支持把 html 字符串渲染为 wxml 结构

3. 表单组件
   1. button
      * open-type 调用微信功能(客服/转发/授权/获取用户信息等)
      * type 类型
      * size 尺寸
      * plain 镂空效果

4. 导航组件
   1. navigator

5. 媒体组件
   1. image
      * 默认 300px * 240px
      * mode 裁剪和缩放模式
6. 地图组件 map

7. 画布组件 canvas

8. 开发能力

9. 无障碍访问

### 4. API

1. 事件监听 API
    * on开头,监听某些事件触发
2. 同步 API
    * Sync 结尾, 通过返回值获取调用结果
3. 异步 API
    * 通过 success, fail, complete 获取调用结果

# d

## wxml

## wxss

## 全局配置

## 页面配置

## 网络请求

## 案列-本地生活

# d
## 页面导航
## 下拉刷新
## 上拉加载
## 常用生命周期

# d
## 自定义组件
## behaviors
## vant-weapp 组件库
## mobx
## promise 化

# d
## 使用 npm 包
## 全局数据共享
## 分包
## 案列 - 自定义 tabBar

# day 6 uni-app