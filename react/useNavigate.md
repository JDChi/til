# useNavigate

useNavigate 是个 hook api，因此在定义的时候，需要在函数组件里声明，而不能在函数内，或是组件内。

但我遇到了个问题，如下：
```tsx
function Error404() {
    const nav = useNavigate();

    function handleClick(): void {
        nav('/');
    }

    return (
        <Result
            status={'404'}
            extra={
                <Button type='primary' onClick={handleClick}>
                    回首页
                </Button>
            }
        />
    );
}

export default Error404;
```
我已经正确的定义了，但却报了个错误：
> Uncaught TypeError: Cannot read properties of null (reading 'useContext')

后来发现是在路由那里把这个页面的语法写错了，在没有使用 useNavigate 的时候，即使用错误的写法，页面也能正常显示，但使用了 useNavigate 后，因为没有当做组件来使用，就获取不到组件的 context 了：
```tsx
const router = [
    // wrong
    {
        path: '/404',
        element: Error404()
    },
    // correct
    {
        path: '/404',
        element: <Error404 />
    }
]
```