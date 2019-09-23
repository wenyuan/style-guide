# Vue.js编码规范
> 来源：[Vue.js官方风格指南](https://cn.vuejs.org/v2/style-guide/)

## 1. 工程目录安排
　　全局通用的组件放在 `/src/components/` 下<br/>
　　各页面/视图放在 `/src/views/` 下<br/>
　　全局公共指令、过滤器（多于三个文件以上引用）分别放在 `src/` 目录下的 `directives/`、`filters/`<br/>

　　当页面文件具有私有组件、指令、过滤器时，则建立一个与页面同名的目录，页面文件更名为 `index.vue`，然后在该目录下创建私有 `./components` 等文件夹<br/>
　　例如[vue-element-admin](https://github.com/PanJiaChen/vue-element-admin/tree/master/src)中：
```bash
src/
├── App.vue
├── assets
├── main.js
├── components
│   └── BackToTop
│   │   └── index.vue
├── directive
│   └── el-table
│   │   ├── adaptive.js
│   │   └── index.js
├── filters
│   └── index.js
└── views
    ├── login
    │   ├── auth-redirect.vue
    │   ├── components
    │   │   └── SocialSignin.vue
    │   └── index.vue
    ├── profile
    │   ├── components
    │   │   ├── Account.vue
    │   │   └── UserCard.vue
    │   └── index.vue
    └── zip
        └── index.vue
```

## 2. 文件夹命名规范
　　属于 `components` 文件夹下的子文件夹（仅是直接子文件夹），使用大写字母开头的 `PascalBase` 风格；<br/>
　　其它文件夹统一使用 `kebab-case` 的风格。<br/>
　　例如[vue-element-admin](https://github.com/PanJiaChen/vue-element-admin/tree/master/src/components/ImageCropper)中：
```bash
components/
├── BackToTop                     # BackToTop大写
│   └── index.vue
├── Charts                        # Charts大写
│   ├── Keyboard.vue
│   ├── LineMarker.vue
│   ├── MixChart.vue
│   └── mixins                    # mixins小写
│       └── resize.js
├── ImageCropper                  # ImageCropper大写
│   ├── index.vue
│   └── utils                     # utils小写
│       ├── data2blob.js
│       └── mimes.js
└── UploadExcel
    └── index.vue
```

## 3. 组件文件命名规范（.vue文件）
ref:
https://cn.vuejs.org/v2/style-guide/#%E7%BB%84%E4%BB%B6%E6%96%87%E4%BB%B6-%E5%BC%BA%E7%83%88%E6%8E%A8%E8%8D%90
https://www.jianshu.com/p/7e397fc3dd5c
https://segmentfault.com/a/1190000009805187?utm_medium=hao.caibaojian.com&utm_source=hao.caibaojian.com&share_user=1030000000178452
https://blog.csdn.net/weixin_43383257/article/details/84066742
