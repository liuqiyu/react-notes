# API

<hr/>

#### `<Provider store>`

通常，你无法使用`connect()`去`connent`一个没有继承`Provider`的 组件。

**props**

* `store`： 应用中唯一的状态store
* `children`： 应用的子组件

**example**

```
ReactDOM.render(
  <Provider store={store}>
    <App />
  </Provider>,
  document.getElementById('root')
);
```
<hr/>

#### `connect([mapStateToProps], [mapDispatchToProps], [mergeProps], [options])`

**props**

* `[mapStateToProps]`：如果制定了此参数，订阅了`react store`,任何时候`store`更新，`mapStateToProps`将会被调用。必须是一个普通的对象。如果不想订阅`react store`更新，可以通过`null`或`undefined`取代`mapStateToProps`;
```js
export default connect(state => ({
  proData: state.proData,
}), {
  getProData, 
})(Production);
```
* `[mapDispatchToProps]`：
* `[mergeProps]`：
* `[options]`：





