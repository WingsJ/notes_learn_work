
React面经
    React的生命周期
        componentWillMount 在渲染前调用,在客户端也在服务端。
        componentDidMount  在第一次渲染后调用，只在客户端。之后组件已经生成了对应的DOM结构
        componentWillReceiveProps 在组件接收到一个新的 prop (更新后)时被调用。
        shouldComponentUpdate 返回一个布尔值。在组件接收到新的props或者state时被调用。
        componentWillUpdate 在组件接收到新的props或者state但还没有render时被调用。在初始化时不会被调用
        componentDidUpdate 在组件完成更新后立即调用。在初始化时不会被调用。
        componentWillUnmount 在组件从 DOM 中移除之前立刻被调用。
    
    redux的数据流向
        单向数据流调用<code> store.dispatch(action) -> reducer(state, action) -> store.getState()</code>

        Action 会触发给 Store 指定的 rootreducer
        rootreducer会返回一个完整的状态树，state状态树上的各个值都可以由对应的reducer来更新。

        （3）store会保存状态树
        更新完state后，新的 State 会替代旧的 State。然后可以添加监听函数<code>store.subscribe(listener)</code>在回调函数里面可以通过<code>store.getState()</code>来获取新的state。这样就能更新整个UI。只要调用<code>dispath</code>，state就会根据<code>reducer</code>对应更新，进而触发监听函数<code>subscribe</code>，然后触发回调函数渲染UI。

    组件间值传递通信
        父组件通过属性进行传递，子组件通过props获取
        子组件向父组件传值（回调函数）：通过回调进行传递数据
        利用react-redux进行组件之间的状态信息共享
        非嵌套组件间通信,利用二者共同父组件的 context 对象进行通信

    React中函数组件和类组件的区别
       函数组件没有this,没有生命周期，没有状态state,(useState,useEffect)
　　    类组件有this,有生命周期，有状态state

    setState是同步还是异步？
        在组件生命周期中或者react事件绑定中，setState是通过异步更新的。
        在延时的回调或者原生事件绑定的回调中调用setState不一定是异步的。
    
    react高阶组件
        高阶组件只是一个包装了另外一个 React 组件的 React 组件。

        代码复用，逻辑抽象，抽离底层准备（bootstrap）代码
        渲染劫持
        State 抽象和更改
        Props 更改

        
    redux处理异步的中间件
        redux-thunk
            redux-thunk中间件允许action是一个方法
            中间件收到action后会执行action方法并将结果提供给reducer
            action混乱导致不易维护
        redux-saga
            saga会监听action并基于这个action执行Effects操作
            Effects提供灵活的API，包括阻塞、非阻塞调用，取消、等待、race等操作
            方便隔离并执行异步操作，并易于测试 