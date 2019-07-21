# 项目介绍

基于 react+react-router+rudux 技术栈开发的一个租房项目

## 项目功能

- 1 登录
- 2 首页

## 导入路由模块

- 安装

```bash
npm i react-router-dom
```

## 引入semantic-ui-react组件库

- 安装

```npm
npm i semantic-ui-react
npm i semantic-ui-css
```

- 引入semantic-ui

```js
// 注意：semantic-ui-react是按需加载
import { Button } from 'semantic-ui-react'
```

- 引入样式文件

```js
// 在index.js中引入 样式文件
import 'semantic-ui-css/semantic.min.css'
```

- 点标记语法原理

```jsx
import React from 'react'
class Home extends React.Component {
  // 点标记语法
  render() {
    return (
      <Form>
        <Form.Input />
        <Form.Button />
      </Form>
    )
  }
}

class Form extends React.Component {
  render() {
    return (
      <div>
        我是一个form组件
        {this.props.children}
      </div>
    )
  }
  // 可以在组件内部去定义组件
  static Input = () => {
    return <div>Input组件</div>
  }

  static Button = () => {
    return <div>Button组件</div>
  }
}

export default Home

```

## 登录功能

### 文本受控组件

 ```jsx 
  //文本框添加 value={ this.state.pwd } onChange={ this.handleChange } 属性
  // 添加受控组件文本改变方法
  handleChange = e => {
    let {name, value} = e.target
    this.setState({
      [name]: value
    })
  }
 ```

### 引入axios

- 安装

```npm
npm i axios
```

- 使用

1. 在index.js文件中引入，不用再每个文件中多次引入

```js
import axios from 'axios'
```
2. 把axios对象绑定到React组件的原型上，将来所有的react组件都能访问到axios对象

```js
React.Component.prototype.axios = axios
```

3. 给axios对象配置默认全局路径

```js
axios.defaults.baseURL = 'http://47.96.21.88:8086/'
```

4. 给axios配置响应拦截器 直接把data中的数据返回
 ```js
 axios.interceptors.response.use(
   function(res) {

   },
   function(err) {

   }
 )
 ```

 ### 登录

 - 设置token

 - 编程式导航跳转到首页

 1. 引入withRouter实现编程式导航

 ```js
import { withRouter } from 'react-router-dom'
 ```

 2. 通过history对象跳转页面

 ```js
 let { history } = this.props

 // 跳转到主页
 history.push('/home')
 ```




