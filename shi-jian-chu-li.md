# 事件处理

React 元素的事件处理和 DOM元素的很相似。但是有一点语法上的不同:

> React事件绑定属性的命名采用驼峰式写法，而不是小写。

> 如果采用 JSX 的语法你需要传入一个函数作为事件处理函数，而不是一个字符串(DOM元素的写法)

```js
// 传统html
<button onclick="click()">
    html
</button>

// react 
<button onClick={click}>
    react
</button>
```

> 你必须谨慎对待 JSX 回调函数中的 this，类的方法默认是不会绑定 this 的。如果你忘记绑定 this.handleClick 并把它传入 onClick, 当你调用这个函数的时候 this 的值会是 undefined。

```js
import React from 'react';

class Toggle extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      isToggleOn: false,
    }
    
    this.handleClick = this.handleClick.bind(this);
  }
  
  handleClick() {
    this.setState(prevState => ({
      isToggleOn: !prevState.isToggleOn
    }))
  }
  
  render() {
    return (
      <div>
        <button onClick={this.handleClick}>
          {this.state.isToggleOn ? 'on' : 'off'}
        </button>
      </div>
    )
  }
}

export default Toggle;
```