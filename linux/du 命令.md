# du 命令
显示特定目录的磁盘使用情况

```shell
➜  $ du
24	./Ollama.app/Contents/_CodeSignature
240	./Ollama.app/Contents/MacOS
0	./Ollama.app/Contents/Resources/de.lproj
```

使用 -h 可以输出人类易读的格式
```shell
➜  $ du -h
 12K	./Ollama.app/Contents/_CodeSignature
120K	./Ollama.app/Contents/MacOS
  0B	./Ollama.app/Contents/Resources/de.lproj
```

使用 -s 输出汇总信息，可以结合 -h 使用
```shell
➜  $ du -h -s
 22G	.
```