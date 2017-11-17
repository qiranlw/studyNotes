# 通过例子学习C语言

## 第一个例子

```c
//helloworld
#include <stdio.h>

int main(int argc, char const *argv[]) {
    printf("Hello World!\n");
    return 0;
}
```
上面代码就是在命令行中输出一行文字，内容为 `Hello World!` 并换号。<br>
现在只需要关注 `printf("Hello World!\n");` 这一行就行了。他的功能就是把 `Hello World!` 输出到控制台上并换行。<br>
引号内的内容可以随意替换。其中 `\n` 是用来实现换行功能的。<br>
其他内容暂时不需要关心，暂时认为是一个标准模板就行了。

## 第二个例子

```C
#include <stdio.h>

int main(int argc, char const *argv[]) {
    int i = 158;
    int j = 23;
    printf("i + j = %d\n", i+j);
    printf("i - j = %d\n", i-j);
    printf("i * j = %d\n", i*j);
    printf("i / j = %d\n", i/j);
    printf("i % j = %d\n", i%j);
    return 0;
}
```
上面代码用于实现计算两个数加、减、乘、除和取余的值。
