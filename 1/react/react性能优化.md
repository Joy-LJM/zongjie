#### react性能优化

答：1.虚拟化长列表（ “windowing” (开窗口) ），进行可视区域的渲染

 1.1.从react-virtualized引进 list   autosize



2 避免重新渲染 ==> 相当于react-precomponent 高性能组件

答：重写生命周期函数 `shouldComponentUpdate` 来优化性能 ，当组件的 props 和 state 改变时，React 通过比较新返回的元素 和 之前渲染的元素 来决定是否有必要更新DOM元素。当二者不相等时，则更新 DOM 元素

3.代码的拆分

第一种：import（将代码拆分引入到应用程序中的最好方法是通过动态 `import()` 语法。）

```
注意点：动态 import() 语法是ECMAScript（JavaScript）提案，目前不是语言标准的一部分
之前
import { add } from './math';

console.log(add(16, 26));

以后：
import("./math").then(math => {
  console.log(math.add(16, 26));
});

```

第二种`React.lazy`(组件 路由都可以使用懒加载)

```
之前
import OtherComponent from './OtherComponent';

之后  （还要用到suspense 组件，把fallback函数放在组件中）
const OtherComponent = React.lazy(() => import('./OtherComponent'));

function MyComponent() {
  return (
    <div>
      <Suspense fallback={<div>Loading...</div>}>
        <OtherComponent />
      </Suspense>
    </div>
  );
}
```

