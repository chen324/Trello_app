###########环境依赖      

**backend 部分**：  

​	"**class-validator**": "^0.12.0-rc.0", // 基于 `validator.js` 和 `TypeScript` 的数据验证工具，对用户或者接口调用传入的数据进行校验。

​	"**jsonwebtoken**": "^8.5.1", // `JWT` 鉴权库。

​	"**koa**": "^2.11.0", // 后端主框架。

​	"**koa-body**": "^4.1.1",

​	"**koa-bodyparser**": "^4.3.0",

​	"**koa-router**": "^8.0.8", // 基于 `koa` 的路由。

​	"**koa-static-cache**": "^5.1.2", // `koa` 静态文件代理。

​	"**koa-ts-controllers**": "^2.1.0", // 基于 `koa` 和 `Typescript` 构建的路由控制系统，它提供了各种装饰器来构建 `RESTful` 风格的 `API`

​	"**mysql2**": "^2.1.0", // `NodeJS` 连接操作 `MySQL` 的库。

​	"**sequelize**": "^5.21.5", // 一个功能更丰富和强大的数据库操作库，支持 `MySQL`、`MSSQL`、`SQLite` 等数据库，提供了 `ORM`、`事务` 以及 `Promise` 等支持。

​	"**sequelize-typescript**": "^1.1.0" // `sequelize` 的 `TypeScript` 版

​	"**ts-node-dev**": "^1.0.0-pre.44", // `ts-node`  的 `dev` 版，实现了热重载（修改代码即可自动重启服务）。

​    	"**sequelize-cli**": "^5.5.1" // `sequelize` 提供了的 `CLI` 工具，可以通过它来维护数据库。



**frontend 部分**：

​	"**axios**": "^0.19.2", // 基于 `promise` 的 `HTTP` 库，用来发送请求，获取数据

​    	"**core-js**": "^3.6.4",

​    	"**moment**": "^2.24.0", // 日期时间处理工具

​    	"**vue**": "^2.6.11",  // 前端主框架

​	"**vue-router**": "^3.1.6", // 前端的路由

​    	"**vuex**": "^3.1.3" // 前端数据管理



###########部署步骤

1.创建项目目录 `backend`，并通过 `npm init` 进行初始化。

2.`sequelize db:create` 是根据当前 `env` 值找到对应 `database.json` 中的配置，最后根据 `database` 项创建对应的数据库。`sequelize db:migrate` 是在数据库中创建相应的表以及字段信息。`sequelize db:seed:all` 可以生成数据。

3.利用 `npm run dev` 开启服务器。

4.创建项目目录 `frontend`，通过 `vue create vueapp` 构建项目。

5.通过输入 `yarn server` 运行项目。



