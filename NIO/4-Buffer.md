# Buffer

capacity 容


limit 读状态：最大可读位置 写状态：最大容量即capacity

position 读状态：从0开始  写状态： 当前写的位置 从0开始 最大为capacity-1

flip() 从写模式切到读模式

mark() 标记一个特定位置

reset() 回到标记的位置

clear() 清楚 从读模式切到写模式

compact() 将所有未读的数据拷贝到Buffer起始处（类似于gc的compact） 从读模式切到写模式

