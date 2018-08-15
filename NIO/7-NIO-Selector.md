# Selector
* 能够检测一到多个通道
* 能够知晓通道是否为 诸如读写事件做好准备的 组件

这样，一个单独的线程可以管理多个channel，从而管理多个网络连接。


不能将FileChannel与Selector一起使用，因为FileChannel不能切换到非阻塞模式。而套接字通道都可以。