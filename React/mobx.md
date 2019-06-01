# Mobx 

## Mobx 和 Redux 的比较

    Redux是单一的数据源,而Mobx往往可以根据应用的UI数据或业务逻辑来组织store
    Redux store是普通的Javascript对象结构，Mobx将常规的Javascript对象包裹,
    赋予observer的能力通过隐式订阅,自动跟踪observable的变化,Mobx是观察引用的，
    在跟踪函数中任何引用的observer的属性都会被记录,一旦引用改变,Mobx将做出反应,
    不在跟踪函数中的属性将不会被跟踪，在异步中访问的属性不会被跟踪

    Redux的state是只读的,只能通过将之前的state与触发的action结合,产生新的state，因此是纯洁的（pure）
    Mobx的state即可又读又写,action是非必须的,可以直接赋值改变因此是不纯净的（Impure）

> redux 管理的是 (STORE -> VIEW -> ACTION) 的整个闭环，
> 而 mobx 只关心 STORE -> VIEW 的部分 

 
### 优点

        1.基于运行时的数据订阅 mobx 的数据依赖始终保持了最小，而且还是基于运行时。
    而如果用 redux，可能一不小心就多订阅或者少订阅了数据。所以为了达到高性能，
    我们需要借助 PureRenderMixin 以及 reselect 对 selector 做缓存通过 OOP 的
    方式组织领域模型 (domain model) OOP 的方式在某些场景下会比较方便，尤其是容易抽取 domain model 的时候。

        2.进而由于 mobx 支持引用的方式引用数据，所以可以非常容易得形成模型图 (model graph )，
    这样可以更好地理解我们的应用。

        3.修改数据方便自然 mobx 是基于原生的 JavaScript 对象、数组和 Class实现的。
    所以修改数据不需要额外语法成本，也不需要始终返回一个新的数据，而是直接操作数据


## 缺点

        1.缺最佳实践和社区 mobx 比较新，遇到的问题可能社区都没有遇到过。
    并且，mobx 并没有很好的扩展/插件机制随意修改 store 我们都知道 redux 
    里唯一可以改数据的地方是 reducer，这样可以保证应用的安全稳定；

        2.而 mobx 可以随意修改数据，触发更新，给人一种不安全的感觉最新的mobx 2.2 加入了 action 的支持。
    并且在开启 strict mode 之后，就只有 action 可以对数据进行修改，限制数据的修改入口。可以解决这个问题

        3.逻辑层的限制如果更新逻辑不能很好地封装在 domain class 里，用 redux 会更合适。
    另外，mobx缺类 redux-saga 的库，业务逻辑的整合不知道放哪合适