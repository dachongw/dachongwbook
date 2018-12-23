# 第1节：vue简介

## vue的特点

1. 模板（html里面套js）(A)
2. 双向数据绑定 (A)
3. 组件 (R)
4. vue(2.0)虚拟dom的概念
5. 数据代理

## vue的 2个核心概念
1. 响应的数据绑定
2. 组合的视图组件

## 数据绑定语法
1. {{}} innerText
2. {{{}}} innerHTML
3. v-bind:xxx = "yyy" 强制数据绑定 
4. v-on:xxx = "yyy" 事件监听

## 计算属性
### 计算属性高级
1. 通过get/set 方法实现对属性数据的显示和监视
2. 有缓存，在页面中多次读取数据，只调用1次get()
    computed: {
      fullName: {
    ​     get () { // 用来得到当前属性值，当读取当前属性值时回调
    ​         return this.firstName + '-' + lastName
    ​     },
    ​     set (val) { // 监视当前属性值的变化，当属性值发生变化时回调
    ​         // 更新相关的属性数据
    ​         var names = val.split('-')
    ​         this.firstName = names[0]
    ​         this.lastName = names[1]
    ​     }
      }
    }

## 动态绑定 class 和 style 

动态绑定 class

1.  :class = "a" 变量
2.  :class = "{ 'classA': isA, 'calssB': isB}" 对象 ，isA 为布尔值
3.  :style = "['classA', 'classB']" 数组

动态绑定 style 

1. :style = "{ color: activeColor, fontSize: fontSize + 'px'}"

## 条件渲染

1. v-if v-else
2. v-show
3. template v-if , 不能用 v-show

## 列表渲染

v-for

1. 遍历数组  / $index
2. 遍历对象 / $key
3. 扩展数组的方法：
   1. $set(index, value)
      1. vue 会对数组的方法做一次包装，已使 vue 能监听到数组内部数组的变化，从而直接更新视图层，替换数组时为数组添加 set 方法。
      2. 包装的方法包含：push, pop, shift, unshift, splice, sort, reverse
   2. $remove(value)
      1. vue 支持可以直接传数组的值，调用 remove 删除数组，相当于：

        `var index = this.arrs.indexOf(oldArr)
        arrs.splice(index, 1)`