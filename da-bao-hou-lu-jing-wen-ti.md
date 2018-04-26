# 打包后路径问题

package.json

```json
{
  "name": "subject-1",
  "version": "0.1.0",
  "private": true,
  "dependencies": {
    "antd-mobile": "^2.1.8",
    "react": "^16.3.2",
    "react-dom": "^16.3.2",
    "react-loadable": "^5.3.1",
    "react-redux": "^5.0.7",
    "react-router-dom": "^4.2.2",
    "react-scripts": "1.1.4",
    "redux": "^4.0.0"
  },
  "scripts": {
    "start": "react-app-rewired start",
    "build": "react-app-rewired build",
    "test": "react-app-rewired test --env=jsdom",
    "eject": "react-scripts eject"
  },
  "devDependencies": {
    "babel-plugin-import": "^1.7.0",
    "babel-plugin-syntax-dynamic-import": "^6.18.0",
    "node-sass": "^4.8.3",
    "react-app-rewired": "^1.5.2",
    "sass-loader": "^7.0.1"
  },
  "homepage": "./"  // 这里！！！！！！！！
}

```