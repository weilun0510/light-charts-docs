
## KLine
效果图
![avatar](./image/kline.png)

代码演示
```jsx
import React from 'react';
import { KLine } from 'light-charts';

const App = () => {
  // 获取数据，注意返回格式
  const getKLineData = (pageSize = 20, endTime = moment().format('MM-DD')) => {
    return new Promise((resolved, rejected) => {
      setTimeout(resolved, 500, new Array(pageSize).fill({}).map((item, index) => {
        return {
          id: Math.random().toString().slice(2, 7),
          date: moment(endTime).subtract(pageSize - index - 1, 'days').format('MM-DD'),
          heightPrice: +('10' + Math.random().toString().slice(2, 4)),
          lowPrice: +('7' + Math.random().toString().slice(2, 4)),
          openingPrice: +('8' + Math.random().toString().slice(2, 4)),
          closingPice: +('8' + Math.random().toString().slice(2, 4)),
        }
      }))
    })
  }

  return (
    <KLine
      style={{ width: '600px', height: '300px' }}
      loadData={getKLineData}
    />
  )
}
```

### api
| 属性 | 说明 | 类型 |  默认值  |
| ------ | ------ | ------ | ------ |
| option	| 配置项对象	| object	| {}
| loadData	| 必填。请求数据的方法，返回数据约定为{id: number, date: string, heightPrice: number, lowPrice: number, openingPrice: number, closingPrice: number}[]	| Promise | -
| style	| 元素宽高	| object	| { width: '600px', height: '300px' }

### option配置项
| 属性 | 说明 | 类型 |  默认值  |
| ------ | ------ | ------ | ------ |
| candleW	|蜡烛宽度	|number	|20
| showTips	|显示辅助线	|boolean	|true
| canDrag	|是否可拖拽	|boolean	|true
| canScroll	|是否可缩放	|boolean	|false
| pageSize	|一屏展示多少条	|number	|10
| maxShowSize	|一屏最多展示多少条	|number	|20
| yAxisSplitNumber	|y轴分段数量	|number	|4
| backgroundColor	|背景色	|string	|'DARK'
| xAxisItemMaxShowNumber	|x轴元素「文字和刻度」最大展示个数	|number	|5
| curveType	|曲线类型。可选为最高价 或 最低价 或 开盘价 或 收盘价	| string: heightPrice/lowPrice/openingPrice/closingPice | 'lowPrice'
| axisTick	|刻度相关。默认长度为5px，显示刻度	|object	|{ length: 5, show: true }
| grid	|grid对象	|object	| -

### grid配置项
| 属性 | 说明 | 类型 |  默认值  |
| ------ | ------ | ------ | ------ |
| left	|距离容器左侧的距离	|number	|50
| right	|距离容器右侧的距离	|number	|50
| top	|距离容器顶部的距离	|number	|50
| bottom	|距离容器底部的距离	|number	|50
| height	|grid组件的高度。想设置百分比的话，选择0-1，1表示100%	|string	|'auto'
| width	|grid组件的宽度。想设置百分比的话，选择0-1，1表示100%	|string	|'auto'


## Line
效果图
![avatar](./image/line.png)

代码演示
```jsx
import React, { useEffect, useState } from 'react';
import { KLine } from 'light-charts';

const App = () => {
  const [lineData, setLineData] = useState([]);

  /**
   *
   * @param {Object} param 获取折线图接口数据
   * @returns
   */
  const getLineMockData = function () {
    return new Promise((resolved, rejected) => {
      setTimeout(resolved, 500, new Array(7).fill({}).map((item, index) => {
        return {
          date: moment().subtract(7 - index - 1, 'days').format('MM-DD'),
          value: +('10' + Math.random().toString().slice(2, 3)),
        }
      }))
    })
  }

  useEffect(() => {
    getLineMockData().then((res) => {
      const data = res || [];
      setLineData(data)
    })
  }, [])

  return (
    <Line
      option={{
        yData: lineData.map(x => x.value),
        xData: lineData.map(x => x.date),
      }}
      style={{ width: '600px', height: '300px' }}
    />
  )
}
```

### api
| 属性 | 说明 | 类型 |  默认值  |
| ------ | ------ | ------ | ------ |
| yData	|纵坐标数据	|number[]	|[]
| xData	|横坐标数据	|string[]	|[]
| yAxisSplitNumber	|y轴分段数量	|number	|4
| backgroundColor	|背景色	|string	|'DARK'
| axisTick	|刻度相关。默认长度为5px，显示刻度	|object	|{ length: 5, show: true }
| grid	|grid对象	|object	| -


### grid配置项
| 属性 | 说明 | 类型 |  默认值  |
| ------ | ------ | ------ | ------ |
| left	|距离容器左侧的距离	|number	|50
| right	|距离容器右侧的距离	|number	|50
| top	|距离容器顶部的距离	|number	|50
| bottom	|距离容器底部的距离	|number	|50
| height	|grid组件的高度。想设置百分比的话，选择0-1，1表示100%	|string	|'auto'
| width	|grid组件的宽度。想设置百分比的话，选择0-1，1表示100%	|string	|'auto'


## Bar
效果图
![avatar](./image/bar.png)

代码演示
```jsx
import React, { useEffect, useState } from 'react';
import { Bar } from 'light-charts';

const App = () => {
  const [barData, setBarData] = useState([]);

  /**
   *
   * @param {Object} param 获取柱状图接口数据
   * @returns
   */
  const getLineMockData = function () {
    return new Promise((resolved, rejected) => {
      setTimeout(resolved, 500, new Array(7).fill({}).map((item, index) => {
        return {
          date: moment().subtract(7 - index - 1, 'days').format('MM-DD'),
          value: +('10' + Math.random().toString().slice(2, 3)),
        }
      }))
    })
  }

  useEffect(() => {
    getLineMockData().then((res) => {
      const data = res || [];
      setBarData(data)
    })
  }, [])

  return (
    <Bar
      option={{
        yData: barData.map(x => x.value),
        xData: barData.map(x => x.date),
      }}
      style={{ width: '600px', height: '300px' }}
    />
  )
}
```

### api
| 属性 | 说明 | 类型 |  默认值  |
| ------ | ------ | ------ | ------ |
| yData	|纵坐标数据	|number[]	|[]
| xData	|横坐标数据	|string[]	|[]
| yAxisSplitNumber	|y轴分段数量	|number	|4
| backgroundColor	|背景色	|string	|'DARK'
| axisTick	|刻度相关。默认长度为5px，显示刻度	|object	|{ length: 5, show: true }
| grid	|grid对象	|object	| -


### grid配置项
| 属性 | 说明 | 类型 |  默认值  |
| ------ | ------ | ------ | ------ |
| left	|距离容器左侧的距离	|number	|50
| right	|距离容器右侧的距离	|number	|50
| top	|距离容器顶部的距离	|number	|50
| bottom	|距离容器底部的距离	|number	|50
| height	|grid组件的高度。想设置百分比的话，选择0-1，1表示100%	|string	|'auto'
| width	|grid组件的宽度。想设置百分比的话，选择0-1，1表示100%	|string	|'auto'