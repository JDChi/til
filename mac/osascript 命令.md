# osascript

osascript 是 macOS 系统中的一个命令行工具，用于执行 AppleScript 和 JavaScript for Automation (JXA) 脚本。它可以通过命令行接口调用 macOS 的图形用户界面功能，允许用户通过脚本与操作系统和应用程序进行交互，比如显示通知、打开文件、控制应用程序等。

比如我可以直接在命令行里发送一个系统通知：
```shell
osascript -e 'display notification "这是一条通知" with title "通知标题"'
```

或者打开一个程序：
```shell
osascript -e 'tell application "Safari" to activate'
```

同样的，在一些语言程序里，也可以调用它。例如在 Go 里：
```go
package main

import (
	"fmt"
	"os/exec"
)

func main() {
	// 自定义通知标题和内容
	title := "系统通知"
	message := "这是通过 Go 发送的通知！"

	// 使用 osascript 调用 AppleScript 发送通知
	cmd := exec.Command("osascript", "-e", fmt.Sprintf(`display notification "%s" with title "%s"`, message, title))
	err := cmd.Run()

	if err != nil {
		fmt.Println("Error sending notification:", err)
	} else {
		fmt.Println("Notification sent successfully")
	}
}

```