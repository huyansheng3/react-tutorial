[![Deploy](https://www.herokucdn.com/deploy/button.png)](https://heroku.com/deploy)

# React Tutorial

This is the React comment box example from [the React tutorial](http://facebook.github.io/react/docs/tutorial.html).

## To use

There are several simple server implementations included. They all serve static files from `public/` and handle requests to `/api/comments` to fetch or add data. Start a server with one of the following:

### Node

```sh
npm install
node server.js
```

### Python

```sh
pip install -r requirements.txt
python server.py
```

### Ruby
```sh
ruby server.rb
```

### PHP
```sh
php server.php
```

### Go
```sh
go run server.go
```

### Perl

```sh
cpan Mojolicious
perl server.pl
```

And visit <http://localhost:3000/>. Try opening multiple tabs!

## Changing the port

You can change the port number by setting the `$PORT` environment variable before invoking any of the scripts above, e.g.,

```sh
PORT=3001 node server.js
```



---
##笔记

###事件处理和参数合成
React里只需要把事件处理器以驼峰形式命名当作组件的props传入即可。React内部创建一套合成事件系统来使所有事件在IE8以上的浏览器表现一致。也就是说，React知道如何冒泡和捕获事件，而且你的事件处理器接收到的参数和W3C规范一致，无论你使用哪种处理器。

###幕后原理：自动绑定（ Autobinding ）和事件代理（ Event Delegation ）
**自动绑定**：在JavaScript创建回调的时候，为了保证 `this` 的正确性，一般都需要显式的绑定方法到它的实例上。在React中，所有方法都被自动绑定到它的组件实例上。React还缓存这些方法，所以CPU和内存都是非常高效。

**事件代理**：React实际上并没有把事件处理器绑定到节点本身。当React启动时，它在最外层使用唯一一个事件监听器处理所有事件。当组件被加载和卸载时，只是在内部添加或删除事件处理器。当事件触发时，React根据映射决定如何分发。当映射没有事件处理器时，会当作空处理。

###state工作原理
常用的通知Reacts数据变化的方法是调用 `setState(data,callback)` 。这个方法会合并data到 `this.state` 中，并重新渲染组件。**尝试把尽可能多的组件无状态化**。常用的模式是创建多个只负责渲染数据的无状态组件，在它们的上层创建一个有状态组件并把它的状态通过props传给子级。这个有状态的组件封装了所有用户的交互逻辑，而这些无状态的组件则负责声明式的渲染数据。

> 在需要用户输入时、服务请求时、时间变化等做出响应时，使用state。
> 创建一个状态化的组件时，思考表示它的状态最少需要哪些数据，并只把这些数据存入 `this.state`。

###数据流
React里，数据通过从上面介绍的 `props` 从拥有者流向归属者。这就是高效的单向数据绑定；拥有者们通过它们的 `props` 或 `state` 计算出一些值，并把这些值绑定到它们拥有的的组件的props上。因为这个过程会递归的调用，所以数据变化会自动在所有它们被使用的地方反映出来。

###Mixins
组件是React复用代码的最佳方式，但有时一些不同的组件间也需要共用一些功能。有时会被成为跨切面关注点。React使用 `mixins` 来解决这类问题。

###受控组件
**受控组件**：一个受控的组件有一个 `value` prop。渲染一个受控 `<input>` 会反映 `value` prop的值。所以在这个例子中，我们更接受用户提供的值来更新 `input` 组件的 `value` prop。
**不受控组件**：一个没有 `value` 属性的 `<input>` 是一个不受控的组件。*不受控*组件维持自己的内部状态。





