#React Native 学习笔记

** 1.画线实例**

[参考1](https://www.jianshu.com/p/8e6544ee647f) 
[参考2](https://segmentfault.com/a/1190000006652340)
```
import { ART } from 'react-native';
const { Surface, Shape, Path } = ART;
const path = Path()
      .moveTo(30, 1)
      .lineTo(410, 1);
const path_v1 = Path()
      .moveTo(1, 10)
      .lineTo(1, 125);

function App(){
return(
<Surface width={380} height={2} style={{ position: 'absolute', top: 64 }}>
 {/* <Shape d={path} stroke="#aaa" strokeWidth={1} strokeDash={[10, 5]} /> //虚线*/}
   <Shape d={path} stroke="#eee" strokeWidth={1} />
</Surface>
)
}      

```

**2. Antd-mobile**
[参考1](https://mobile.ant.design/docs/react/introduce-cn)
[论坛1](https://segmentfault.com/t/antd-mobile)

**3.echarts绘制图表**
[参考1-官网](https://www.npmjs.com/package/native-echarts)
[参考2](https://blog.csdn.net/sinat_17775997/article/details/68936687)

基础实例：
```
import Echarts from 'native-echarts';
let option1 = {
            title: {
                text: 'ECharts demo'
             },
            tooltip: {},
            legend: {
                data: ['年度仪表统计数量/个']
            },
            xAxis: {
                name: '时间',
                data: ["2018", "2019", "2020", "2021", "2022", "2023"]
            },
            yAxis: {
                name: '数量(个)'
            },
            color: ['rgb(0,59,59)'],
            series: [{
                name: '年度仪表统计数量/个',
                type: 'bar',
                data: [5, 0, 0, 0, 0, 0]
            }]
        };
function App(){
return(
     <Echarts option={option1} height={350} width={370}  /> 
)
}
```
**4.react native storage** [参考文档](https://github.com/sunnylqm/react-native-storage/blob/master/README-CHN.md)

      这是一个本地持久存储的封装，可以同时支持react-native(AsyncStorage)和浏览器(localStorage)。ES6语法，promise异步读取，使用jest进行了完整的单元测试。
      
      
**5. React Native 页面跳转不更新解决方法：注册监听事件-DeviceEventEmitter**

问题：

      在react native 中，使用react-navigation 从A页面跳到B页面，在B页面里修改数据，同时影响了A页面，但是从B页面返回A页面时，页面不刷新。
      
解决方法：

      在A页面设置DeviceEventEmitter监听事件,组件卸载时要移除监听，如：
      
```
import { DeviceEventEmitter } from 'react-native';

export default class App extends Component {
      render(){
      return(
            ....
            )
      }
      componentDidMount() {
            //调用事件通知
            this.deEmitter = DeviceEventEmitter.addListener("changeList",()=>{
               //更新页面相关操作
               .....
            })
       }
       
        componentWillUnmount(){
        //在组件销毁的时候要将其移除  
            this.deEmitter.remove();  
        }
```

      在B页面，在返回A页面操作前，先触发监听事件，如：
      
```
import { DeviceEventEmitter } from 'react-native';

      ...
      DeviceEventEmitter.emit('changeList');
      //this.props.navigation.goBack();
      ...

```






