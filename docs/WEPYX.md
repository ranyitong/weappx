如果你很早关注这个项目，就会了解原来的项目名称叫做 `wepyx`。

看上去似乎是为 `wepy` 专门打造的。

但是随着时间的推移，渐渐发现，这个数据框架应该是独立于组件框架的。

在准备实现和 原生小程序 的对接中，暴露出来了这个问题。

因此，新项目相对老项目主要干了2件事情

- 将数据管理部分和组件框架分离
- 改了个名字（还是和微信有关系）

升级方案

1. 引入 wepyx 改成 weappx
```js
- import wepyx from 'wepyx'
+ import weappx from 'weappx'
```

2. 需要配合引入连接器，根据组件框架不同；目前实现的版本有 wepy 和 原生小程序
```js
+ import wepyConnector from 'weappx-wepy'
// or
+ import weappConnector from 'weappx-weapp'

// 和 wepyx 的单例相比，现在可以创建多个实例了，也是较大的区别之一
const store = weappx()

// init 现在必须得调用了，并且 connector 是必传的参数
store.init({
    connector: wepyConnector || weappConnector
})

store.model(...)

store.start()
```




