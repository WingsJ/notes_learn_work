webpack
    entry
    output
    Loader与Plugin的区别
        Loader 本质就是一个函数，在该函数中对接收到的内容进行转换，返回转换后的结果。 因为 Webpack 只认识 JavaScript，所以 Loader 就成了翻译官，对其他类型的资源进行转译的预处理工作。

        Plugin 就是插件，基于事件流框架 Tapable，插件可以扩展 Webpack 的功能，在 Webpack 运行的生命周期中会广播出许多事件，Plugin 可以监听这些事件，在合适的时机通过 Webpack 提供的 API 改变输出结果。

        Loader 在 module.rules 中配置，作为模块的解析规则，类型为数组。每一项都是一个 Object，内部包含了 test(类型文件)、loader、options (参数)等属性。

        Plugin 在 plugins 中单独配置，类型为数组，每一项是一个 Plugin 的实例，参数都通过构造函数传入。

npm插件常用哪些
    js-cookie
    good-stroage
    sass-loader
    css-loader
    webpack
    webpack-cli

Cookie localStorage sessionStorage区别

        生命周期
            Cookie 可以有服务器生成 浏览器生成 关闭浏览器失效
            localStorage 永久保存
            sessionStorage 关闭页面or浏览器清除
            (vuex 页面刷新消失)
        大小
            cookie 4K
            Storage 5M
        服务器通信
            Cookie会被携带HTTP中
            Storage仅在客户端
        使用场景
            Cookie 验证信息 token
            Storage 保存本地数据
    跨域
        同源策略
            协议 + 域名 + 端口三者相同,即为同源

        解决方案
        JSONP 只接受GET请求 会受到XXS攻击 解决方法 0324.md 面试学习

        CORS 服务端

        cookie 跨域
            Axios withCredentials设置为true
            Fetch credentials设置为include

防抖 在执行事件,如果一定时间之内又触发,重新开始执行
节流 每隔一段时间执行一次

虚拟DOM工作原理
    用javascript对象表示virtual node(VNode)，根据VNode 计算出真实DOM需要做的最小变动，然后再操作真实DOM节点，提高渲染效率。
    高效的diff算法能够保证进行对实际的DOM进行最小的变动

ES6 --> ES5
    babel-loader {'parsets':['es2015']}

promise的链式调用
    使用then方法之后会返回一个promise对象，可以继续用then方法调用，再次调用所获取的参数是上个then方法return的内容

