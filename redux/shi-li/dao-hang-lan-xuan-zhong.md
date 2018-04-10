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

* action.js

```js
export const currentNavIndex = (text) => {
    return {
        type: 'CURRENT_NAV_INDEX',
        text,
    };
};
```

* reducer.js

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

    