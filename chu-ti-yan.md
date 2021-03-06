

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

你可以使用引号来定义以字符串为值的属性：

`const element = <div tabIndex="0"></div>;`

也可以使用大括号来定义以 JavaScript 表达式为值的属性：

`const element = <img src={user.avatarUrl}></img>;`

切记你使用了大括号包裹的 JavaScript 表达式时就不要再到外面套引号了。JSX 会将引号当中的内容识别为字符串而不是表达式。

##### JSX 嵌套

如果 JSX 标签是闭合式的，那么你需要在结尾处用 />, 就好像 XML/HTML 一样：

`const element = <img src={user.avatarUrl} />;`

JSX 标签同样可以相互嵌套：

```js
const element = (
  <div>
    <h1>Hello!</h1>
    <h2>Good to see you here.</h2>
  </div>
);
```

>警告:
>因为 JSX 的特性更接近 JavaScript 而不是 HTML , 所以 React DOM 使用 camelCase 小驼峰命名 来定义属性的>名称，而不是使用 HTML 的属性名称。
>例如，class 变成了 className，而 tabindex 则对应着 tabIndex。

##### JSX 防注入攻击

你可以放心地在 JSX 当中使用用户输入：

```
const title = response.potentiallyMaliciousInput;
// 直接使用是安全的：
const element = <h1>{title}</h1>;
```
React DOM 在渲染之前默认会 过滤 所有传入的值。它可以确保你的应用不会被注入攻击。所有的内容在渲染之前都被转换成了字符串。这样可以有效地防止 XSS(跨站脚本) 攻击。

##### JSX 代表 Objects

Babel 转译器会把 JSX 转换成一个名为 React.createElement() 的方法调用。

下面两种代码的作用是完全相同的：

```
const element = (
  <h1 className="greeting">
    Hello, world!
  </h1>
);

const element = React.createElement(
  'h1',
  {className: 'greeting'},
  'Hello, world!'
);
```
React.createElement() 这个方法首先会进行一些避免bug的检查，之后会返回一个类似下面例子的对象：

```js
// 注意: 以下示例是简化过的（不代表在 React 源码中是这样）
const element = {
  type: 'h1',
  props: {
    className: 'greeting',
    children: 'Hello, world'
  }
};
```

这样的对象被称为 “React 元素”。它代表所有你在屏幕上看到的东西。React 通过读取这些对象来构建 DOM 并保持数据内容一致。