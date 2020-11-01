####       													React 

**React**构建用户界面 **JavaScript**库，主要用于构建 **UI**界面， lnstagram,2013开源。

##### 特点:

1. 声明式设计
2. 高效灵活采用虚拟DOM，来实现DOM渲染，最大限度减少DOM操作。
3. 灵活，跟其他库灵活搭配使用。
4. JSX ,俗称JS里面写HTML,JavaScript 语法来扩展
5. 组件化，模块化代码容易复用，2016 年之前打啊性项目比较喜欢
6. 单项数据流，没有实现数据双向绑定， 数据==》 视图==》事件==》数据

#### 创建 项目

1. ​    通过scrip/src引入使用，仅用于学习调试

   ```js
   <script src="https://unpkg.com/react@16/umd/react.development.js" crossorigin></script>
     <script src="https://unpkg.com/react-dom@16/umd/react-dom.development.js" crossorigin></script>
   
     <!-- 加载我们的 React 组件。-->
     <script src="like_button.js"></script>
   ```

   2. ###### 通过react的脚手架，来创建项目进行开发部署

      - 先安装onde环境  

      - 安装React  cnpm i -g create-react-app   查看版本号   create-react-app -V

      - 安装脚手架项目 create-react-app (项目名自定义)

      - 进入 cd 项目

      - npm  start  启动项目
   
        

   ###### React  元素渲染
   
   ```js
    let app = <App/>;
    let root = document.getElementById('root');
    let h1 = <h1>Hellwoerld</h1>
  ReactDOM.render(h1,root);
   ```

   使用JSX的写法，可以创建JS元素对象

   注意: **JSX**元素对象或者组件对象，必须只有一个根元素(根节点)
   
   ```js
   function clock(){//声明一个函数
     let time = new Date().toLocaleTimeString()//声明一个时间转换时间格式
     let element = <h1>现在时间{time}</h1>//创建一个对象并且赋值
     let root = document.querySelector('#root')//渲染DOM
     ReactDOM.render(element,root)//  React  渲染DOM的方法
   }
   
clock()//调用此函数
   ```

   ###### 渲染DOM
   
   ```js
   function clock(){
       let time = new Date().toLocaleTimeString()//获取当前时间转换成数字形式
       let element = (//用括号()包起来这是一个节点  赋值 给  element
       <div>
           <h1>输出文字{time}</h1>    用单花括号的形式包起来输出你的变量业务逻辑
   		    <h2>这是副标题</h2>
           </div>)
    let root = document.querySelector('#root')//声明输出DOM操作变量
     ReactDOM.render(element,root)//通过这两种形式输出到页面 
   }
   clock()//调用
setInterval(clock,1000);//每过一秒增加一秒  计时器
   ```

   ###### 函数 props传值
   
   ```js
   function Clock(props){//函数传值 函数名 传参数props传值
    return(
    	  <div>
         <h1>现在时间{props.date.toLocaleTimeString()}</h1>//props传值对象时间格式
         <h2>这是副标题</h2>
       </div>
    	)
   }
   
   function run(){
     ReactDOM.render(//通过 ReactDOM.render导出到页面上
       <Clock date={new Date()}/>,//他是一个 对象必须首个字母大写 通过对象date
       document.querySelector('#root')//再导出到页面
     )
   }
   
   setInterval(run,1000)

   ```

   ###### React  JSX

   ###### 优点:
   
   - JSX运行更快，编译为JavaScript代码时进化
- 类型更安全，如果出错不能 编译及时编译，及时发现错误。
   - JSX编写模板更快简洁 

   ###### 注意:
   
-  JSX必须要有根节点
   - 正常的普通HTML元素需要小写，"如果大写会默认为组件"

   ##### JSX 表达式
   
   1. 由HTML元素 构成
   2. 中间如果需要插入变量用{}
   3. {}中间可以 使用表达式
   4. {}中间表达式可以使用JSX对象
