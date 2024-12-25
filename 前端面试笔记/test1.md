# redux与antd

## 一、redux与antd简介
- **redux**：是一个可以用在react上的全局状态管理工具。
- **antd**：是蚂蚁金服开发的一套ui框架。

## 二、使用antd快速搭建页面
### （一）安装antd
- 使用命令`npm i antd --save`进行安装。

### （二）测试安装是否成功
1. 新建`list.js`文件
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
3. 在浏览器手动输入`list`地址查看效果
   - 如果安装成功，会看到一个蓝色的按钮（初次加载会稍微慢点）。

### （三）案例制作
1. 在`assets`文件夹中新建`css`文件夹用于储存不同组件的样式文件
   - 新建`list.css`文件并导入到`list.js`中
     - 在`list.js`中导入相关组件和样式文件
       - `import React,{Component}from 'react'; import{ Button,Input,List}from 'antd";//导入需要使用的antd组件 import 'antd/dist/reset.css';//导入antd组件样式 import'../assets/css/1ist.css'//导入1ist组件的样式`
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
   - 在学习vue时知道，vue组件可通过`style`标签的`scoped`属性封闭样式，但外部无法修改，需通过`v-deep`实现修改。
   - 而在react中，可以直接找到组件中标签的类名来直接修改，也可以添加新的类名来修改。
2. `antd`的`List`组件的使用
   - `antd`组件的使用和`elementPlus`基本一模一样，对于已经学会使用`elementPlus`的人来说基本是直接就拿来用。
   - 注意：当前使用的`antd`是针对PC端的，如果要适配移动端可以使用`antd mobile`。

### （五）将`Input`组件制作成受控组件
1. 在`list`组件的`constructor`中设置`textval`用于储存`Input`的`value`的值
   - ```jsx
     constructor(props){
       super(props);
       this.state ={ arr:['zhangsan','1isi','wangwu'], textval:"'//设置textva1储存Input的value的值
       }
     }
     ```
2. 制作获取`Input`的`value`值的方法`getInputval`
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
### （一）安装redux
- 使用命令`npm i redux`进行安装。

### （二）新建`store`文件夹及相关文件
1. 新建`store`文件夹，然后新建两个`js`文件：`index.js`和`reducer.js`。
2. 先看`reducer.js`管理数据的文件
   - `reducer`文件负责两件事：
     - 声明默认状态
       - `const defaultState = {msg:"hello"}`
     - 导出一个修改状态的函数
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
- 两个文件的关系类似于数据与数据管理员的关系，`reducer.js`负责储存操作数据，`index.js`负责管理`reducer`的数据。

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
     import reducer from './reducer' //导入要在实例中引入使用的数据
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
       //使用dispatch方法必须要传入一个action对象，所以我们创建一个action对象
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

### （七）`subscribe`订阅方法
- 解决`Input`数据无法双向绑定更新和全局`state`更新但界面未更新的问题。
1. 在`list`组件中创建`viewChange`方法用于获取每次修改全局`state`修改之后的数据
   - ```jsx
     viewChange(){
       this.setState(store.getState())
     }
     ```
2. 从`store`中调用`subscribe`方法，当`redux`中的全局`state`发生变化的时候执行`viewChange`方法，让组件中的`state`进行实时更新，再通过`setState`方法实时渲染到界面上。
   - ```jsx
     constructor(props){
       super(props);
       this.state = {
      ...store.getState()
       }
       store.subscribe(this.viewChange.bind(this))
     }
     ```

### （八）实现全局`state`和页面数据同步更新
1. 修改`addItem`方法
   - ```jsx
     addItem(){
       let action = {
         type:"arr"
       }
       store.dispatch(action)
     }
     ```
   - 代码分析：
     - 新增数据已在`Input`输入过程同步到全局`state`中的`textVal`，这里不需要设置`value`。
