# 初体验

```
npm install -g create-react-app

create-react-app app

cd app

npm start

// create-react-app 是React官方提供的一个用于快速搭建项目的脚手架  
// 但是打开项目会发现，一些与webpack相关的东西被隐藏掉了，只需要键入命令  

npm run eject  
```

#### JSX 简介

我们来观察一下声明的这个变量：

`const element = <h1>Hello, world!</h1>;`

这种看起来可能有些奇怪的标签语法既不是字符串也不是 HTML。

它被称为 JSX， 一种 JavaScript 的语法扩展。 我们推荐在 React 中使用 JSX 来描述用户界面。JSX 乍看起来可能比较像是模版语言，但事实上它完全是在 JavaScript 内部实现的。

##### 在 JSX 中使用表达式

你可以任意地在 JSX 当中使用 JavaScript 表达式，在 JSX 当中的表达式要包含在大括号里。

例如 2 + 2， user.firstName， 以及 formatName(user) 都是可以使用的。

```js
function formatName(user) {
  return user.firstName + ' ' + user.lastName;
}

const user = {
  firstName: 'Harper',
  lastName: 'Perez'
};

const element = (
  <h1>
    Hello, {formatName(user)}!
  </h1>
);

ReactDOM.render(
  element,
  document.getElementById('root')
);
```
##### JSX 本身其实也是一种表达式

在编译之后呢，JSX 其实会被转化为普通的 JavaScript 对象。

这也就意味着，你其实可以在 if 或者 for 语句里使用 JSX，将它赋值给变量，当作参数传入，作为返回值都可以：
```js
function getGreeting(user) {
  if (user) {
    return <h1>Hello, {formatName(user)}!</h1>;
  }
  return <h1>Hello, Stranger.</h1>;
}
```
##### JSX 属性