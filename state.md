# state

> 不要直接更新状态
```
// Wrong
this.state.comment = 'Hello';

// Right
this.setState({
  comment: 'Hello',
})
``` 

> 状态可能是异步的

```
// Wrong
this.setState({
  counter: this.state.counter + this.props.increment,
});

// Correct正确
this.setState((prevState, props) => ({
  counter: prevState.counter + props.increment
}));
```



##### 时钟案列

```
import React from 'react';

class Clock extends React.Component {
  constructor (props) {
    super(props);
    this.state = {
      time: new Date(),
    }
  }
  
  componentDidMount() {
    this.timer = setInterval(() => {
      this.setState({
        time: new Date(),
      });
    })
  }
  
  componentWillUnmount() {
    clearInterval(this.timer)
  }
  
  render() {
    return (
      <div>
        <h1>
          计时器： { this.state.time.toLocaleTimeString() }
        </h1>
      </div>
    )
  }
}

export default Clock;
```