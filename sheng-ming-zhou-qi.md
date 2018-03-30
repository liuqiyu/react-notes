# state &7 生命周期

### 组件的生命周期

* `Mounting`:已插入真是Dom

* `Updating`:正在被重新渲染

* `Unmounting`:已移除真是Dom

##### 生命周期的方法

* `componentWillMount`: 在渲染前调用，在客服端也在服务端

* `componentDidMount`: 在第一次渲染后，也在客户端。之后组件已经生成了对应的DOM结构，可以通过`this.getDOMNode()`来进行访问。 如果你想和其他JavaScript框架一起使用，可以在这个方法中调用`setTimeout, setInterval`或者发送AJAX请求等操作(防止异部操作阻塞UI)。

* `componentWillReceiveProps`: 在组件接收到一个新的 `prop` (更新后)时被调用。这个方法在初始化`render`时不会被调用。

* `shouldComponentUpdate`: 返回一个布尔值。在组件接收到新的props或者state时被调用。在初始化时或者使用`forceUpdate`时不被调用。 
可以在你确认不需要更新组件时使用。

* `componentWillUpdate``: 在组件接收到新的props`或者`state`但还没有`render`时被调用。在初始化时不会被调用。

* `componentDidUpdate`: 在组件完成更新后立即调用。在初始化时不会被调用。

* `componentWillUnmount`: 在组件从 `DOM` 中移除的时候立刻被调用。

### 生命周期图

![](/assets/f616a6cad60f20b13a1ef44e9ef2e16d38beec0b.png)