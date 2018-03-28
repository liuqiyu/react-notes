# 时间组件

```react
import React from 'react';

class Clock extends React.Component {
    constructor(props) {
        super(props);
        this.state = {
            date: new Date(),
        };
    }
    
    componentDidMount() {
        this.timerID = setInterval(() => {
            return this.tick();
        });
    }
    
    componentWillUnmount() {
        clearInterval(this.timerID);
    }
    
    tick() {
        this.setState({
            date: new Date()
        })
    }
    
    render() {
        return (
            <div>
                <h1>clock</h1>
                <h2>当前时间是：{this.state.date.toLocaleTimeString()}</h2>
            </div>
        )
    }
}

ReactDOM.render(
    <Clock />,
    document.getElementById('root')
)
```