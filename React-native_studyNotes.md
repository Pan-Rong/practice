# React Native 学习笔记

**1.画线实例**

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
**4.react-native-charts-wrapper 图表**

[官方文档-JAVA](https://github.com/wuxudong/react-native-charts-wrapper/blob/master/README.md) | [官方文档JAVA-wiki](https://github.com/PhilJay/MPAndroidChart/wiki)

[参考文档1-JS](https://github.com/gaishimo/react-native-charts-wrapper-example/blob/master/line-chart.js)

[参考文档2-JS](https://github.com/gregkyt/rnchartsexample/blob/master/index.android.js)

> 另一种react native的图表，和Echarts的设置有所区别，示例如下

```
import React, { Component } from 'react';
import { View, StyleSheet, processColor } from 'react-native'
import { LineChart } from 'react-native-charts-wrapper'
class Home extends Component {
      render(){
            return(
            <View>
                  <LineChart
                    style={{ flex: 1 }}
                    data={{
                        dataSets: [
                            {
                              values: [
                                { y: 3.4 },
                                { y: 10.5 },
                                { y: 5.8 },
                                { y: 8.2 },
                                { y: 15.4 },
                                { y: 6.3 },
                                { y: 7.1 },
                                { y: 9.9 },
                                { y: 10.1 },
                                { y: 6.2 },
                                { y: 7.3 },
                              ],
                              //设置数值label
                              label: '',
                              config: {
                                //lineWidth: 1.5,
                                //drawCircles: false,
                                //drawCubic: false,
                                //highlightColor: processColor('red'),
                                //color: processColor('rgb(255, 150, 150)'),
                                // drawFilled: true,
                                //fillColor: processColor('red'),
                                //fillAlpha: 255,
                                //valueTextSize: 0,
                                //valueFormatter: "##.0",
                                //设置虚线
                               // dashedLine: {
                                //  lineLength: 20,
                                //  spaceLength: 0,
                                //},
                              }
                            },
                          ],
                    }}
                    xAxis={{
                        // fontFamily: "HelveticaNeue-Medium",
                        // fontWeight: "bold",
                        // fontStyle: "italic",
                        valueFormatter: [1,2,3,4,5,6,7,8,9,10,11],
                    }}
                    yAxis={{
                        left:{
                          //限值线
                          limitLines: [
                              {
                              limit: 9,
                              label: '上限_9',
                              lineColor: processColor('#0a4'),
                              lineWidth: 1,
                              dashedLine: {
                                  lineLength: 5,
                                  spaceLength: 5,
                                },
                              },
                              {
                                  limit: 7,
                                  label: '警戒线_7',
                                  lineColor: processColor('red'),
                                  lineWidth: 1,
                              },
                              {
                                  limit: 5,
                                  label: 'XX_5',
                                  lineColor: processColor('#a77'),
                                  lineWidth: 1,
                              },
                              {
                                  limit: 3,
                                  label: '下线_3',
                                  lineColor: processColor('blue'),
                                  lineWidth: 1,
                              }
                          ],
                          drawLimitLinesBehindData: true,
                      }
                    }}
                    marker={{
                      enabled: true,
                      digits: 1,//精确到几位小数
                      backgroundTint: processColor('teal'),
                      markerColor: processColor('#a44'),
                      textColor: processColor('white')
                    }}
                    chartDescription={{ text: '' }} animation={{ durationX: 100 }} />
                  />
            </View>
            )
      }
}

```

**5.react native storage** [参考文档](https://github.com/sunnylqm/react-native-storage/blob/master/README-CHN.md)

      这是一个本地持久存储的封装，可以同时支持react-native(AsyncStorage)和浏览器(localStorage)。ES6语法，promise异步读取，
      使用jest进行了完整的单元测试。
      

**6. React Native 页面跳转不更新解决方法：注册监听事件-DeviceEventEmitter**

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

**7. 安卓机硬件上的返回按钮事件(React-Native 安卓back键处理)**

[参考文档](http://bbs.reactnative.cn/topic/480/%E5%AE%89%E5%8D%93back%E9%94%AE%E7%9A%84%E5%A4%84%E7%90%86-%E5%9F%BA%E6%9C%AC-%E9%AB%98%E7%BA%A7%E7%AF%87)
[官方文档](https://reactnative.cn/docs/0.45/backhandler.html)

Android back键监听，主要是事件监听，已被`BackHandler`代替，监听设备上的后退按钮事件：

> Android：监听后退按钮事件。如果没有添加任何监听函数，或者所有的监听函数都返回false，则会执行默认行为，退出应用;
>         监听函数是按倒序的顺序执行（即后添加的函数先执行）。如果某一个函数返回true，则后续的函数都不会被调用。

> tvOS(即Apple TV机顶盒)：监听遥控器上的后退按钮事件（阻止应用退出的功能尚未实现）。

> iOS：尚无作用。

```
      //设置监听事件
      BackHandler.addEventListener('hardwareBackPress', this.onBackPressed);

      // 取消监听事件
      BackHandler.removeEventListener('hardwareBackPress', this.onBackPressed);
```

***注：*** 

> 同时有两个页面a和b(其中b页面后入栈)，监听Android的back键事件，
  
- 如果b页面中监听函数 return true的情况下，a页面就不会监听到back键事件了
  
- 如果b页面中监听函数 return false 或者没有返回值，a页面也能监听到back事件。



