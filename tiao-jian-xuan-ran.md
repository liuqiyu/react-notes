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
  
  // 三目运算符
  
  return (
  
    {props.isLogin ? (<div>已登录</div>) : (<div>未登录</div>) }
  )
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

> 之所以能这样做，是因为在 JavaScript 中，true && expression 总是返回 expression，而 false && expression 总是返回 false。
> 因此，如果条件是 true，&& 右侧的元素就会被渲染，如果是 false，React 会忽略并跳过它。

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