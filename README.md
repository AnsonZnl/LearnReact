# 学习 React 笔记

## 官方教程
- [React-官方教程](https://zh-hans.reactjs.org/)

## 基本知识

## JSX

通过React.createElement(`<div><div>`, root)将虚拟DOM转化为真实的DOM节点，并挂载到指定的节点上

而第一个参数必须有一个子节点，如果不提供可以使用React.Fragments或者`<>...</>`替代。

## 组件

### class组件
需要从React.Component上继承，有state，和props，有生命周期。

``` js
class List extends React.Component {
    constructor(props){
        super(props)
    }
    render(){
       const {list} = this.props;
        return 
        <div>
            {list.map((item,index)=>{
               return 
               <li key={item.id}>
                  <span>{item.title}</span>
               </li>
             })}
        <div>
    }
}
```

**特点**
- 有组件实例
- 有生命周期
- 有state 和 setState

### 函数组件
直接写一个函数，接收props（相当于函数参数），

``` js

function List(props){
    const list = props;
    reutrn <ul>
           {list.map((item,index)=>{
            return <li key={item.id}>
               {item.title}
            </li>
           })}
     </ul>
}
```

**特点**
- 没有组件实例
- 没有生命周期
- 没有state和setState，只有props


## Hook

React V16.8新增的特性。

在不实使用Class组件的情况下使用state
### useState

替代之前的this.setState，每次都有通过前面的setValue方法去设置值

``` js
function Example(){
    // 声明一个“count”的state变量
    const [count, setCount] = useState(0);// count 的默认值是 0 

    return (
        <div>
        <p>You clicked {count} times</p>
        <button onClick={() => setCount(count + 1)}>
            Click me
        </button>
        </div>
    )
}
// 每次点击时 count + 1
```


### useEffect

替代之前的生命周期，默认每次在视图更新时执行。

``` js
useEffect(()=>{
    document.title = `You clicked ${count} times`;
})
// 相当于 组件挂载和组件更新时的生命周期都会触发它的更新


useEffect(()=>{
    document.title = `You clicked ${count} times`;
}, [count])
// 仅在count更新时，触发一次。
```


