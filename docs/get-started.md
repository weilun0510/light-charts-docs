
```

 /'\_/`\
/\      \    ___   ____    ____
\ \ \__\ \  / __`\/\_ ,`\ /\_ ,`\
 \ \ \_/\ \/\ \L\ \/_/  /_\/_/  /_
  \ \_\\ \_\ \____/ /\____\ /\____\
   \/_/ \/_/\/___/  \/____/ \/____/


```

## Install

```bash
> yarn add light-charts
# or
> npm i light-charts
```

## 使用

直接导入要使用的图表即可

```jsx
import { Line } from 'light-charts';

const App = () => {
  return (
    <Line
      option={{
        yData: [109, 102, 100, 108],
        xData: ['03-07', '03-06', '03-05', '03-04'],
      }}
    />
  )
}
export default App;
```

### KLine
