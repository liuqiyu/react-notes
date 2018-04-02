# 按需加载


#### 按需加载 一

React Router 4.0：使用 babel-plugin-syntax-dynamic-import + react-loadable 实现按需加载
首先确保已安装 babel-plugin-syntax-dynamic-import 和 react-loadable，未安装请先安装：

```js
npm i -D babel-plugin-syntax-dynamic-import

npm i -S react-loadable

import Loadable from 'react-loadable';

const loadingComponent = ({ isLoading, error }) => {
  // Handle the loading state
  if (isLoading) {
    return <div>Loading...</div>;
  }
  // Handle the error state
  else if (error) {
    return <div>Sorry, there was a problem loading the page.</div>;
  }
  else {
    return null;
  }
};

const Home = Loadable({
  loader: () => import('../../views/home/index'),
  loading: loadingComponent
});
const Datalist = Loadable({
  loader: () => import('../../views/datalist/index'),
  loading: loadingComponent
});
const About = Loadable({
  loader: () => import('../../views/about/index'),
  loading: loadingComponent
});
const Clock = Loadable({
  loader: () => import('../../views/clock/index'),
  loading: loadingComponent
});
const Toggle = Loadable({
  loader: () => import('../../views/toggle/index'),
  loading: loadingComponent
});
const Status = Loadable({
  loader: () => import('../../views/status/index'),
  loading: loadingComponent
});
const Form = Loadable({
  loader: () => import('../../views/form/index'),
  loading: loadingComponent
});
```