# head 命令

查看文件头 n 行
```shell
➜  ~ head -n 2 hello.txt
kasldfjalsd
skldjflksjdl

➜  ~ head hello.txt | cat -n # 默认显示前 10 行，这里使用管道，输出行号
     1	kasldfjalsd
     2	skldjflksjdl
     3	lkfdjskldjfkls
     4	skldjflkasjdfkl
     5	;klasjdflkasjelf
     6	lsdjfio;ej
     7
     8	ljdksflksa
     9	aslkdjfklsaj
    10	aksdjfkjasldkf
```

查看文件头 n 个字符
```shell
➜  ~ head -c 10 hello.txt
kasldfjals%
```