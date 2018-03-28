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
    
    render() {
        return (
            <div>
                <h1>clock</h1>
                <h2>当前时间是：{this.state.date.totoLocaleTimeString()}</h2>
            </div>
        )
    }
}
```