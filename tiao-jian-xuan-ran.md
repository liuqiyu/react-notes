# 条件渲染

> 判断渲染登录和注销两个页面

```js
import React from 'react';

function Page(props) {
  // 判断条件
  if (props.isLogin) {
    return (
      <div>已登录</div>
    )
  } else {
    return (
      <div>未登录</div>
    )
  }
}


class Status extends React.Component {
  constructor (props) {
    super(props);
    this.state = {
      isLogin: false
    }
    
    this.handleClick = this.handleClick.bind(this);
  }
  
  handleClick() {
    this.setState(prevState => ({
      isLogin: !prevState.isLogin
    }))
  }
  
  render() {
    return (
      <div>
        <button onClick={this.handleClick}>
          {this.state.isLogin ? '注销' : '登录'}
        </button>
        <Page isLogin={this.state.isLogin}></Page>
      </div>
    )
  }
}

export default Status;
```
### 与运算符 &&

```js
function Mailbox(props) {
  const unreadMessages = props.unreadMessages;
  return (
    <div>
      <h1>Hello!</h1>
      {unreadMessages.length > 0 &&
        <h2>
          You have {unreadMessages.length} unread messages.
        </h2>
      }
    </div>
  );
}

const messages = ['React', 'Re: React', 'Re:Re: React'];
ReactDOM.render(
  <Mailbox unreadMessages={messages} />,
  document.getElementById('root')
);
```