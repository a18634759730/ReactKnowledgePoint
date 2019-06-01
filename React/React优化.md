 
# React性能优化,你需要知道以下几个点

### 一.React组件的性能优化(渲染角度优化)
  
#### 1.react性能查看工具

    再性能优化之前，我们需要先了解一下如何查看React加载组件时所耗费的时间工具
    在react16版本之前我们可以使用React Perf来查看

    可以在chorme中先安装React Perf扩展，然后在入口文件或者redux的store.js中加入
  
> import Perf from 'react-addons-perf'    
> const win = window;
> win.Perf = Pert

> 在最新的React16版本中，我们可以直接在url后加上?react_pref就可以在chrome浏览器的performance，我们可以查看User Timeing来查看组件的加载时间

#### 2.单个react组件性能优化
  
   render里面尽量减少新建变量和bind函数,传递参数是尽量减少传递参数的数量

   比如我要实现一个点击按钮使相应的num增加1，我们有哪一些方法
    
   > 无非下面3种方法

    construtor(){
        this.handleClick1 = this.handleClick1.bind(this)
    }
    <button onClick={this.handleClick1}>btn1</button>
    <button onClick={this.handleClick2.bind(this)}>btn2</button>
    <button onClick={()=>{this.handleClick3()}}>btn3</button> 
   

> 第一种是构造函数中绑定this,第二种是在render()函数绑定this第三种就是使用箭头函数，

    但是那一种方法性能最好,是我们要考虑的问题，答案是第一种因为第一种,构造函数每一次渲染时
    候只会执行一遍而第二种方法,在每次render()的时候都会重新执行一遍函数;第三中的话,每一次
    render()的时候，都会生成一个新的箭头函数即使两个箭头函数的内容是一样的 

   
#### 定制shouldComponentUpdata函数
  
    shouldComponentUpdata是决定react组件时什么能够不重新渲染的函数,但是这个函数
    默认的实现方式就是简单的放回一个true。也就是说默认每次更新的时候都要调用所有的
    生命周期函数，包括render函数,重新渲染
  
> 在最新的react中,react给我们提供了 React.PureComponent 官方也在早期提供了名为    react-addons-pure-render-mixin插件来重新实现 shouldComponentUpdata生命周期方法
> 不要直接为props设置对象或者数组、不要将方法直接绑定在元素上，因为其实函数也是对象         