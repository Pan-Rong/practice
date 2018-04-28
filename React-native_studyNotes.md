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