2. 在`reducer.js`中修改导出方法的业务逻辑
   - ```jsx
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

### （九）制作删除功能
1. 在`list`的标签结构上添加删除按钮
   - ```jsx
     <List.Item>
       <span>{item3</span>
       <Button type="primary"danger>删除</Button>
     </List.Item>
     ```
2. 制作删除方法`delItem`
   - ```jsx
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
   - ```jsx
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

### （十）reducer函数写法优化
1. 使用`switch`语句优化`if - else if`判断
   - ```jsx
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
           state.arr.splice(action快照

## 为后期维护提供便利
### （一）把`type`值提取成公用部分
1. 在`store`文件夹内新建`actionTypes.js`
   - 注意文件名是固定的不能随便取。
   - 内容如下：
     - ```js
       export const TEXT_VAL = "textVal";
       export const ARR = "arr";
       export const DEL = "del";
       ```
   - 这里`action`的`type`在取名的时候都是大写，是一个约定熟成的规则。
2. 在需要调用的地方解构导入对应需要的`type`值，并替换原来`list`和`reducer`中的使用`type`。

### （二）把`action`与`dispatch`部分提取
1. 在`store`文件夹中新建`actionCreators.js`，把之前`list`组件中用于操作全局`state`的方法体提取出来
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
2. 在`list`中导入调用并传入对应的实参
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
1. 新建`react`项目操作
   - `src`文件夹下面只保留`App.js`和`index.js`，其他全部删掉。
   - 把`index.js`内部引入的已经被删除的文件导入和调用都删除掉，把严格模式的标签也删除掉。
   - 把`App.js`中的代码全部删除，替换成类式组件代码。
2. 安装原生`redux`并创建`store`
   - 新建`reducer.js`
     - 设置全局状态（全局数据）
       - ```js
         const defaultState = {
           num:20
         }
         ```
     - 导出`reducer`函数（操作全局数据的方法）
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
     - 导入相关内容创建`store`实例，并让`redux`开发工具捕获到实时的全局状态
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
               <p>{this.state.num3</p> <button onclick={this.toAdd.bind(this)}>按钮</button>
             </div>
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
1. 安装包
   - 使用命令`npm i react-redux`安装。
2. `Provider`提供器组件
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
     - `Provider`作为一个提供器组件，通过其`store`属性将全局数据提供给其所有的子组件，所以需要把`Provider`组件写在最外层。
3. `connect`连接器方法
   - 在需要使用全局状态的组件中导入`connect`方法。
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
   - 第二次执行时传入一个组件名作为参数，将打包的内容注入到组件中，使组件能使用全局`state`的数据。
   - 在`Page`组件中导入`connect`方法并进行相关操作：
     - 创建映射全局状态的函数`mapStateToProps`。
     - 导入并使用`connect`方法
       - ```js
         import React,{ Component } from 'react'
         import store from '../store'
         import{ connect}from 'react-redux';
         class Page1 extends Component{
           //把原来的constructor和viewChange直接可以删除掉了
           toAddO{
             let action={
               type:"toAdd"
             }
             store.dispatch(action)
           }
           render(){
             return(
               <div>
                 <!--connect注入的全局数据要从props中调用-->
                 <p>{this.props.num}</p>
                 <button onclick={this.toAdd.bind(this)}>按钮</button>
               </div>
             )
           }
         }
         export default connect (mapStateToProps) (Page1)
         ```
   - 注意事项：
     - 把`mapStateToProps`作为`connect`实参传入，`mapStateToProps`中`return`的对象会成为第二次执行时组件内部的`state`使用，但数据要从`props`里面调用。
     - 原因是`connect`方法注入的全局数据是通过`Provider`组件提供的，`Provider`作为顶层组件，是父组件向子组件传值的过程，所以数据从`props`中调用。
   - 再传入`dispatch`的映射函数`mapDispatchToProps`
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
       ```
     - 这样所有修改全局`state`的方法都会挂到`props`对象上面，所以在调用`toAdd`方法的时候需要从`props`中调用。
   - 相关组件渲染操作
     - ```js
       render(){
         return(
           <div>
             <p>{this.props.num3</p>
             <!--toAdd方法要从props中调用-->
             <button onclick={this.props.toAdd.bind(this)}>按钮
             </按钮>
           </div>
         )
       }
       ```
4. 补充内容
   - 当完成了上述操作之后，组件无需导入`store`，因为`Provider`组件已经将`store`提供给了通过`connect`方法返回并导出的组件中了。
   - 解释`mapStateToProps`和`mapDispatchToProps`获取参数的原因：
     - `Provider`将`store`作为组件属性传入并提供数据。
   - 备注：
     - `react-redux`只是对组件内操作全局`state`的写法进行了优化，对原本的`redux`中的`reducer`和`index`文件并没有影响。