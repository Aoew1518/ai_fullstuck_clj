# Vue 单项应用
项目只有一个html项目，所有的能在浏览器看见的页面都只是这个html中的一个代码片段

# v-model
双向数据绑定， 让data数据源中的变量和input中的value实时双向同步

# 组件化
组件化是vue.js最强大的功能之一，组件是可复用的vue实例，可以嵌套在其他vue实例中，组件化使代码更加容易复用，组件化使代码结构更加清晰
把代码分出去写一个独立的文件，再引入回来生效

1. 代码复用
2. 逻辑分明，结构清晰

# 父子组件通讯
1. 父组件v-bind绑定xx属性
2. 子组件通过props接受xx属性


# 动手
1. 只要列表有数据，列表就出现，购物车为空 就不出现
2. 将数据渲染完成
3. 购买的数量可以加减，减少到1为最小值，就不能再减少
4. 可以移除不想购买的数据
5. 实时计算总价格