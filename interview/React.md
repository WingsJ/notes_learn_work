React面经
    React的生命周期
        componentWillMount 在渲染前调用,在客户端也在服务端。
        componentDidMount  在第一次渲染后调用，只在客户端。之后组件已经生成了对应的DOM结构
        componentWillReceiveProps 在组件接收到一个新的 prop (更新后)时被调用。
        shouldComponentUpdate 返回一个布尔值。在组件接收到新的props或者state时被调用。
        componentWillUpdate 在组件接收到新的props或者state但还没有render时被调用。在初始化时不会被调用
        componentDidUpdate 在组件完成更新后立即调用。在初始化时不会被调用。
        componentWillUnmount 在组件从 DOM 中移除之前立刻被调用。