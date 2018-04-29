# 解决跨域问题

## 开发环境

使用代理，在package.json添加一下代码：

```json
"proxy": {
    "/api": {
      "target": "http://auto.stosz.com",
      "changeOrigin":true
    }
  }
```