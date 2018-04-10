# 导航栏选中

### 安装

```js
npm install --save redux
npm install --save react-redux
```

### 文件结构
```
。
├── src
    ├── store
        ├── action.js
        ├── reducer.js
        ├── index.js
    ├── components
        ├── menu.js  导航组件
    ├── index.js
```

### 代码

* store/action.js

```js
export const currentNavIndex = (text) => {
    return {
        type: 'CURRENT_NAV_INDEX',
        text,
    };
};
```

* store/reducer.js

```js
const initState = {
    text: '',
}

const reducer = (state = initState, action) => {
    switch(action.type) {
        case 'CURRENT_NAV_INDEX':
            return {
                text: action.text,
            };
        default:
            return state;
    }
}

export default reducer;
```

* store/index.js

```js
    import { createStore } from 'redux';
    import reducer from './reducer';
    
    let store = createStore(reducer);
    
    export default store;
```

* index.js

```js
import React from 'react';
import ReactDOM from 'react-dom';
import { Provider } from 'react-redux';
import 'antd/dist/antd.css';
import './style/reset.css';
import './style/base.css';
import App from './containers/app/App';
import store from './store/index';
import registerServiceWorker from './registerServiceWorker';


console.log(process.env.NODE_ENV)
ReactDOM.render(
  <Provider store={store}>
    <App />
  </Provider>,
  document.getElementById('root'));
registerServiceWorker();

```

    