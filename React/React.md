# React

  React 现在的版本 16.8.6  16.8.3  16.8.0  17.0.0
  
  16.8.3之后就可以不用生命周期因为出现了 hooks 增加了两个新生命周期 去掉了三个不安全的生命周期

  组件创建的三种方式 函数式  ES6 class  ES5 createClass()

  高阶组件：是一个高阶函数 接收一个组件返回一个新的组件

  组件通信:父子 子父 跨级
  
  传递方式

    1.props

    2.context（provder/consamc）

    3.redux

    4.发布订阅  $emit --流向--> $on

  生命周期

  样式覆盖 css modules

  合成事件
  
    合成事件的好处是组件销毁后他会自动消失  

    React的事件指向是 undefined 因为它没有this指向 React把所有事件冒泡都指向 document.body
  
  generator函数 并行加载 串行加载

### DvaJS

  dva首先是具有redux和redux-saga的数据流方案
  
  安装
  npm install dva-cli --s

  roadhogrc.mock.js === webpack

  cross-env 跨平台

  redux没有命名空间的概念

  combineReducers

  同步改变,是更改state的唯一地方
  reducers
  
### Css Module

  一共有两种方式

    一种局部  一种全局

    :local(){}局部

    :global(){}全局

    style-loader

    css-loader?module

    就可以启用css module

    sass-loader
