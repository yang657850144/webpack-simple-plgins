```js
// 声明 webpack 插件
function SimpleWebpackPlugin () {}
/**
 * 插件的原型上，定义 apply 方法
 * @param {*} compiler 返回一个 compiler 对象
 * compiler 对象表示 webpack 的完整配置，可以获取到 loader、plugin、options
 * 插件和 webpack 也是通过 compiler 对象进行关联的
 */
SimpleWebpackPlugin.prototype.apply = function(compiler) {
  // 挂载 webpack 提供的 Event Hook
  // compilation 对象表示一次资源版本构建，即当检测到某一个文件改变，就会构建一个新的 compilation
  // 一个  compilation 对象可以获取到当前模块的资源文件、编译生成资源、变更的文件，以及被跟踪的状态信息
  compiler.plugin('eventHook', function(compilation, callback) {
    // 执行相关逻辑
    // ...
    callback()
  })
}

```

- [Compiler 源码](https://github.com/webpack/webpack/blob/master/lib/Compiler.js)
- [Compilation 源码](https://github.com/webpack/webpack/blob/master/lib/Compilation.js)