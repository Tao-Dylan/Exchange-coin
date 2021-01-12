# coin-exchange

## 简介

币交所 web 前台，项目简称 `CEC`

## 快速构建&部署

包管理器 `yarn` 与 `npm` 类似，下面默认只写 `yarn`

> `Node.js` 最好 `v10+`

进入项目根目录，执行 `yarn install` 安装依赖

依赖安装成功后，执行 `yarn run build` 命令进行构建

构建完成后，构建产物在 `/dist` 文件夹

## 快速开发引导

### 开发环境

> Node.js, v10+
>
> [Yarn](https://yarnpkg.com)，可选用于替代 npm

### 开发准备

1. `yarn` 或 `yarn install` 安装依赖
2. `yarn run serve` 启动开发热更新服务器

### 快速开发

1. 在 `page` 下新建 `demo.app.js` 入口 ，将会得到 `demo.html`。内容参考其他。
2. 在 `page`下新建 `demo.vue`，作为 `demo.html`页面的根组件。
3. 直接在 `demo.vue` 上进行开发，如有需要，引用组件。

## 项目大体流程

### 使用技术

Vue + Vue CLI 3 + Element UI + SCSS + Vue I18n

### 目录结构

```
coin-exchange
├─ .browserslistrc                  # 指定项目的目标浏览器的范围
├─ .editorconfig                    # EditorConfig, 定义基本的编码风格
├─ .env                             # 指定环境变量
├─ .eslintrc.js                     # ESlint 配置
├─ .gitignore
├─ .idea                            # JetBrains IDEs 项目配置
├─ .npmrc                           # npm 配置
├─ .prettierrc.js                   # Prettier 配置, 用于统一代码风格
├─ babel.config.js
├─ dist                             # 项目构建产品输出目录
├─ node_modules
├─ package.json
├─ postcss.config.js
├─ public                           # 静态资源，直接被拷贝
│    ├─ favicon.ico
│    └─ index.html                  # 生成 html 默认模板
├─ src
│    ├─ assets                      # 静态资源
│    ├─ common                      # 项目公共代码
│    ├─ components                  # Vue 组件
│    ├─ locales                     # 国际化翻译文件
│    │    ├─ en.js
│    │    ├─ zh-CN.js
│    │    └─ zh-HK.js
│    ├─ pages                       # 多页面入口
│    │    ├─ demo.app.js            # 将生成 /demo.html
│    │    └─ index.app.js           # 首页 /index.html 的入口
│    └─ plugins                     # 第三方库
├─ title.config.js
├─ vue.config.js                    # Vue Cli 调整 webpack 配置
└─ yarn.lock                        # Yarn 固化依赖
```

### 构建相关

项目基于 `vue cli3` 搭建
因为 vue cli 3 隐藏了 webpack 配置，通过根目录的 `vue.config.js` 进行配置、修改，具体见官网。

### 多页面入口

`src/pages` 目录中以 `.app.js` 为后缀的文件为入口文件，
将生成以 `src/pages` 为根目录的同层次同名的 html 。

### 公共代码

1. `src/common/page-common.js` 为页面公共 js 入口
2. 公共 js 引入了公共样式，其入口为 `src/common/style/index.scss`

### Element UI 自定义主题

因默认主题与项目不一致，故需要对其组件的样式进行一一的替换

自定义样式入口 `src/plugins/element.scss`

可参照 table 组件

### 国际化

1. 国际化方案基于 [Vue I18n](https://kazupon.github.io/vue-i18n/)
2. 国际化文件在 `src/locales` 里面
3. 页面显示语言判断流程，优先读取 url `lang`，其次读取 cookie，最后读取 `navigator.language` ，如读取的语言都不支持，将回退至默认语言

## 团队合作

### 代码检查 ESlint

基于 vue cli ，选择了最轻的 `vue/essential`规则

[vue 官方风格指南](https://cn.vuejs.org/v2/style-guide/)
[eslint-plugin-vue Available rules](https://eslint.vuejs.org/rules/)

### 代码风格 Prettier

1. 使用了 [Prettier](https://prettier.io/) 统一代码风格。
2. 另，也用 [EditorConfig](https://editorconfig.org/) 辅助。
3. 基于 vue cli 配置了 `pre-commit` gitHooks，commit 时自动格式化代码

### IDE

强烈推荐使用 `WebStorm` ，因为配置了一系列支持。

> `.idea` 目录中，排除了个人相关，将项目相关配置提交至 git 仓库，以达到项目成员共享。
>
> 因此使用 WebStorm 打开项目，无需进行设置就可以进行开发

#### 其他 IDE/编辑器？

请根据实际进行下面所以或部分设置。

1. webpack + 智能感知？因为 vue cli 3 隐藏了 webpack 配置，会导致 IDE 无法解析模块引用，进而影响智能感知和跳转。需要设置为 `<projectRoot>/node_modules/@vue/cli-service/webpack.config.js` 。详见[官方文档](https://cli.vuejs.org/zh/guide/webpack.html#以一个文件的方式使用解析好的配置)。
2. Eslint 实时错误提示。
3. 安装 [Prettier](https://prettier.io/)、 [EditorConfig](https://editorconfig.org/) 插件以得到统一代码风格支持。这是可选的，也可直接执行 `yarn run lint` 进行格式化或等待 commit 时的自动格式化。


curl --user myusername:mypassword --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "getwalletinfo", "params": [] }' -H 'content-type: text/plain;' http://127.0.0.1:8332/

Official_No1@163.com 账号 密码 abc5341842
前台暂时全部控制amount 小数点后面6位 目前测试btc  tron 和eth 小数点后要6位 

//保留两位小数   
//功能：将浮点数四舍五入，取小数点后2位  
function toDecimal(x) {  
    var f = parseFloat(x);  
    if (isNaN(f)) {  
        return;  
    }  
    f = Math.round(x*100)/100;  
    return f;  
}  


//制保留2位小数，如：2，会在2后面补上00.即2.00  
function toDecimal2(x) {  
    var f = parseFloat(x);  
    if (isNaN(f)) {  
        return false;  
    }  
    var f = Math.round(x*100)/100;  
    var s = f.toString();  
    var rs = s.indexOf('.');  
    if (rs < 0) {  
        rs = s.length;  
        s += '.';  
    }  
    while (s.length <= rs + 2) {  
        s += '0';  
    }  
    return s;  
}  
  
function fomatFloat(src,pos){     
      return Math.round(src*Math.pow(10, pos))/Math.pow(10, pos);     
}  
//四舍五入  
alert("保留2位小数：" + toDecimal(3.14159267));  
alert("强制保留2位小数：" + toDecimal2(3.14159267));  
alert("保留2位小数：" + toDecimal(3.14559267));  
alert("强制保留2位小数：" + toDecimal2(3.15159267));  
alert("保留2位小数：" + fomatFloat(3.14559267, 2));  
alert("保留1位小数：" + fomatFloat(3.15159267, 1));  
          
        //五舍六入  
        alert("保留2位小数：" + 1000.003.toFixed(2));  
        alert("保留1位小数：" + 1000.08.toFixed(1));  
        alert("保留1位小数：" + 1000.04.toFixed(1));  
        alert("保留1位小数：" + 1000.05.toFixed(1));  
          
        //科学计数  
        alert(3.1415.toExponential(2));  
        alert(3.1455.toExponential(2));  
        alert(3.1445.toExponential(2));  
        alert(3.1465.toExponential(2));  
        alert(3.1665.toExponential(1));  
        //精确到n位，不含n位  
        alert("精确到小数点第2位" + 3.1415.toPrecision(2));  
        alert("精确到小数点第3位" + 3.1465.toPrecision(3));  
        alert("精确到小数点第2位" + 3.1415.toPrecision(2));  
        alert("精确到小数点第2位" + 3.1455.toPrecision(2));  
        alert("精确到小数点第5位" + 3.141592679287.toPrecision(5));  


