# redux与antd

## 一、redux与antd简介
- **redux**：是一个可以用在react上的全局状态管理。
- **antd**：是蚂蚁金服开发的一套ui框架。

## 二、使用antd快速搭建页面
### （一）安装包
- 使用命令`npm i antd --save`安装antd。

### （二）简单测试是否安装成功
1. 新建`list.js`
   - 在`list.js`中导入相关组件
     - `import React,[ Component]from'react'; import { Button }from 'antd'; import 'antd/dist/reset.css';`
   - 创建`list`组件并在`render`方法中返回一个包含`Button`的`div`
     - ```jsx
       export default class list extends Component{
         render(){
           return(
             <div>
               <Button type="primary">utton</Button>
             </div>
           )
         }
       }
       ```
2. 在`router`中设置`List`组件的跳转路由
   - 导入相关路由组件和`List`组件
     - `import{ BrowserRouter, Switch,Route } from 'react-router-dom'; import List from'../views/list';`
   - 创建`Routers`函数组件并设置`List`组件的路由
     - ```jsx
       const Routers=()=>{
         return(
           <BrowserRouter>
             <Switch>
               <Route path="/1ist" component={List}></Route>
             </switch>
           </BrowserRouter>
         )
       }
       export default Routers;
       ```
3. 在浏览器手动输入`list`地址查看效果，如果安装成功会看到一个蓝色的按钮（初次加载会稍微慢点）。

### （三）案例制作
1. 在`assets`文件夹中新建`css`文件夹用来储存不同组件的样式文件，新建`list.css`并导入到`list.js`中。
   - 在`list.js`中导入相关组件和样式文件
     - ```jsx
       import React,{Component}from 'react';
       import{ Button,Input,List}from 'antd";//导入需要使用的antd组件
       import 'antd/dist/reset.css';//导入antd组件样式
       import'../assets/css/1ist.css'//导入1ist组件的样式
       ```
   - 在`list`组件的`constructor`中准备需要被渲染的数据
     - ```jsx
       constructor(props){
         super(props); //准备需要被渲染的数据
         this.state={
           arr:['zhangsan','1isi','wangwu']
         }
       }
       ```
   - 在`render`方法中返回包含`Input`、`Button`和`List`组件的`div`，并设置相关属性和样式
     - ```jsx
       render(){
         return(
           <div className='box'>
             <div className="top">
               <Input placeho1der="请输入内容'></Input>
               <Button className='m-1' type="primary">添加
               </Button>
             </div>
             <div className="bottom">
               <List
                 bordered
                 dataSource={this.state.arr}
                 renderItem={item=>(
                   <List.Item>{item}</List.Item>
                 )}
               />
             </div>
           </div>
         )
       }
       ```
2. `list.css`样式设置
   - ```css
     .box{
       width:600px;
       margin:100px auto;
     }
     .top{
       display: flex;;
     }
     .m-l{
       margin-left:10px;
     }
     .bottom{
       margin-top:15px;
     }
     ```

### （四）代码分析
1. 在父组件中修改子组件的样式
   - 在react中可以直接找到组件中标签的类名来直接修改，也可以添加新的类名来修改，与vue中通过`style`标签的`scoped`属性和`v-deep`实现样式修改不同。
2. `antd`的`List`组件的使用
   - 和`elementPlus`基本一模一样，对于已经学会使用`elementPlus`的人来说基本是直接就拿来用。
   - 如果要适配移动端可以使用`antd mobile`。

### （五）将`Input`组件制作成受控组件
1. 在`list`组件的`constructor`中设置`textval`用于储存`Input`的`value`的值
   - ```jsx
     constructor(props){
       super(props);
       this.state ={ arr:['zhangsan','1isi','wangwu'], textval:"'//设置textva1储存Input的value的值
       }
     }
     ```
2. 制作获取`Input`的`value`值的方法`getInputval`，让其成为受控组件
   - ```jsx
     getInputval(event){
       this.setState({
         textval :event.target.value
       })
     }
     ```
3. 将每次`Input`输入的内容添加到`arr`数组的前面，从而实时渲染新值的列表项
   - ```jsx
     addItem(){
       this.state.arr.unshift(this.state.textval);
       this.setState({
         arr:this.state.arr,
         textval:"'//每次新增之清除之前输入的内容
       })
     }
     ```

## 三、redux全局状态管理
### （一）安装包
- 使用命令`npm i redux`安装redux。

