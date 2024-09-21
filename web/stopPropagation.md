# stopPropagation

在前端的页面里，如果父和子两个组件都实现了点击事件，此时如果对子组件进行点击，则会触发点击冒泡事件，即也会触发到父组件的点击事件。

一个处理就是在子组件里调用点击事件的 stopPropagation 方法，以拦截事件往上传递。

```jsx
import React, { useState } from 'react';

function App() {
  const [message, setMessage] = useState('');

  // 父元素的点击事件处理函数
  const handleParentClick = () => {
    setMessage('Parent clicked!');
  };

  // 子元素的点击事件处理函数
  const handleChildClick = (event) => {
    event.stopPropagation(); // 阻止事件冒泡到父元素
    setMessage('Child clicked!');
  };

  return (
    <div>
      <div 
        style={{ padding: '20px', backgroundColor: '#eee' }} 
        onClick={handleParentClick} // 父元素点击事件
      >
        Parent Div
        <div 
          style={{ padding: '20px', backgroundColor: '#ddd' }} 
          onClick={handleChildClick} // 子元素点击事件
        >
          Child Div
        </div>
      </div>
      <p>{message}</p>
    </div>
  );
}

export default App;

```