# inspect

python 里的 inspect 包，可以检查用于检查实时对象的各种信息，包括源代码、签名、类、方法等。

## getsource
以字符串的形式，返回源代码
```python
import inspect

def hello():
    print("hello world")

source_code = inspect.getsource(hello)

print(source_code)
```
