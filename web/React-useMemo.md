# React-useMemo

useMemo 这个 hook 是在 render 的过程中执行，一般用于缓存比较耗时的计算结果。

例如有一个列表，希望能在某个输入的过程中，进行一个实时的过滤。

在 React 里，如果不使用 useMemo，则这个过滤操作会在任何一次 Dom 变更的时候，被触发。

因此使用 useMemo 可以避免这个问题。

```jsx
import React, { useState, useMemo } from 'react';

function FilteredList() {
  const [query, setQuery] = useState('');
  
  // 假设我们有一个初始的未过滤的列表
  const itemList = [
    'Apple',
    'Banana',
    'Orange',
    'Mango',
    'Pineapple',
    'Grape',
    'Strawberry'
  ];

  // 使用 useMemo 缓存过滤后的列表，只有 query 改变时才重新过滤
  const filteredList = useMemo(() => {
    console.log('Filtering list...');
    return itemList.filter(item => 
      item.toLowerCase().includes(query.toLowerCase())
    );
  }, [query, itemList]);

  return (
    <div>
      <input 
        type="text"
        placeholder="Search..."
        value={query}
        onChange={(e) => setQuery(e.target.value)} // 更新输入框的状态
      />

      <ul>
        {filteredList.length > 0 ? (
          filteredList.map((item, index) => <li key={index}>{item}</li>)
        ) : (
          <li>No items found</li>
        )}
      </ul>
    </div>
  );
}

export default FilteredList;

```