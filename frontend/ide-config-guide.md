# 开发工具配置（IDE）

## 1. 适用背景
* WebStorm
* vue.js项目
* 基于vue-cli3构建


## 2. 代码风格标准
######　　ESLint + Prettier


## 3. 定制化调整
### 3.1 规则
* JavaScript代码不使用分号；
  * [尤雨溪对于javascript语句后要不要写分号的回答](https://www.zhihu.com/question/20298345/answer/49551142)
* JavaScript代码使用单引号；
* 缩进使用 2 个空格，不使用 4 个空格 或 tab 字符；
* ...

### 3.2 项目配置文件
　　在使用 `vue-cli3` 构建完项目后，做如下配置。
* 新建 `.eslintrc.js` 文件，配置如下内容：
```javascript
module.exports = {
  root: true,
  env: {
    node: true
  },
  extends: ["plugin:vue/essential", "@vue/prettier"],
  rules: {
    "no-console": process.env.NODE_ENV === "production" ? "error" : "off",
    "no-debugger": process.env.NODE_ENV === "production" ? "error" : "off",
    // 强制使用单引号
    'quotes': ['error', 'single'],
    // 关闭行末分号提示/报错
    'semi': 0
  },
  parserOptions: {
    parser: "babel-eslint"
  }
}
```

* 新建 `postcss.config.js` 文件，配置如下内容：
```javascript
module.exports = {
  plugins: {
    autoprefixer: {}
  }
}
```

* 新建 `prettier.config.js` 文件，配置如下内容：
```javascript
// prettier.config.js or .prettierrc.js 返回对象
module.exports = {
  eslintIntegration: true, // 开启 eslint 支持
  singleQuote: true, // 使用单引号
  tabWidth: 2, // 一个tab代表几个空格数，默认为80
  useTabs: false, // 是否使用tab进行缩进，默认为false，表示用空格进行缩减
  semi: false, // 行位是否使用分号，默认为true
  bracketSpacing: true //对象大括号直接是否有空格，默认为true，效果：{ foo: bar }
}
```

### 3.3 IDE代码自动格式化配置
　　WebStorm配置方式参考：[我的博客-WebStorm配置代码格式化](https://www.wenyuanblog.com/blogs/webstorm-eslint-prettier-reformat-code.html) <br/>
　　注意：不同版本下的WebStorm可能会略有不同。
