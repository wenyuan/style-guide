# Vue.js编码规范
> 来源：[Vue.js官方风格指南](https://cn.vuejs.org/v2/style-guide/)

[1 工程目录安排](#1.工程目录安排)
[2. 文件夹命名规范](#2.文件夹命名规范)
　　[2.1 大小写规范](#2.1大小写规范)
　　[2.2 取名规范](#2.2取名规范)
[3. `.vue`文件命名规范](#2..vue文件命名规范)


## 1. 工程目录安排
* 全局通用的组件放在 `/src/components/` 下；
* 页面/视图放在 `/src/views/` 下；
* 全局公共指令、过滤器（多于三个文件以上引用）分别放在 `src/` 目录下的 `directives/`、`filters/`；
* 当页面文件具有私有组件、指令、过滤器时，则建立一个与页面同名的目录，页面文件更名为 `index.vue`，然后在该目录下创建私有 `./components` 等文件夹；

　　例如[vue-element-admin](https://github.com/PanJiaChen/vue-element-admin/tree/master/src)中：
```bash
src/
├── App.vue
├── assets
├── main.js
├── components                     # 全局通用组件
├── directive                      # 全局公共指令
├── filters                        # 全局公共过滤器
└── views                          # 页面/视图
    ├── login
    │   ├── components             # 私有组件
    │   └── index.vue
    └── profile
        ├── components             # 私有组件
        └── index.vue
```


## 2. 文件夹命名规范
### 2.1 大小写规范
* 属于 `components` 文件夹下的子文件夹（特指直接子文件夹），使用大写字母开头的 `PascalBase` 风格；
* 其它文件夹统一使用 `kebab-case` 的风格。

　　例如[vue-element-admin](https://github.com/PanJiaChen/vue-element-admin/tree/master/src/components/ImageCropper)中：
```bash
components/
├── BackToTop                     # BackToTop大写
│   └── index.vue
├── Charts                        # Charts大写
│   ├── MixChart.vue
│   └── mixins                    # mixins小写
│       └── resize.js
└── ImageCropper                  # ImageCropper大写
    ├── index.vue
    └── utils                     # utils小写
        ├── data2blob.js
        └── mimes.js
```
### 2.2 取名规范
#### 组件文件夹
　　位于 `components` 下的文件夹。
* 代表着这类模块的类别；
* 由名词组成（例如：`Charts`）
* 如果有两个以上单词，采用 `PascalBase` 风格（例如：`BackToTop`）
* 最好只有一个单词，特殊情况可例外（good: `Car`，`Order`，`Cart`）（bad: `CarInfo`，`CarPage`）


## 3. `.vue`文件命名规范
### 3.1 大小写规范
* 属于 `components` 下的组件名采用 `PascalBase` 风格，各模块的入口文件`index.vue`采用小写；
* 其它地方的组件名采用 `kebab-case` 的风格。

### 3.2 取名规范
#### 基础组件名
　　位于 `components` 文件夹下的基础组件。
* 应该全部以一个特定的前缀开头，比如 `Base`、`App` 或 `V`。[参考官方文档](https://cn.vuejs.org/v2/style-guide/#基础组件名-强烈推荐)
```bash
# 反例
components/
|- MyButton.vue
|- VueTable.vue
|- Icon.vue

# 好例子
components/
|- BaseButton.vue
|- BaseTable.vue
|- BaseIcon.vue
```
#### 单例组件名
　　位于 `components` 文件夹下的组件，这类组件在每个页面只使用一次，永远不接受任何 prop，是为你的应用定制的。
* 以 `The` 前缀命名，以示其唯一性。[参考官方文档](https://cn.vuejs.org/v2/style-guide/#单例组件名-强烈推荐)
```bash
# 反例
components/
|- Heading.vue
|- MySidebar.vue

# 好例子
components/
|- TheHeading.vue
|- TheSidebar.vue
```
#### 紧密耦合的组件名
　　位于 `components` 文件夹下的组件，该类组件只在某个父组件的场景下有意义，这层关系应该体现在其名字上。因为编辑器通常会按字母顺序组织文件，所以这样做可以把相关联的文件排在一起。
* 以父组件名作为前缀命名。[参考官方文档](https://cn.vuejs.org/v2/style-guide/#紧密耦合的组件名-强烈推荐)
```bash
# 反例
components/
|- SearchSidebar.vue
|- NavigationForSearchSidebar.vue

# 好例子
components/
|- SearchSidebar.vue
|- SearchSidebarNavigation.vue
```
#### 组件名中的单词顺序
　　位于 `components` 文件夹下的组件。[参考官方文档](https://cn.vuejs.org/v2/style-guide/#组件名中的单词顺序-强烈推荐)
* 组件名应该以高级别的 (通常是一般化描述的) 单词开头，以描述性的修饰词结尾。
* **官网的描述比较抽象，什么叫“高级别”的呢，直接看例子**：
```bash
# 反例
components/
|- ClearSearchButton.vue
|- ExcludeFromSearchInput.vue
|- LaunchOnStartupCheckbox.vue
|- RunSearchButton.vue
|- SearchInput.vue
|- TermsCheckbox.vue

# 好例子
components/
|- SearchButtonClear.vue
|- SearchButtonRun.vue
|- SearchInputQuery.vue
|- SearchInputExcludeGlob.vue
|- SettingsCheckboxTerms.vue
|- SettingsCheckboxLaunchOnStartup.vue
```
　　因为编辑器通常会按字母顺序组织文件，所以现在组件之间的重要关系一目了然。
#### 组件名使用完整单词
* 组件名应该倾向于完整单词而不是缩写，这样便于团队合作与后期维护。[参考官方文档](https://cn.vuejs.org/v2/style-guide/#完整单词的组件名-强烈推荐)
```bash
# 反例
components/
|- SdSettings.vue
|- UProfOpts.vue

好例子
components/
|- StudentDashboardSettings.vue
|- UserProfileOptions.vue
```
#### 页面/视图文件名
　　位于 `views` 文件夹下的`.vue`文件。<br/>
　　`views` 文件夹下面是由 **以页面为单位的vue文件** 或者 **模块文件夹** 组成的。
* `views` 目录下面的 `.vue` 文件代表着页面的名字；
* 只有一个文件的情况，直接放在 `views` 目录下面，如 `Login.vue`、`Home.vue`；
* 有 `utils` 等子文件夹时，在 `views` 下创建一个文件夹，要体现页面的名字， `.vue` 文件可与之同名；
* 有两个以上 `.vue` 文件时，在 `views` 下创建一个文件夹，要体现内部文件的所属类名（例如`car`），`.vue` 文件放在里面（例如`car-list.vue`，`car-detail.vue`）；
* 有私有组件时，在 `views` 下创建一个文件夹，要体现页面的名字，文件夹下必须有 `index.vue` 或 `index.js`；
* 尽量是名词；
* 除`components`下的，一律采用 `kebab-case` 的风格；
* 名字至少两个单词（good: `car-detail`）（bad: `car`）
* 常用结尾单词有（`detail`、`edit`、`list`、`info`、`report`）
* 私有`components`目录下，以 `Item` 结尾的代表着私有组件（`CarListItem`、`CarInfoItem`）


## 4. `.vue`文件内部编程规范
### 4.1 vue 方法放置顺序
######　　① components
######　　② props
######　　③ data
######　　④ created
######　　⑤ mounted
######　　⑥ activited
######　　⑦ update
######　　⑧ beforeRouteUpdate
######　　⑨ metods
######　　⑩ filter
######　　⑪ computed
######　　⑫ watch

### 4.2 prop 名大小写
* 在声明 `prop` 的时候，其命名应该始终使用 `camelCase`；
* 在模板和 JSX 中应该始终使用 `kebab-case`。[参考官方文档](https://cn.vuejs.org/v2/style-guide/#Prop-名大小写-强烈推荐)
```js
props: {
  greetingText: String
}
```
```html
<WelcomeMessage greeting-text="hi"/>
```

### 4.3 method 方法命名
* 动宾短语（good：`jumpPage`、`openCarInfoDialog`）（bad：`go`、`nextPage`、`show`、`open`、`login`）
* ajax 方法以 `get`、`post` 开头，以 `data` 结尾（good：`getListData`、`postFormData`）（bad：`takeData`、`confirmData`、`getList`、`postForm`）
* 事件方法以 `on` 开头（例如：`onTypeChange`、`onUsernameInput`）
* `init`、`refresh` 单词除外
* 尽量使用常用单词开头（例如`set`、`get`、`open`、`close`、`jump`）
* 驼峰命名（good: `getListData`）（bad: `get_list_data`、`getlistData`）

### 4.4 data props 方法注意点
* 使用 `data` 里的变量时请先在 `data` 里面初始化；
* `props` 指定类型，也就是 `type`；

### 4.5 生命周期方法注意点
* 不在 `mounted`、`created` 之类的方法里直接写取异步数据的逻辑，将方法抽象出来，只在此处调用；
* 在 `created` 里面监听 Bus 事件


## 5. 资源文件命名规范(.js .less等)
### 5.1 `.js` 文件命名规范
* 属于类的 `.js` 文件，除 `index.js` 外，使用 `PascalBase` 风格；
* 其他类型的 `.js` 文件，使用 `kebab-case` 风格
### 5.1 `.less` 等其它文件命名规范
* 一律采用 `kebab-case` 的风格。
