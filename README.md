# 小而美的脚手架-plop
## 安装plop包
```
yarn add plop --dev
```



## 根路径新建plopfile.js

```
// Plop 入口文件,需要导出一个函数
// 此函数接收一个Plop 对象，用于创建生成器任务

module.exports = plop => {
    plop.setGenerator('component', {
        description: 'create a component',
        prompts: [
            {
                type: 'input',
                name: 'name',
                message: 'component name',
                default: 'MyComponent'
            }
        ],
        actions: [
            {
                type: 'add', // 代表添加文件
                path: 'src/components/{{name}}/{{name}}.js',
                templateFile: 'plop-templates/component.hbs'
            },
            {
                type: 'add', // 代表添加文件
                path: 'src/components/{{name}}/{{name}}.css',
                templateFile: 'plop-templates/component.css.hbs'
            }
        ]
    })
}
```

## 新建模版文件(根路径下plop-templates)

**plop-templates/component.hbs**

```
import React from 'react';

export default function {{name}}(){
    return (
        <div className="{{name}}">
            <h1>{{name}} Component</h1>
        </div>
    )
}
```

**plop-templates/component.css.hbs**

````
.{{name}} {
    
}
````

 ## 命令生成

```
yarn plop component
```



## 总结

将plop 模块作为项目开发依赖安装

在项目根目录下创建一个`plopfile.js`文件

在`plopfile.js`文件中定义脚手架任务

编写用于生成特定类型文件的模版

通过plop 提供的CLI运行脚手架任务



## 创建react 模版项目

```
npx create-react-app plop-templeate
```

**新建components文件夹**

**app.js**

```
import './App.css';
import Header from './components/Header/Header'

function App() {
  return (
    <div className="App">
      <Header/>
    </div>
  );
}

export default App;

```

**app.css**

```
.App {
  text-align: center;
}
```


