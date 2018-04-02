# 嵌套路由

嵌套路由。路由的子路由，类似vue-router的`children`。

##### demo1

app.js

```js
import React, { Component } from 'react';
import { BrowserRouter, Route, Switch } from 'react-router-dom';
import XHeader from './components/xheader';

import Page1 from './views/page1';
import Page2 from './views/page2';
import Page3 from './views/page3';


class App extends Component {
  render() {
    return (
      <BrowserRouter>
        <div className="App">
          <XHeader></XHeader>
          <div className="content">
            <Switch>
              <Route path='/page1' component={Page1}></Route>
              <Route path='/page2' exact component={Page2}></Route>
              <Route path='/page3' component={Page3}></Route>
            </Switch>
          </div>
        </div>
      </BrowserRouter>
    )
  }
}

export default App;
```