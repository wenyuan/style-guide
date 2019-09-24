# Vue.js编码规范
> 来源：[Vue.js官方风格指南](https://cn.vuejs.org/v2/style-guide/)

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
　　位于 `views` 文件夹下的组件。<br/>
　　`views`文件夹下面是由 **以页面为单位的vue文件** 或者 **模块文件夹** 组成的。



## 3. 组件文件命名规范（.vue文件）
* 属于 `components` 下的组件名采用 `PascalBase` 风格，各模块的入口文件`index.vue`采用小写；
* 其它地方的组件名采用 `kebab-case` 的风格。

## 4. 资源文件命名规范(.js .less等)
* 资源文件一律采用 `kebab-case` 的风格。


## 4. views命名
views 文件夹下面是由 以页面为单位的 vue 文件 或者 模块文件夹 组成的，放在 src 目录之下，与 components、assets 同级。
#### 4.1 views下的文件夹取名
* views 下面的文件夹代表着模块的名字
* 由名词组成（car、order、cart）
* 单词只能有一个（good: car order cart）（bad: carInfo carpage）
* 尽量是名词（good: car）（bad: greet good）
* 以小写开头（good: car）（bad: Car）
#### 4.2 views 下的 vue 文件命名
* views目录下面的vue文件代表着页面的名字
* 放在模块文件夹之下
* 只有一个文件的情况下不会出现文件夹，而是直接放在 views 目录下面，如 Login Home
* 尽量是名词
* 大写开头，开头的单词就是所属模块名字（CarDetail、CarEdit、CarList）
* 名字至少两个单词（good: CarDetail）（bad: Car）
* 常用结尾单词有（Detail、Edit、List、Info、Report）
* 以 Item 结尾的代表着组件（CarListItem、CarInfoItem）


## 5. vue 方法命名
#### 4.1 vue 方法放置顺序
```bash
1.  components
2.  props
3.  data
4.  created
5.  mounted
6.  activited
7.  update
8.  beforeRouteUpdate
9.  metods
10. filter
11. computed
12. watch
```
#### 4.2 method 自定义方法命名
* 动宾短语（good：jumpPage、openCarInfoDialog）（bad：go、nextPage、show、open、login）
* ajax 方法以 get、post 开头，以 data 结尾（good：getListData、postFormData）（bad：takeData、confirmData、getList、postForm）
* 事件方法以 on 开头（onTypeChange、onUsernameInput）
* init、refresh 单词除外
* 尽量使用常用单词开头（set、get、open、close、jump）
* 驼峰命名（good: getListData）（bad: get_list_data、getlistData）
#### 4.3 data props 方法注意点
* 使用 data 里的变量时请先在 data 里面初始化
* props 指定类型，也就是 type
* props 改变父组件数据 基础类型用 $emit ，复杂类型直接改
* ajax 请求数据用上 isLoading、isError 变量
* 不命名多余数据，现在是详情页、你的数据是 ajax 请求的，那就直接声明一个对象叫 d，而不是每个字段都声明
* 表单数据请包裹一层 form
#### 4.4 生命周期方法注意点
* 不在 mounted、created 之类的方法写逻辑，取 ajax 数据，
* 在 created 里面监听 Bus 事件




ref:
https://cn.vuejs.org/v2/style-guide/#%E7%BB%84%E4%BB%B6%E6%96%87%E4%BB%B6-%E5%BC%BA%E7%83%88%E6%8E%A8%E8%8D%90
https://www.jianshu.com/p/7e397fc3dd5c
https://segmentfault.com/a/1190000009805187?utm_medium=hao.caibaojian.com&utm_source=hao.caibaojian.com&share_user=1030000000178452
https://blog.csdn.net/weixin_43383257/article/details/84066742