5. 属性和html内容一样都是用{}插入内容
   6. 一个{}只能放一个表达式
   
   ```js
   import React from 'react';
   import ReactDOM from 'react-dom';
   import './index.css';//引入css样式
   
   let color = 'bgRed'//声明从./index.css样式引入 过来的文件 
   let logo = 'https://ss1.bdstatic.com/70cFvXSh_Q1YnxGkpoWK1HF6hhy/it/u=3592298666,409220333&fm=26&gp=0.jpg'//
   let element5 = (//声明代码块DOM节点
     <div  className={color}>   {}通过引入样式  图片 
     棕色  <img src={logo}/>
     </div> 
   )
   
   ReactDOM.render(//渲染到页面
     element5,//节点名字
     document.getElementById('root');
)
   ```

   ###### JSX_style  样式

   1.  Class style 中不可以多个class属性 `<div class='abc' class={'active'}>`错误表示

   2. style样式中如果存在多个单词，属性组合第二个单词开始首个字母大写,"遇到长单词必须驼峰命名，或者用 " "包起来  "
   
      ```js
      let exampleStyle = {//声明一个样式对象
           width:"200px",
        height:"200px",
        background:"skyblue",
        borderBottom:"4px  solid red",
        'background-size':"100% 100%",//  注意在这里面用双'' 或者 驼峰命名
          'background-image':'url()'
      }
      let element = (//声明这个变量名字  运行到 ReactDOM.render 挂载
        <div>
          <h1 style={exampleStyle}>helloworld</h1>//引入样式对象
        </div>
      )
      ReactDOM.render(
        element,
        document.getElementById('root')
   )
      ```

   3. 多个 类共存操作
   
      ```js
      let element3 = (
      	<div>
      	<h1 className={"abc" + classStr}>Hellowrold</h1>// 一个字符串 + classStr
      	</div>
      )
      let classStr2 = ['abc','redBge'].join(" ") //  拼接
      let element3 = (
      	<div>
          <h2 className={classStr2} style={exampleStyle}>wodewenti</h2>
          </div>
   )
      ```

   4.  ###### 注释

       必须要在{}里面书写  表达式，否则报错:{/*这里写注释*/}

   #### React 组件

   1. 函数式组件
   
      ```js
      function Childcom(){  				定义一个函数 声明函数名
          let title = <h2>我是一个副标题<h2>       定义一个渲染标题 渲染到 渲染的地方
          let weather = "下雨"                 定一个变量名字
          let isGo = weather == "下雨" ? "不出门":"出门"   声明一个变量结果weather是否等于他下雨或者不下雨 
          return(
          <div>
              <h1>函数式组件</h1>
              {title}   渲染
                 <div>
                     今天是否出门    
      					<span>{isGo}</span>   声明一个变量结果
                     </div>
              </div>
          )
      }
      
      ReactDOM.render(   渲染
      <Childcom/>  
          document.querySelector('#root')
   )
      ```

      
   
   2. 类组件

```js
class Helloworld extends React.Component{ 声明一个了组件变量名字 开头字母大写 导出
	render(){ 渲染
	return{返回到上级
	<div>
	<h1>类组件定义  Helloworld</h1>内容
	</div>
	}
	}
}

ReactDOM.render(reactdom渲染
<Helloworld/>,  插入类组件 开头字母大写
    document.querySelector('#root')渲染到页面
)

```

​      3.

```js
// 函数式组件
function Childcom(props){//通过 props传参的形式导出
  console.log(props)//
  let title = <h2>我是副标题</h2>
  let weather = "props.weather"//声明变量 = "参数.值条件"
  let isGo = weather == "下雨" ? "不出门":"出门"
  return(
    <div>
      <h1> 函数式组件  </h1>
      {title}
      <div>今天是否出门?
        <span> {isGo} </span>
      </div>
    </div>
  )
}

ReactDOM.render(
  <Childcom  weather="出太阳" />,//在插入根组件上 
  document.querySelector('#root')
)
```

###### 复合组件

