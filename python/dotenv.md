# dotenv
在一些项目里，我们会把一些配置文件以系统变量的形式进行保存。但有时我们不想把这些配置作为系统级别，而是想作为项目级别。此时就可以用 dotenv 来处理。

```shell
pip install python-dotenv
```

在项目根目录创建 `.env` 文件，将相关变量写入该文件。

然后在项目里，进行加载，既可以用同样获取系统变量的方式来获取配置。

```py
# 导入
from dotenv import load_dotenv
# 加载
load_dotenv() 
# 获取
openai_host = os.environ.get("OPENAI_HOST")
```