---
title: webpack5内vue递归组件报错.md
date: 2023-03-06 18:23:13
tags: 前端
---

今天在一个webpack4升级到webpack5后的项目中，遇到了一个问题：
页面打开后，提示如下报错：
```
 ReferenceError: Cannot access '__WEBPACK_DEFAULT_EXPORT__' before initialization
 at Module.default (155747:3:42)
 at eval (index.vue?d775:50:1)
```

第一反应就是是不是webpack5哪里打包错误导致引用错误，然后进到项目文件里发现了一个递归组件
```
import MenuTree from '@/views/help-center/components/menu-tree';

export default {
    name: 'MenuTree',
    components: {
        MenuTree
    },
...    
}
```

结合报错信息，盲猜是打包的时候导入自身，而自身又没有引入引起的，于是将组件引入方法改成了动态引入
```
export default {
    name: 'MenuTree',
    components: {
        MenuTree: ()=> import("./index.vue"),
    },
...    
}
```
再打开页面，就发现正常工作了，详细原因日后补充，反正修好了