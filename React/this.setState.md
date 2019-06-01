# React 内部状态 state

关于setState（）方法的ReactJS文档有点令人困惑。在一个大而大胆的红色警告中，它指出setState（）不会立即改变this.state，但会创建挂起状态转换。调用此方法后访问this.state可能会返回现有值 

> setState只在合成事件和构子函数中是异步的,在原生事件和setTimeout中都是同步的.

    1.setState的异步并不是说内部由异步代码实现,其实本身执行的过程和代码都是同步的,只是合成事件和构子函数的顺序在更新之前,导致在合成事件和构子函数中没法立马拿到更新后的值,
    形成了所谓的异步当然可以通过第二个参数setState(partialState,callback)中的callback拿到更新后的结果
  
    2.setState的批量更新优化也是建立在异步(合成事件,构子函数)之上的在原生事件setTimeout中不会批量更新,在异步中如果对同一个值进行多次setState,setState的批量更新策略
    会对其进行覆盖,取最后一次的执行,如果同时setState多个不同的值,在更新时会对其进行合并批量更新
       
>setState()有两个参数 一个对象一个回调函数

    1.不使用回调函数,打印出来就是this.state中的值
    2.使用回调函数,这个函数相当于使用生命周期中的
    ComponentDidUpdata函数的作用
    
      