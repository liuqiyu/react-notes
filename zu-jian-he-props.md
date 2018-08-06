# 组件 && props

组件可以将UI切分成一些的独立的、可复用的部件，这样你就只需专注于构建每一个单独的部件。

#### 使用es6class定义一个组件

```js
import React from 'react';

class Hello extends React.Component {
    constructor(props) {
        super(props);
    }
    render() {
        return (
            <h1>hello,{this.props.value}!</h1>
        )
    }
}

class Welcome extends React.Component {
    render() {
        return (
            <Hello value="world"></Hello> 
            // 组合组件
            <Hello value="world"></Hello> 
        )
    }
}

export default Welcome;
```

> 提示：组件名称必须以大写字母开头。

#### props的只读性

>无论是使用函数或者类来声明一个组件，它决不能修改它的自己的props。

```js

// 纯函数 -> 它没有改变自己的输入值【a&b】。
function sum(a, b) {
    return a + b
}

// 非纯函数 -> 它改变自身的输入值
function change(a) {
    a++
}
``` 

> 所有的组件必须像纯函数那样操作使用它们的props..

#### 父组件异步