###########目录结构描述
├─backend // 后端代码
│  │  .sequelizerc // `sequelize` 配置文件
│  │  package-lock.json // 环境依赖具体信息
│  │  package.json // 环境依赖
│  │  tsconfig.json // `TypeScript` 配置文件
│  │  
│  └─src // 后端源码
│      │  app.ts // 项目主入口文件，对静态资源代理，连接数据库，注册路由等
│      │  
│      ├─attachments // 评论相关资源
│      │      logo.png
│      │      upload_1debc8bfb7de326addc328b08b71d17f.png
│      │      upload_2ff1b6956b998a8e867881e31b650fbf.png
│      │      upload_35462bafd2fe69de74860f912da90c73.png
│      │      upload_3e5c4f8d0ea5738fe9811afa4e14c683.png
│      │      upload_4336b8b24c72f6d7e24eefe050beda7c.png
│      │      upload_623badb6cc5d70a0686f52e826c78f62.png
│      │      upload_6ff1e894da92b37be47e5153fba19020.png
│      │      upload_7dcdf469829b8f34b9406b4404a7fe1f.png
│      │      upload_7f92d4755c64a9a4b103da3ef73b20b3.png
│      │      upload_c4a8a40b2d4f95e4bacd61ad04a1fc03.png
│      │      upload_ca00206d6b5976457e95364ec5b48bc9.png
│      │      upload_f01187302c3425f479040f53363b9a14.png
│      │      upload_f682499d0335523278bc86bd113b6293.png
│      │      
│      ├─configs 
│      │      database.json // 连接数据库所需要的配置（包括测试，开发，生产等环境）
│      │      index.ts // 项目配置以及数据库配置文件
│      │      
│      ├─controllers // 控制器，通过 `TypeScript` 的装饰器与路由进行绑定
│      │      Board.ts // 面板路由
│      │      BoardList.ts // 面板列表路由
│      │      BoardListCard.ts // 卡片路由
│      │      Comment.ts // 评论路由
│      │      Test.ts // 测试路由
│      │      User.ts // 用户路由
│      │      
│      ├─database 数据库
│      │  ├─migrations // 迁移文件（创建表及表结构）
│      │  │      initAttachment.js // 卡片附件
│      │  │      initBoard.js // 任务面板
│      │  │      initBoardList.js // 任务列表
│      │  │      initBoardListCard.js // 任务卡片
│      │  │      initCardAttachment.js // 卡片附件关联
│      │  │      initComment.js // 评论
│      │  │      initUser.js // 用户
│      │  │      
│      │  └─seeders // 种子文件（生成数据）
│      │          initAttachment.js // 卡片附件
│      │          initBoard.js // 任务面板
│      │          initBoardList.js // 任务列表
│      │          initBoardListCard.js // 任务卡片
│      │          initCardAttachment.js // 卡片附件关联
│      │          initComment.js // 评论
│      │          initUser.js // 用户
│      │          
│      ├─middlewares // 中间件
│      │      authorization.ts // 验证
│      │      
│      ├─models // 模型类
│      │      Attachment.ts // 卡片附件
│      │      Board.ts // 任务面板
│      │      BoardList.ts // 任务列表
│      │      BoardListCard.ts // 任务卡片
│      │      CardAttachment.ts // 卡片附件关联
│      │      Comment.ts // 评论
│      │      User.ts // 用户
│      │      
│      ├─types // 类型声明文件
│      │      global.d.ts
│      │      koa.ext.d.ts
│      │      
│      └─validators // 验证类
│              Board.ts //  任务面板
│              BoardList.ts // 任务列表
│              BoardListCard.ts // 任务卡片
│              Comment.ts // 评论
│              CustomValidationDecorators.ts // 自定义验证装饰器
│              User.ts // 用户
│              
└─frontend // 前端代码
    └─vueapp
        │  .browserslistrc
        │  .env.development
        │  .gitignore
        │  babel.config.js
        │  package-lock.json
        │  package.json
        │  README.md // help
        │  vue.config.js
        │  yarn.lock
        │  
        ├─public // 资源文件
        │      favicon.ico
        │      index.html
        │      
        └─src // 源码
            │  App.vue // 主组件
            │  main.js // 项目主入口
            │  
            ├─api // 接口
            │      index.js
            │      
            ├─assets // 资源
            │  │  logo.png
            │  │  
            │  ├─css // 样式
            │  │  │  css.css
            │  │  │  
            │  │  └─fonts // 字体
            │  │          trellicons-iefix.eot
            │  │          trellicons.eot
            │  │          trellicons.ttf
            │  │          trellicons.woff
            │  │          
            │  └─images // 图片
            │          header-loading-logo.gif
            │          header-logo-2x.png
            │          lef-large.svg
            │          loading.gif
            │          right-large.svg
            │          trello-logo-blue.svg
            │          
            ├─components // 组件
            │  │  TCard.vue
            │  │  TComment.vue
            │  │  THeader.vue
            │  │  TList.vue
            │  │  TPagination.vue
            │  │  TPopup.vue
            │  │  TPopupMenu.vue
            │  │  
            │  └─TMessage
            │          TMessage.js
            │          TMessage.vue
            │          
            ├─filters
            │      dateTime.js
            │      
            ├─router // 路由文件
            │      index.js
            │      
            ├─store // 数据管理文件
            │  │  index.js
            │  │  
            │  ├─board
            │  │      index.js
            │  │      
            │  ├─card
            │  │      index.js
            │  │      
            │  ├─comment
            │  │      index.js
            │  │      
            │  ├─list
            │  │      index.js
            │  │      
            │  └─user
            │          index.js
            │          
            └─views // 视图文件
                    Board.vue
                    Card.vue
                    Home.vue
                    Login.vue
                    NotFound.vue
                    Register.vue
                    