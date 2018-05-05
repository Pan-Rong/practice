# react-router切换界面

**1、在项目中遇到的，使用react-router切换界面的方法**

(1) 使用<Link>组件

(2) 使用`this.props.histroy.push("/XXX")`;

注：首先要在总路由里导入相关组件和添加相关route的path

**2、页面切换效果**

使用组件`react-transition-group`;
`
import { TransitionGroup, CSSTransition } from "react-transition-group";
`
在`route`组件中添加动画，然后再精确导航到相应的路径，例：

`
<Router>
        <Route render={({ location }) => (
            <Page>
                <Header></Header>
                {window.location.pathname.includes('index.html') && <Redirect to="/home" />}
                <TransitionGroup className="XXX">
                    <CSSTransition key={location.key} classNames="fade" timeout={1000}>
                        <Switch location={location}>
                            <Route exact path="/home" component={Home} />
                            <Route render={() => <div>Not Found</div>} />
                        </Switch>
                    </CSSTransition>
                </TransitionGroup>
            </Page>
        )}
        />
    </Router>
`
css部分：

`
// 进出场动画
// 飞入
.slide-in-appear {
    transform: translate3D(100%, 0, 0);
    transition: all 300ms linear;
    &.slide-in-appear-active {
        transform: translate3D(0, 0, 0);
    }
}

.slide-in-enter {
    transform: translate3D(100%, 0, 0);
    transition: all 300ms linear;
    &.slide-in-enter-active {
        transform: translate3D(0, 0, 0);
    }
} // 向左滑出
.slide-in-leave {
    position: absolute;
    left: 0;
    top: 0;
    opacity: 1;
    transform: translate3D(0, 0, 0);
    transition: all 300ms linear;
    &.slide-in-leave-active {
        opacity: 0.01;
        transform: translate3D(-100%, 0, 0);
    }
}

.fade-enter {
    opacity: 0;
    z-index: 1;
}

.fade-enter.fade-enter-active {
    opacity: 1;
    transition: opacity 250ms ease-in;
}
`
