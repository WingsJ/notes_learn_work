Vue面经
    Vue的生命周期
        beforeCreate 组件的实例被创建之初,属性生效之前
        created 组件实例已经完全创建，属性也绑定，但真实 dom 还没有生成，$el 还不可用
        beforeMount 在挂载开始之前被调用：相关的 render 函数首次被调用
        mounted el 被新创建的 vm.$el 替换，并挂载到实例上去之后调用该钩子
        beforeUpdate 组件数据更新之前调用，发生在虚拟 DOM 打补丁之前
        update 组件数据更新之后
        activited keep-alive 专属，组件被激活时调用
        deactivated keep-alive 专属，组件被销毁时调用
        beforeDestory	组件销毁前调用
        destoryed 组件销毁后调用

    keep-alive
        keep-alive 是 Vue 内置的一个组件，可以使被包含的组件保留状态

        一般结合路由和动态组件一起使用，用于缓存组件；(meta)
        提供 include 和 exclude 属性，两者都支持字符串或正则表达式， include 表示只有名称匹配的组件会被缓存，exclude 表示任何名称匹配的组件都不会被缓存 
        其中 exclude 的优先级比 include 高；
        对应两个钩子函数 activated 和 deactivated ，当组件被激活时，触发钩子函数 activated，当组件被移除时，触发钩子函数 deactivated。
    
    v-show与v-if的区别
        v-if 是真正的条件渲染，因为它会确保在切换过程中条件块内的事件监听器和子组件适当地被销毁和重建；也是惰性的：如果在初始渲染时条件为假，则什么也不做——直到条件第一次变为真时，才会开始渲染条件块。
        v-show 就简单得多——不管初始条件是什么，元素总是会被渲染，并且只是简单地基于 CSS 的 “display” 属性进行切换。
        (v-if 适用于在运行时很少改变条件，不需要频繁切换条件的场景；v-show 则适用于需要非常频繁切换条件的场景。)

    
    Vue的路由权限控制
        Vue-Router的路由,beforeEach控制,addRoutes()添加动态路由,meta

    Vuex中的属性
        Vuex 是一个专为 Vue.js 应用程序开发的状态管理模式。每一个 Vuex 应用的核心就是 store（仓库）。“store” 基本上就是一个容器，它包含着你的应用中大部分的状态 (state)

        Vuex 的状态存储是响应式的。当 Vue 组件从 store 中读取状态的时候，若 store 中的状态发生变化，那么相应的组件也会相应地得到高效更新。
        改变 store 中的状态的唯一途径就是显式地提交 (commit) mutation。这样使得我们可以方便地跟踪每一个状态的变化。

        State：定义了应用状态的数据结构，可以在这里设置默认的初始状态。
        Getter：允许组件从 Store 中获取数据，mapGetters 辅助函数仅仅是将 store 中的 getter 映射到局部计算属性。
        Mutation：是唯一更改 store 中状态的方法，且必须是同步函数。
        Action：用于提交 mutation，而不是直接变更状态，可以包含任意异步操作。
        Module：允许将单一的 Store 拆分为多个 store 且同时保存在单一的状态树中。
    
    Vue 组件间通信有哪几种方式？
        props / $emit 适用 父子组件通信

        ref 与 $parent / $children 适用 父子组件通信
        ref：如果在普通的 DOM 元素上使用，引用指向的就是 DOM 元素；如果用在子组件上，引用就指向组件实例
        $parent / $children：访问父 / 子实例

        EventBus （$emit / $on） 适用于 父子、隔代、兄弟组件通信
        $attrs/$listeners 适用于 隔代组件通信
        provide / inject 适用于 隔代组件通信

        Vuex 适用于 父子、隔代、兄弟组件通信
    
    vue-router 路由模式有几种？
        vue-router 有 3 种路由模式：hash、history、abstract，对应的源码如下所示：

        hash:  使用 URL hash 值来作路由。支持所有浏览器，包括不支持 HTML5 History Api 的浏览器；

        history :  依赖 HTML5 History API 和服务器配置。具体可以查看 HTML5 History 模式；

        abstract :  支持所有 JavaScript 运行环境，如 Node.js 服务器端。如果发现没有浏览器的 API，路由会自动强制进入这个模式.
