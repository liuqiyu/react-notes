# 元素渲染

元素构成React应用的最小单位。

#### 将元素渲染到DOM中

首先在html里面添加一个`id="app"`的`div`.

`<div id="app"></div>`

渲染

```js
import React from 'react';
import ReactDOM from 'react-dom';

const element = <h1>你好！</h1>

ReactDOM.render(
    element,
    document.getElementById('app')
);
```