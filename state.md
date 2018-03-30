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