### （二）新建`store`文件夹及相关文件
1. 新建`store`文件夹，然后新建两个`js`文件，`index.js`和`reducer.js`。
2. 先看`reducer.js`管理数据的文件
   - 声明默认状态并导出一个修改状态的函数
   - ```jsx
     //reducer文件只负责两件事
     //1､声明默认状态
     - 相关代码如下：
       - 声明`defaultState`
         - ```jsx
           const defaultState = {
             msg:"hello"
           }
     ```
       - 导出修改状态的函数
         - ```jsx
           export default (state = defaultState,action) => {
             return state
           }
           ```
3. `index.js`全局状态管理入口文件
   - 导入创建`store`实例的方法和要在实例中引入使用的数据，创建`store`实例并导出
   - ```jsx
     import {createStore} from "redux" //导入创建store实例的方法
     import reducer from './reducer' //导入要在实例中引入使用的数据
     const store = createStore(reducer); //创建store实例，然后引用
     reducer方法
     export default store //导出store实例
     ```

### （三）代码分析
- 两个文件的关系有点类似于数据与数据管理员的关系，`reducer.js`负责储存操作数据，`index.js`负责管理`reducer`的数据。

### （四）使用全局状态管理调用案例中的数据
1. 在`list`组件中从导入的`store`中使用`getState`方法来调出全局的状态在当前组件中使用
   - ```jsx
     import store from '../store'
     export default class list extends Component {
       constructor(props){
         super(props);
         this.state = store.getState()
       }
     }
     ```
2. 注意事项
   - 如果直接覆盖掉原组件中的`state`，可能会把组件自己的状态也覆盖掉，所以可以通过展开运算来获取全局状态
   - ```jsx
     this.state = {
     ...store.getState()
     }
     ```

### （五）redux-devtools调试工具
1. 安装插件
   - 在edge浏览器直接在插件扩展的商店里面搜索`redux-devtools`安装。
2. 在`store`的`index.js`中添加代码
   - ```jsx
     import {createStore} from "redux" //导入创建store实例的方法
     import reducer from './reducer' //导入要在实例中中引入使用的数据
     const store = 
       createStore(reducer,window.__REDUX_DEVTOOLS_EXTENSION__ &&
       window.__REDUX_DEVTOOLS_EXTENSION__()); //创建store实例，然后引用
     reducer方法
     export default store //导出store实例
     ```

### （六）修改数据的方法
1. `dispatch`派发方法
   - 在`getInputVal`方法中使用`dispatch`方法修改数据
   - ```jsx
     getInputVal(event){
       //使用dispatch方法必须要传入一个按一个action对象，所以我们创建一个action对象
       let action = {
         type:"textVal",
         value:event.target.value
       }
       store.dispatch(action)
     }
     ```
   - 代码分析
     - `action`对象中，有两个固定的属性分别是`type`和`value`。
     - `type`：表示本次修改的行为。
     - `value`：表示本次修改的实际值。然后把设置好的`action`传入`dispatch`方法的参数中这里的`action`会传入到`reducer.js`中导出的函数的`action`参数中。
2. 在`reducer.js`中修改导出方法的业务逻辑
   - ```jsx
     const defaultState = {
       arr:['zhangsan','lisi','wangwu'],
       textVal:''
     }
     export default (state = defaultState,action) => {
       if(action.type === "textVal"){
         state.textVal = action.value
       }
       return state
     }
     ```
3. `subscribe`订阅方法
   - 解决`Input`数据无法双向绑定更新和全局`state`更新但界面未更新的问题。
   - 相关介绍如下：
     - 本质是一个监听器，用于监听全局状态的变化，当全局状态发生变化的时候执行一个操作。

## 四、redux相关操作
### （一）实现全局state和页面数据同步更新
1. 在`list`组件中创建`viewChange`方法
   - ```js
     viewChange(){
       this.setState(store.getState())
     }
     ```
   - 代码分析：
     - 由于redux中的state更新但界面数据未更新，所以需要此方法获取最新state并双向绑定。
2. 在`list`组件的`constructor`中调用`subscribe`方法
   - ```js
     constructor(props){
       super(props);
       this.state = {
       ...store.getState()
       }
       store.subscribe(this.viewChange.bind(this))
     }
     ```
   - 代码分析：
     - `constructor`是挂载阶段生命周期函数，在`list`组件载入时执行`subscribe`方法监听`store`中的全局state。
     - 当`Input`输入数据触发`onChange`事件执行`getInputVal`方法，`getInputVal`方法修改全局state会触发`subscribe`方法执行`viewChange`方法，形成循环过程。
3. 修改`addItem`方法
   - ```js
     addItem(){
       let action = {
         type:"arr"
       }
       store.dispatch(action)
     }
     ```
   - 代码分析：
     - 新增数据已在`Input`输入过程同步到全局state中的`textVal`，这里不需要设置`value`。
4. 在`reducer.js`中修改导出方法的业务逻辑
   - ```js
     const defaultState = {
       arr:['zhangsan','lisi','wangwu'],
       textVal:''
     }
     export default (state = defaultState,action) => {
       if(action.type === "textVal"){
         state.textVal = action.value
       }else if(action.type === "arr"){
         state.arr.unshift(state.textVal)
         state.textVal = ""
       }
       return state
     }
     ```
### （二）制作删除功能
1. 在`list`的标签结构上添加删除按钮
   - ```jsx
     <List.Item>
       <span>{item3</span>
       <Button type="primary"danger>删除</Button>
     </List.Item>
     ```
2. 制作删除方法`delItem`
   - ```js
     delItem(index){
       let action = {
         type:"de1"
         value:index
       }
       store.dispatch(action)
     }
     ```
   - 代码分析：
     - 删除全局状态需使用`dispatch`方法，且传递索引给`reducer`。
3. 绑定`delItem`方法
   - ```jsx
     <List
       bordered
       datasource={this.state.arr}
       renderItem={(item,index)=>(
         <List.Item>
           <span>{item}</span>
           <Button onclick={this.delrtem.bind(this,index)}
           type="primary"danger>除</Button>
         </List.Item>
       )}
     1>
     ```
   - 代码分析：
     - 通过`antd`组件`List`的`renderItem`获取索引并绑定到`delItem`方法。
4. 在`reducer.js`中修改导出方法
   - ```js
     const defaultstate ={
       arr:['zhangsan','1isi","wangwu"],
       textval:"
     }
     export default (state = defaultstate,action)=>{
       if(action.type==="textval"){
       }else if(action.type==="arr"){
         state.textval = action.value
         state.arr.unshift(state.textva1)
       }else if(action.type==="de1"){
         state.textval ="
         state.arr.splice(action.value,1)
       }
       return state
     }
     ```
### （三）reducer函数写法优化
1. 使用`switch`语句优化`if - else if`判断
   - ```js
     const defaultstate={
       arr:['zhangsan','1isi','wangwu'],
       textval:"'
     }
     export default(state = defaultstate,action)=>{
       switch(action.type){
         case"textval":
           state.textval =action.value;
           break;
         case "arr":
           state.arr.unshift(state.textval);
           newState.textval="
           break;
         case "de1":
           state.arr.splice(action.value,1)
           break;
         default:
           break;
       }
       return state
     }
     ```
2. 避免数据类型导致的赋值深浅拷贝问题
   - ```js
     const defaultstate ={
       arr:['zhangsan','1isi','wangwu'],
       textval:"'
     }
     export default (state = defaultstate,action)=>{
       //对state做一个深拷贝，并且下面所有的state全部替换成newstate
       let newstate = JSON.parse(JSON.stringify(state))
       switch(action.type){
         case "textval":
           newState.textval = action.value;
           break;
         case "arr":
           newstate.arr.unshift(state.textval)
           newState.textval="
           break;
         case "de1"
           newState.arr.splice(action.value,1)
           break;
         default:
           break;
       }
       return newState
     }
     ```
### （四）为后期维护提供便利
1. 把`type`值提取成公用部分
   - 在`store`文件夹内新建`actionTypes.js`
   - ```js
     export const TEXT_VAL = "textVal";
     export const ARR = "arr";
     export const DEL = "del";
     ```
   - 在需要调用的地方解构导入对应需要的`type`值，并替换原来`list`和`reducer`中的使用`type`。
2. 把`action`与`dispatch`部分提取
   - 在`store`文件夹中新建`actionCreators.js`
   - ```js
     import store from './'
     export default (type,value) => {
       let action = {
         type,
         value
       }
       store.dispatch(action)
     }
     ```
   - 在`list`中导入调用并传入对应的实参
   - ```js
     import {TEXT_VAL,ARR,DEL} from '../store/actionTypes'
     import actionCreators from '../store/actionCreators';
     export default class list extends Component {
       getInputVal(event){
         actionCreators(TEXT_VAL,event.target.value)
       }
       addItem(){
         actionCreators(ARR)
       }
       delItem(index){
         actionCreators(DEL,index)
       }
     }
     ```

## 五、React-redux
### （一）原生redux实现简单累加过程
1. 新建react项目操作
   - `src`文件夹保留`App.js`和`index.js`，删除其他文件。
   - 对`index.js`和`App.js`进行相关清理和代码替换操作。
2. 安装原生redux并创建`store`
   - 新建`reducer.js`
     - 设置全局状态
       - ```js
         const defaultState = {
           num:20
         }
         ```
     - 导出`reducer`函数
       - ```js
         export default (state = defaultState,action) => {
           let newState = JSON.parse(JSON.stringify(state));
           switch (action.type) {
             case value:
               break;
             default:
               break;
           }
           return newState
         ```
   - 在`store`内新建`index.js`
     - 创建`store`实例并导出
       - ```js
         import { createstore } from "redux";
         import reducer from "./reducer";
         const store=
           createStore(reducer,window.REDUX_DEVTOOLS_EXTENSION_&&
           window.REDUX_DEVTOOLS_EXTENSION_(O)
         export default store
         ```
3. 创建`Page1.js`组件实现累加
   - 在`Page1`组件中：
     - `constructor`导入全局状态到`state`
       - ```js
         constructor(props){
           super(props);
           this.state = store.getstate();
         }
         ```
     - 制作修改全局状态的方法`toAdd`
       - ```js
         toAddO{
           //根据action的type值来决定reducer函数内部执行哪种操作修改全局状态
           let action={
             type:"todd"
           }
           //将action派发给全局状态
           store.dispatch(action)
         }
         ```
     - `render`方法返回相关元素
       - ```js
         render(){
           return(
             <div>
               <p>{这部分内容文档似乎不完整，可能是PDF扫描或提取问题，“{this.state.num3”可能是“{this.state.num}”，此处按可能正确的理解继续转换}
               <button onclick={this.toAdd.bind(this)}>按钮</button>
             </div>
           )
         }
         ```
   - 在`reducer.js`中修改`switch`判断为`toAdd`时，将全局状态中的`num`执行递增运算
       - ```js
         export default (state = defaultState,action) => {
           let newState = JSON.parse(JSON.stringify(state));
           switch (action.type) {
             case "toAdd":
               newState.num++;
               break;
           }
           return newState
         }
         ```

### （二）通过`subscribe`订阅实时变化
1. 在`Page1`组件中
   - `constructor`订阅`store`中的`num`变化
     - ```js
       constructor(props){
         super(props);
         this.state = store.getState();
         store.subscribe(this.viewChange.bind(this))
       }
       ```
   - `viewChange`方法实现双向绑定
     - ```js
       viewChange(){
         this.setState(store.getState())
       }
       ```

### （三）react-redux优化
1. `Provider`提供器组件
   - 在`index.js`入口文件中导入`Provider`作为顶层组件使用
     - ```js
       import App from './App';
       import { Provider } from 'react-redux';
       import store from './store';
       const root =
         ReactDOM.createRoot(document.getElementById('root'));
       root.render(
         <Provider store={store}>
           <App />
         </Provider>
       );
       ```
   - 代码分析：
     - `Provider`通过`store`属性给子组件提供数据，需写在最外层。
2. `connect`连接器方法
   - 在`Page`组件中导入`connect`方法
   - 第一次执行时传入两个回调函数：
     - 参数1：`state`的映射函数`mapStateToProps`
       - ```js
         const mapStateToProps=state=>{
           return{
             num:state.num
           }
         }
         ```
     - 参数2：`dispatch`的映射函数`mapDispatchToProps`
       - ```js
         const mapispatchToProps =dispatch=>{
           return{
             toAddO){
               let action={
                 type:"toAdd"
               }
               dispatch(action)
             }
           }
         }
         ```
   - 第二次执行时传入组件名`Page1`，将打包内容注入组件使其能使用全局数据。
   - 注意事项：
     - `mapStateToProps`作为`connect`实参传入，其`return`对象在第二次执行时作为组件内部`state`，数据从`props`调用。
     - 原因是`connect`注入数据由`Provider`提供，是父组件向子组件传值过程。
   - 相关组件渲染操作
     - ```js
       render(){
         return(
           <div>
             <p>{this.props.num3</p>
             <!--toAdd方法要从props中调用-->
             <button onclick={this.props.toAdd.bind(this)}>按钮
             </button>
           </div>
         )
       }
       ```
3. 补充内容
   - 完成上述操作后，组件无需导入`store`，`Provider`已提供。
   - 解释`mapStateToProps`和`mapDispatchToProps`获取参数原因：
     - `Provider`将`store`作为组件属性传入提供数据。
   - 备注：
     - `react-redux`只影响组件内操作全局`state`的写法，不影响`redux`的`reducer`和`index`文件。