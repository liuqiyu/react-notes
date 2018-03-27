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

class App extends Component {
  render() {
    return (
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
    );
  }
}

export default App;
```

##### /src/components/about.js

```js
import React from 'react';

class About extends React.Component {
  render() {
    return (
      <h1>关于我们!</h1>
    );
  }
}

export default About;
```

##### /src/components/home.js

```js
import React from 'react';

class Home extends React.Component {
  render() {
    return (
      <h1>我爱我家!</h1>
    );
  }
}

export default Home;
```

##### /src/components/product.js

```js
import React from 'react';

class Productextends React.Component {
  render() {
    return (
      <h1>我爱我家!</h1>
    );
  }
}

export default Home;
```


