# CORS-Vulnerability-POC

这是一个用于检测和演示 **CORS（跨域资源共享）配置错误** 的轻量级概念验证（POC）脚本。可用于授权的安全测试、白帽子审计以及网络安全教学。

## 🎯 漏洞原理

当目标服务器在响应头中错误地配置了：
Access-Control-Allow-Origin: *
或者动态反射了请求的 Origin，并且开启了 `Access-Control-Allow-Credentials: true` 时，攻击者可以托管此 POC 页面，诱导受害者访问，从而在受害者不知情的情况下窃取其在目标网站的敏感数据（如会话信息、个人隐私等）。

## 🚀 使用方法

1. 将 `index.html` 下载并托管在你的测试服务器上（例如使用 `python -m http.server 8000` 启动，通过 `http://localhost:8000` 访问，或者解析到自定义域名如 `evil.com`）。
2. 用编辑器打开 `index.html`，修改修改脚本中的 `TARGET` 变量为你要测试的目标系统 URL：
   ```javascript
   const TARGET = '[https://target-example.com](https://target-example.com)';
