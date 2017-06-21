# react 生命周期函数
[link](http://blog.csdn.net/mjzhang1993/article/details/53706714)

1. getDefaultProps
2. getInitialState
    - getDefaultProps,getInitialState(es5 写法，es6将其合并成为 constructor)
3. componentWillMount
4. render
5. componentDidMount

- key/ref 都是非 DOM 属性
    - render 方法成功调用 初始化渲染执行之后立刻调用一次，仅客户端有效（服务器端不会调用），在此阶段中，可以访问真实的DOM元素，如果想与其他框架集成，可以在此方法中进行
    - ···
        componentDidMount(){
           console.log(ReactDOM.findDOMNode(this.refs.a)); //输出真实的DOM节点
        }
      ···

1. componentWillReceiveProps
    - 在任意时刻，组件的props都可以通过父辈组件来更改，在组建接收到新的props的时候就会调用此方法，在初始化渲染的时候此方法不会被调用，在函数中调用this.setState()将不会引起第二次渲染
    ···
    componentWillReceiveProps(nextProps) {
        if (nextProps.checked !== undefined) {
          this.setState({
            checked : nextProps.checked
          })
        }
    }
    ···

2. shouldComponentUpdate
    - 在接收到新的props或者state，将要渲染之前调用，通过返回的true/false决定组件是否更新 
    如果返回 false ，那么render 将不会被执行，componentWillUpdate 和 componentDidUpdate 也不会被执行
    ···
    shouldComponentUpdate(nextProps, nextState) {
        if (nextProps.num === this.props.num && nextState.num === this.state.num) {
            return false;
        }
    }
    ···

3. componentWillUpdate

4. render

5. componentDidUpdate      