```js
// 函数式组件
function Childcom(props){//通过函数名的方式传递给  class类 Helloworld
  console.log(props)
  let title = <h2>我是副标题</h2>
  let weather = "props.weather"
  let isGo = weather == "下雨" ? "不出门":"出门"
  return(
    <div>
      <h1> 函数式组件  </h1>
      {title}
      <div>今天是否出门?
        <span> {isGo} </span>
      </div>
    </div>
  )
}

ReactDOM.render(
  <Childcom  weather="出太阳" />,
  document.querySelector('#root')
)

class Helloworld extends React.Component{//在传递给DOM进行渲染  
  render(){
    return(
      <div>
        <h1> 类组件定义 helloworld </h1>
        <Childcom />   //传递给他   他里面可以传N个组件  但是  Helloworld只有一个传递ReactDOM.渲染到页面
      </div>
    )
  }
}

ReactDOM.render(
  <Helloworld/>,   //再通过class  
  document.querySelector('#root')
)
```

函数组件与类组件的区别在于，函数组件比较简单，一般用于静态没有交互事件内容组件页面。

类组件一般称为动态组件，用于事件交互数据增删改查操作。

复合组件:组件中又有其他的组件，复合组件中既可以有类似组件和函数组件。

###### state

```js
class Clock extends React.Component{
  constructor(props){//传参
    super(props)//传参
      this.state ={
       time:new Date().toLocaleTimeString()//先初始声明一个变量
    }
    // console.log(this.state.time)
  }
  render(){
    // this.state.time = new Date().toLocaleTimeString();
    return(
      <div>
        <h1>
          当前时间: {this.state.time}
        </h1>
      </div>
    )
  }
  componentDidMount(){//声明周期函数过一段时间修改页面
    setInterval(()=>{
      this.setState({
        time:new Date().toLocaleTimeString()//  在函数声明周期 调用  
      })
    },1000)
  }
}

ReactDOM.render(
  <Clock />,
  document.querySelector('#root')
)


```

###### 选项卡切换

```js
class Tab extends React.Component{
  constructor(props){
    super(props)
    this.state = {
      c1:"",
      c2:""
    }
   this.clickEvent = this.clickEvent.bind(this)
  }

  clickEvent(e){
    console.log('clickEvent')
    console.log(e.target)
    let index = e.target.dataset.index;
    if(index=='1'){
      this.setState({
        c1:"content active",
        c2:""})
    }else{
      this.setState({
        c1:"",
        c2:"content active"})
    }
  }

  render(){
    return(
      <div>
        <button data-index="1"  onClick={this.clickEvent }>内容一</button>
        <button data-index="2" onClick={this.clickEvent }>内容二</button>
         <div className={this.state.c1}>一 </div>
         <div className={this.state.c2}>二 </div>
      </div>
    )
  }
}
```

###### React  父子组件传递

1. props 传递给子组件数据，单项流不能子传父
2. props传值可以 是 任意类型 字符串 数字

Props 可以设置默认值

**HelloMessage.defaultProps = { name:"老陈"， msg:"he" }**  属性.属性名 = {内置元素}

父元素中使用state去控制子元素props的从而达到父元素 数据传递给子元素

```js
class ParentCom extends React.Component{//通过calss 类函数组件的形式惊醒到处
  constructor(props){传参
    super(props)接受
    this.state = {设置属性状态
      isActive:true
    }
    this.changeShow = this.changeShow.bind(this)
  }
render(){//view视图数据
    return(
      <div>
        <button onClick={this.changeShow}>控制子元素显示</button>点击事件到当前状态的
        <ChildCom isActive = {this.state.isActive} /> 当前状态 
      </div>
    )
}
changeShow(){
  this.setState({
    isActive:!this.state.isActive
  })
}
}

class ChildCom extends React.Component{
  constructor(props){
    super(props)
  }
  render(){
      let  strClass = null;
      // if(this.props.isActive){
      // strClass = 'active'
      // }else{
      //   strClass = ""
      // }
      strClass = this.props.isActive?"active":"";
      return(
        <div className={"content"+strClass}>
          <h1>我是子元素</h1>
        </div>
      )
  }
}

ReactDOM.render(
  <ParentCom />,
  document.querySelector("#root")
)
```

##### React 数据传递 : 子传父

```js

```

