# MutationObserver

一个用于观察 Dom 状态的观察器。

```typescript
const targetNode = document.querySelector("#someElement");
const observerOptions = {
    childList: true, // 观察目标子节点的变化，是否有添加或者删除
    attributes: true, // 观察属性变动
    subtree: true, // 观察后代节点，默认为 false
};

const observer = new MutationObserver(callback);
observer.observe(targetNode, observerOptions);

function callback(mutationList, observer) {
    mutationList.forEach((mutation) => {
        switch (mutation.type) {
            case "childList":
                /* 从树上添加或移除一个或更多的子节点；参见 mutation.addedNodes 与
                   mutation.removedNodes */
                break;
            case "attributes":
                /* mutation.target 中某节点的一个属性值被更改；该属性名称在 mutation.attributeName 中，
                   该属性之前的值为 mutation.oldValue */
                break;
        }
    });
}
```

例如一个水印组件，在浏览器调试的时候，我们可以把它删除，使其失效。而我们不想让这种情况出现，就可以使用这个观察器，当水印组件发生变化的时候，给重新添加回去。

```typescript
const targetNode = document.getElementById('content') as HTMLDivElement;
        const observer = new MutationObserver(function (
            mutationsList,
            observer
        ) {
            mutationsList.forEach(m => {
                switch (m.type) {
                    case 'childList':
                        m.removedNodes.forEach(n => {
                            if (n instanceof Element) {
                                if (n.id == 'content-text') {
                                    // 做些操作
                                    console.log('remove content text node');
                                }
                            }
                        });
                }
            });
        });
        const config: MutationObserverInit = {
            attributes: true,
            childList: true,
            subtree: true
        };
        observer.observe(targetNode, config);
```

