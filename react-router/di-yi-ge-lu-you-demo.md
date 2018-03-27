# 第一个路由demo

我们使用官方脚手架 `create-react-app`搭建项目

### 安装运行

* npm install -g create-react-app

* create-react-app app

* cd app

* npm i

* npm start

* npm install --save react-router-dom

### 教程

##### APP.JS

```js
import React , { component } from 'react';
import { BrowserRouter, Route, Link} from 'react-router-dom';

import Home from './component/home';
import Product from './component/product';
import About from './component/about';

class App extends React.Component {
    render() {
       <BrowserRouter>
        <div>
          <a href="/abc">家</a>
          <a href="/abc1">产品</a>
          <a href="/abc2">我们</a>
          <br/>
          <Link to="abc"> 家</Link>
          <Link to="abc1"> 产品</Link>
          <Link to="abc2">我们</Link>
          <br/>
          <Route path="/abc" component={Home}/>
          <Route path="/abc1" component={Product}/>
          <Route path="/abc2" component={About}/>
        </div>
      </BrowserRouter>
    }
}
```


