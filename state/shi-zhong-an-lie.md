# 时钟案例

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