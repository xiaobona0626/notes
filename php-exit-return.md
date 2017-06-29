
## PHP中exit,die,return的区别

* return是返回值
* die是遇到错误才停止
* exit是直接停止，并且不运行后续代码，exit()可以显示内容。
* return就是纯粹的返回值了，但是也不会运行后续代码
* exit（0）：正常运行程序并退出程序；
* exit（1）：非正常运行导致退出程序；

```
void exit ([ string $status ] )
```
```
void exit ( int $status )
```

中止脚本的执行。 尽管调用了 exit()， Shutdown函数 以及 object destructors 总是会被执行。

> $status
> 如果 $status 是一个字符串，在退出之前该函数会打印 status 。

> 如果 $status 是一个 integer，该值会作为退出状态码，并且不会被打印输出。 退出状态码应该在范围0至254，不应使用被PHP保留的退出状态码255。 状态码0用于成功中止程序。
