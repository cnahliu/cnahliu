#Reactjs

##React Component

###定义方式

- ES5

```
const Video = React.createClass({
    getDefaultProps: function() {
        return {
            autoPlay: false,
            maxLoops: 10,
        };
    },
    propTypes: {
        autoPlay: React.PropTypes.bool.isRequired,
        maxLoops: React.PropTypes.number.isRequired,
        posterFrameSrc: React.PropTypes.string.isRequired,
        videoSrc: React.PropTypes.string.isRequired,
    },
    handleClick() {
        console.log(this); // React Component instance
    },
    render: function() {
        return (
            <div onClick={this.handleClick}>{this.props.autoPlay}</div>
        );
    },
});
export default Video
```
- ES6

```
class Video extends React.Component {
    constructor(props) {
        super(props);
        //绑定this
        this.handleClick = this.handleClick.bind(this);
        this.state = {

        };
    }
    static defaultProps = {
        autoPlay: false,
        maxLoops: 10,
    };  
    static propTypes = {
        autoPlay: React.PropTypes.bool.isRequired,
        maxLoops: React.PropTypes.number.isRequired,
        posterFrameSrc: React.PropTypes.string.isRequired,
        videoSrc: React.PropTypes.string.isRequired,
    };  
    handleClick() {
        console.log(this); // null;
    }
    render() {
        return (
            <div onClick={this.handleClick}>{this.props.autoPlay}></div>
        );
    } 
export default Video
```
- Stateless function

```
function Video({
    autoPlay,maxLoops,posterFrameSrc,videoSrc
}){
    function handleClick(){
        console.log(this); // null;        
    }
    return(
        <div onClick={handleClick}>${props.autoPlay}</div>
    )
}
Video.propTypes = {
    autoPlay:PropTypes.bool.isRequired, //添加 isRequired 表示不能为空
    maxLoops:PropTypes.number.isRequired,
    posterFrameSrc:PropTypes.string.isRequired,
    videoSrc:PropTypes.string.isRequired,
};
export default Video
```
##模板字符串

模板字符串提供了另一种做字符串组合的方法
```
const user = 'world';
console.log(`hello ${user}`);  // hello world
```
##注释
```
 /*
    多行注释
 */

 // 单行注释 
```
##Props

state 和 props 主要的区别在于 props 是不可变的，而 state 可以根据与用户交互来改变。这就是为什么有些容器组件需要定义 state 来更新和修改数据。 而子组件只能通过 props 来传递数据。
####使用方式

```
function App(props) {
  return <div>{props.name}</div>;
}
App.propTypes = {
  name: React.PropTypes.string.isRequired,
};
```

####Props类型

- PropTypes.bool
- PropTypes.func
- PropTypes.number
- PropTypes.element
- PropTypes.array
- PropTypes.object
- PropTypes.string
- PropTypes.any



