# 移动端

#### 按需加载
在`create-react-app`中使用按需加载

```js
$ npm install antd-mobile --save


```

* package.json
```js
/* package.json */
$ npm install react-app-rewired --save-dev

"scripts": {
-   "start": "react-scripts start",
+   "start": "react-app-rewired start",
-   "build": "react-scripts build",
+   "build": "react-app-rewired build",
-   "test": "react-scripts test --env=jsdom",
+   "test": "react-app-rewired test --env=jsdom",
}
```

* 然后在项目根目录创建一个 config-overrides.js 用于修改默认配置。

```js
module.exports = function override(config, env) {
  // do stuff with the webpack config...
  return config;
};
```

