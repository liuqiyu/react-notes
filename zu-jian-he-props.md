# 组件 && props

组件可以将UI切分成一些的独立的、可复用的部件，这样你就只需专注于构建每一个单独的部件。

#### 使用es6class定义一个组件

```js
import React from 'react';

class Hello extends React.Component {
    render() {
        return (
            <h1>hello,world!</h1>
        )
    }
}

class Welcome extends React.Component {
    render() {
        return (
            <Hello></Hello> 
        )
    }
}

export default Welcome ;
```