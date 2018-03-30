# 子组件触发父组件方法

> ` this.props.Change(event.target.value)`

```js
import React from 'react';

class SearchBar extends React.Component {
  constructor (props) {
    super(props);
    this.change = this.change.bind(this);
  }
  
  change(event) {
    this.props.Change(event.target.value)
  }
  
  render() {
    return (
      <div>
        <input type="text" value={this.props.value} onChange={this.change}/>
        <h1>{this.props.value}</h1>
      </div>
    )
  }
}

class DataList extends React.Component {
  // constructor (props) {
  //   super(props)
  // }
  
  render() {
    return (
      this.props.data.map((item, index) => {
        return (
          <div key={index}>
            <span>{item.name}</span>
            <span>{item.age}</span>
          </div>
        )
      })
    )
  }
}

const data = [
  {
    name: '六千',
    age: '18'
  },
  {
    name: '大的',
    age: '11'
  },
  {
    name: '刚发的',
    age: '22'
  },
  {
    name: '鬼地方个',
    age: '85'
  }
]

class ToDoList extends React.Component {
  constructor (props) {
    super(props);
    this.state = {
      wd: '',
      data: data,
    }
    this.change = this.change.bind(this);
  }
  
  change(value) {
    this.setState({
      wd: value
    });
    
    console.log(value)
    this.searchData(value)
  }
  
  searchData(value) {
    console.log(1)
    const list = [];
    data.forEach((item) => {
      console.log(item.age.indexOf(value))
      if (item.age.indexOf(value) >= 0) {
        list.push(item)
      }
    })
    this.setState({
      data: list,
    });
  }
  
  render() {
    return(
      <div>
        <SearchBar value={this.state.wd} Change={this.change}></SearchBar>
        <DataList data={this.state.data}></DataList>
      </div>
    )
  }
}

export default ToDoList;
```