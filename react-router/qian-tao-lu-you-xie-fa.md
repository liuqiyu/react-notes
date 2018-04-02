# 嵌套路由

嵌套路由。路由的子路由，类似vue-router的`children`。

### demo1

##### app.js

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
              <Route path='/page1' component={Page1}></Route> //有子路由不能加exact
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

##### xheader.js

```js
import React from 'react';
import { Link } from 'react-router-dom';

class Xheader extends React.Component {
  constructor (props) {
    super(props);
  }
  
  render() {
    return (
      <div className="nav">
        <ul>
          <li>
            <Link to='/page1'>page1</Link>
          </li>
          <li>
            <Link to='/page2'>page2</Link>
          </li>
          <li>
            <Link to='/page3'>page3</Link>
          </li>
        </ul>
      </div>
    )
  }
}

export default Xheader;
```

##### page1.js

```js
import React from 'react';
import { Route, Link } from'react-router-dom';

const Message = ({ match }) => (
  <div>
    <h3>new messages</h3>
    <h3>{match.params.id}</h3>
  </div>
)

class Page1 extends React.Component {
  constructor (props) {
    super(props);
  }
  
  componentDidMount() {
    console.log(this.props.match)
  }
  
  render() {
    return (
      <div>
        <h1>
          <Link to='/page1/messages/1'>message</Link>
        </h1>
        <h1>
          <Link to='/page1'>about</Link>
        </h1>
        about
        
        <Route path={`${this.props.match.url}/messages/:id`} exact component={Message}/>
      </div>
    )
  }
}

export default Page1;
```

