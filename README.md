# webpack
webpack 优化

## externals

externals 配置选项提供了「从输出的 bundle 中排除依赖」的方法。相反，所创建的 bundle 依赖于那些存在于用户环境(consumer's environment)中的依赖。此功能通常对 library 开发人员来说是最有用的，然而也会有各种各样的应用程序用到它。

防止将某些 import 的包(package)打包到 bundle 中，而是在运行时(runtime)再去从外部获取这些扩展依赖(external dependencies)。
例如，从 CDN 引入 jQuery，而不是把它打包：

index.html

```
  <script
  src="https://code.jquery.com/jquery-3.1.0.js"
  integrity="sha256-slogkvB1K3VOkzAI8QITxV3VzpOnkeNVsKvtkYLMjfk="
  crossorigin="anonymous">
</script>
```

webpack.config.js

```
module.exports = {
  //...
  externals: {
    jquery: 'jQuery'
  }
};
```

使用：
```
import $ from 'jquery';
$('.my-element').animate(/* ... */);
```


## 使用DllPlugin减少基础模块编译次数
