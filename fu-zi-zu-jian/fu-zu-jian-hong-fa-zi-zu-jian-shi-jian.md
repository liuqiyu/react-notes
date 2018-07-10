# 父组件触发子组件事件


<hr/>

** 父组件 **

```js

class Parent extends Component {
    render() (
        <div>
            <child ref="list"></child>
        </div>
    )
}
```

<hr/>

**子组件**

```js
class Child extends Component {
    contructor
    render() (
        <div></div>
    )
}
```
