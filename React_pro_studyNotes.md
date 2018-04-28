# React projects study notes

**1.echarts 使用**
[官方参考1](http://echarts.baidu.com/tutorial.html#5%20%E5%88%86%E9%92%9F%E4%B8%8A%E6%89%8B%20ECharts)
[按需加载参考](https://github.com/hyy1115/react-echarts-modules)

折线图标实例(可放大缩小)
chart.js
```
import React, { component } from 'react';
import ReactDOM from 'react-dom';
import echarts from 'echarts/lib/echarts' //必须
import 'echarts/lib/component/tooltip'//引入提示框
import 'echarts/lib/component/axisPointer';//引入X轴等值线
import 'echarts/lib/component/dataZoom';//引入缩放区域
import 'echarts/lib/component/legend';//引入legend
import 'echarts/lib/component/grid';//引入网格
import 'echarts/lib/chart/line'; //引入折线图
// import 'echarts/lib/component/toolbox';//引入toolbox



class LineReact extends React.Component {
  
  constructor(props) {
    super(props)
    this.initPie = this.initPie.bind(this)
  }
  
  initPie() {
    const { option={} } = this.props //外部传入的data数据
    let myChart = echarts.init(this.ID) //初始化echarts
    
    //设置options
    myChart.setOption(option)
    window.onresize = function() {
      myChart.resize()
    }
  }
  
  componentDidMount() {
    this.initPie()
  }
  
  componentDidUpdate() {
    this.initPie()
  }
  
  render() {
    const { width="100%", height="350px" } = this.props
    return <div ref={ID => this.ID = ID} style={{width, height}}></div>
  }
}
export default LineReact;
```

```
import AccelerationTimeLine from './chart';
//以下是模拟数据
var base = +new Date(1968, 9, 3);
var oneDay = 24 * 3600 * 1000;
var date = [];

var data = [Math.random() * 300];
var data1 = [Math.random() * 400];
var data2 = [Math.random() * 500];

for (var i = 1; i < 1600; i++) {
    var now = new Date(base += oneDay);
    date.push([now.getFullYear(), now.getMonth() + 1, now.getDate()].join('/'));
    data.push(Math.round((Math.random() - 0.5) * 20 + data[i - 1]));
    data1.push(Math.round((Math.random() - 0.5) * 20 + data1[i - 1]));
    data2.push(Math.round((Math.random() - 0.5) * 20 + data2[i - 1]));
}

let lineOption = {
    tooltip: {
        trigger: 'axis',
        position: function (pt) {
            return [pt[0], '10%'];
        },
        axisPointer: {
            type: 'cross',
            label: {
                backgroundColor: '#6a7985'
            }
        }
    },
    legend: {
        data: ['X轴', 'Y轴', 'Z轴']
    },
    color: ['red', 'green', 'blue'],
    grid: {
        left: '3%',
        right: '4%',
        bottom: '3%',
        containLabel: true
    },
    xAxis: [
        {
            type: 'category',
            boundaryGap: false,
            data: date
        }
    ],
    yAxis: [
        {
            type: 'value',
            // boundaryGap: [0, '100%'] //设置图表的Y轴数值间距，注释掉后可Y轴可根据数据的大小随时调整数值
        }
    ],
    dataZoom: [
        {
            type: 'inside',
            start: 0,
            end: 10
        }, {
        //以下是设置图标的缩放按钮
            start: 0,
            end: 10,
            handleIcon: 'M10.7,11.9v-1.3H9.3v1.3c-4.9,0.3-8.8,4.4-8.8,9.4c0,5,3.9,9.1,8.8,9.4v1.3h1.3v-1.3c4.9-0.3,8.8-4.4,8.8-9.4C19.5,16.3,15.6,12.2,10.7,11.9z M13.3,24.4H6.7V23h6.6V24.4z M13.3,19.6H6.7v-1.4h6.6V19.6z',
            handleSize: '75%',
            handleStyle: {
                color: '#fff',
                shadowBlur: 3,
                shadowColor: 'rgba(0, 0, 0, 0.4)',
                shadowOffsetX: 2,
                shadowOffsetY: 2
            }
        }],
    series: [
        {
            name: 'X轴',
            type: 'line',
            smooth: true,
            symbol: 'none',
            sampling: 'average',
            data: data
        },
        {
            name: 'Y轴',
            type: 'line',
            smooth: true,
            symbol: 'none',
            sampling: 'average',
            data: data1
        },
        {
            name: 'Z轴',
            type: 'line',
            smooth: true,
            symbol: 'none',
            sampling: 'average',
            data: data2
        },
    ]
};

function App(){
 return(
  <AccelerationTimeLine option={lineOption} />
 )
}

```

## 附按需加载详情

### react15.6.1实现echarts模块化加载

**我们真的需要react-echarts插件吗？**

## NO

**注意：该项目仅作为源码学习使用，不能采取npm install --save react-echarts-modules的方式导入你的项目，因为这不是一个插件！！**

**在这里，我使用echarts提供的模块化加载方式，实现了几个react-echarts图表组件：[react-echarts图表在线渲染查看][1]**

**你可以打开控制台，观察每个图表组件的加载情况。**

#### 插件版本号

```json
  "echarts": "^3.6.2",
  "react": "^15.6.1",
  "react-dom": "^15.6.1"
```

#### 实现了哪些图表组件

1、饼图

2、柱状图

3、折线图

4、散点图

5、地图

6、雷达图

7、k线图


#### 我们不总是需要插件

实现这些echarts-react组件的目的，是告诉大家，react可以不需要引入第三方插件，使用echarts，不要惧怕react组件！

看过很多人说react难写，因为他们习惯了在jQuery开发模式下导入echarts、swiper、d3等插件。而突然切换到react中，就产生了不知所措的感觉。
如何在react中导入第三方插件，成为了他们心中的痛点，所以一些人就认为需要别人封装好的echarts-react插件或者其他react插件，才能使用，这种想法是错的。


#### echarts体积太大，使用模块化加载

以柱状图为例子，我们根据需要渲染的插件采取模块导入，不渲染的组件不导入，最大程度减小js。

```javascript
import echarts from 'echarts/lib/echarts' //必须
import 'echarts/lib/component/tooltip'
import 'echarts/lib/component/grid'
import 'echarts/lib/chart/bar'
```

#### 组件化开发的福音，react组件模块化加载

demo中采用单个echarts组件异步打包加载的模式，因为echarts组件普遍偏大，即使压缩也效果不明显，所以异步加载是最好的方式。

```javascript
import { pieOption, barOption, lineOption, scatterOption, mapOption, radarOption, candlestickOption } from './optionConfig/options'
const PieReact = asyncComponent(() => import(/* webpackChunkName: "PieReact" */'./EchartsDemo/PieReact'))  //饼图组件
const BarReact = asyncComponent(() => import(/* webpackChunkName: "BarReact" */'./EchartsDemo/BarReact')) //柱状图组件
const LineReact = asyncComponent(() => import(/* webpackChunkName: "LineReact" */'./EchartsDemo/LineReact'))  //折线图组件
const ScatterReact = asyncComponent(() => import(/* webpackChunkName: "ScatterReact" */'./EchartsDemo/ScatterReact'))  //散点图组件
const MapReact = asyncComponent(() => import(/* webpackChunkName: "MapReact" */'./EchartsDemo/MapReact'))  //地图组件
const RadarReact = asyncComponent(() => import(/* webpackChunkName: "RadarReact" */'./EchartsDemo/RadarReact')) //雷达图组件
const CandlestickReact = asyncComponent(() => import(/* webpackChunkName: "CandlestickReact" */'./EchartsDemo/CandlestickReact')) //k线图组件
```

### 启动项目

```javascript
npm install
```

```javascript
npm start
```

### 打包项目

```javascript
npm run build
```

### 实现方案介绍

1、每个图表单独封装成一个组件，通过参数传递数据，你会发现，图表内部代码几乎完全一样，只有import的类型不同。

2、异步加载是提高图表加载性能的最佳方式，不管是服务端还是客户端渲染。

3、在这些demo中，我认为对你来说最有价值的是react组件异步加载模式，很多人异步加载组件是通过拆分路由的方式，而非路由组件的异步加载，并不多人去尝试。但我想告诉你的是，
非路由组件的异步加载会将你的庞大的父组件拆分的更细，体积更小，加载的更加流畅。

### 附echarts各个模块导出路径

```javascript
/**
 * 导出echarts主模块
 */
module.exports = require('./lib/echarts');

// 各子模块路径
require('./lib/chart/line');
require('./lib/chart/bar');
require('./lib/chart/pie');
require('./lib/chart/scatter');
require('./lib/chart/radar');

require('./lib/chart/map');
require('./lib/chart/treemap');
require('./lib/chart/graph');
require('./lib/chart/gauge');
require('./lib/chart/funnel');
require('./lib/chart/parallel');
require('./lib/chart/sankey');
require('./lib/chart/boxplot');
require('./lib/chart/candlestick');
require('./lib/chart/effectScatter');
require('./lib/chart/lines');
require('./lib/chart/heatmap');
require('./lib/chart/pictorialBar');
require('./lib/chart/themeRiver');
require('./lib/chart/custom');

require('./lib/component/graphic');
require('./lib/component/grid');
require('./lib/component/legend');
require('./lib/component/tooltip');
require('./lib/component/axisPointer');
require('./lib/component/polar');
require('./lib/component/geo');
require('./lib/component/parallel');
require('./lib/component/singleAxis');
require('./lib/component/brush');
require('./lib/component/calendar');

require('./lib/component/title');

require('./lib/component/dataZoom');
require('./lib/component/visualMap');

require('./lib/component/markPoint');
require('./lib/component/markLine');
require('./lib/component/markArea');

require('./lib/component/timeline');
require('./lib/component/toolbox');

require('zrender/lib/vml/vml');

```

[1]: http://setcamp.tech
