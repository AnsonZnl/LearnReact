# 学习 React 笔记

## 官方教程
- [React-官方教程](https://zh-hans.reactjs.org/)

## 基本知识

## JSX

通过React.createElement(`<div><div>`, root)将虚拟DOM转化为真实的DOM节点，并挂载到指定的节点上

而第一个参数必须有一个子节点，如果不提供可以使用React.Fragments或者`<>...</>`替代。

## 组件

- props<object>：组件内接受到的值，可以使用 `componentName.defaultProps = {value: 0}`，设置默认值，需规范props的类型和是否必要时，请使用`prop-type`
- state<object>：组件内的状态，可以使用`this.setState({value:0})`,改变（覆盖）state，并更新到DOM

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
// 相当于 组件挂载和组件更新(任何组件)时的生命周期都会触发它的更新


useEffect(()=>{
    document.title = `You clicked ${count} times`;
}, [])
// 只会在第一次加载时候触发一次

useEffect(()=>{
    document.title = `You clicked ${count} times`;
}, [count])
// 仅在 count 更新时，触发一次。
```
具体参考：[React函数式组件值之useEffect()](https://www.cnblogs.com/guanghe/p/14178482.html)

            
### useContext

      
           
## React API
### React.Fragment
可以使得组件在不创建额外DOM元素的情况下，让render()方法中返回多个元素            
### forwardRef
React.forwardRed 会创建一个React组件，这个组件可以接受 ref 属性转发到其组件树下的另一个组件中，在以下两个场景时比较有用
- 转发 refs 到 DOM 组件中
- 在高阶组件中转发 refs
