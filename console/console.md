
> 稳定性: 2 - 稳定的

`console` 模块提供了一个简单的调试控制台，它与 Web 浏览器提供的 JavaScript 控制台的机制类似。

该模块导出两个特定组件：

* 一个 `Console` 类，包含 `console.log()` 、 `console.error()` 和 `console.warn()` 等方法，可以用于写入到任何 Node.js 流。
* 一个全局的 `console` 实例，用于写入 `stdout` 和 `stderr`。
  因为该对象是一个全局变量，所以使用时无需调用 `require('console')`。

例子：使用全局的 `console`：

```js
console.log('hello world');
// 打印: hello world 到 stdout
console.log('hello %s', 'world');
// 打印: hello world 到 stdout
console.error(new Error('错误信息'));
// 打印: [Error: 错误信息] 到 stderr

const name = 'Will Robinson';
console.warn(`Danger ${name}! Danger!`);
// 打印: Danger Will Robinson! Danger! 到 stderr
```

例子：使用 `Console` 类：

```js
const out = getStreamSomehow();
const err = getStreamSomehow();
const myConsole = new console.Console(out, err);

myConsole.log('hello world');
// 打印: hello world 到 out
myConsole.log('hello %s', 'world');
// 打印: hello world 到 out
myConsole.error(new Error('错误信息'));
// 打印: [Error: 错误信息] 到 err

const name = 'Will Robinson';
myConsole.warn(`Danger ${name}! Danger!`);
// 打印: Danger Will Robinson! Danger! 到 err
```

虽然 `Console` 类的 API 是根据浏览器的 `console` 对象设计的，但 Node.js 中的 `Console` 并没有完全复制浏览器中的功能。

