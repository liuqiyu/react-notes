# 在react中使用sass

使用create-react-app脚手架配置react环境。再使用sass其实非常的简单。

* 安装依赖

`npm install sass-loader node-sass --save-dev`

* 开发环境

```js
// node_modules/react-scripts/config/webpack.config.dev.js

{
    loader: require.resolve('file-loader'),
    // Exclude `js` files to keep "css" loader working as it injects
    // it's runtime that would otherwise processed through "file" loader.
    // Also exclude `html` and `json` extensions so they get processed
    // by webpacks internal loaders.
    exclude: [/\.js$/, /\.html$/, /\.json$/,/\.scss$/],
    options: {
         name: 'static/media/[name].[hash:8].[ext]',
    },
},
{
    test: /\.scss$/,
    loaders: ['style-loader', 'css-loader', 'sass-loader'],
}
```