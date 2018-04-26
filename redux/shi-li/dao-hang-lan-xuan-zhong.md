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
import { Provider } from 'react-redux';        // !important
import 'antd/dist/antd.css';
import './style/reset.css';
import './style/base.css';
import App from './containers/app/App';
import store from './store/index';           // !important
import registerServiceWorker from './registerServiceWorker';


console.log(process.env.NODE_ENV)
ReactDOM.render(
  <Provider store={store}>    // !important
    <App />
  </Provider>,
  document.getElementById('root'));
registerServiceWorker();

```

* home.js

```js
import React from 'react';
import { Button } from 'antd';
import logo from './../../images/logo.svg';
import './home.css';
import { connect } from 'react-redux'
import { currentNavIndex } from '../../store/action'

class Home extends React.Component {
  constructor (props) {
    super(props);
  }
  
  componentDidMount() {
    this.props.currentNavIndex('1');
  }
  
  render() {
    return (
      <div className="home">
        <h1>这是首页</h1>
      </div>
    )
  }
}

// 重点 重点 重点 
export default connect(state => ({
  text: state.text,
}), {
  currentNavIndex,
})(Home);

```

* menu.js

```js
import { connect } from 'react-redux'
import { currentNavIndex } from './../store/action'

class XMenu extends React.Component {
  constructor (props) {
    super(props);
  }
  
  render() {
    console.log(this.props)
    const { text } = this.props;    
    
    return (
      <aside className="ant-layout-sider">
        <div className="ant-layout-logo">REACT</div>
        <Menu mode="inline" theme="dark"
              selectedKeys={[text]} defaultOpenKeys={['sub1']}>
          <SubMenu key="sub1" title={<span><Icon type="user" />我的demo1</span>}>
            <Menu.Item key="1" >
              <Link to="">首页</Link>
            </Menu.Item>
            <Menu.Item key="2" >
              <Link to="/form">表单</Link>
            </Menu.Item>
          </SubMenu>
        </Menu>
      </aside>
    )
  }
}


export default connect(state => ({
  text: state.text,
}), dispatch => ({
  currentNavIndex: () => dispatch(currentNavIndex),
}))(XMenu)

```

    