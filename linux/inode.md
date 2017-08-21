# 一、inode是什么？

理解inode，要从文件储存说起。
文件储存在硬盘上，硬盘的最小存储单位叫做"扇区"（Sector）。每个扇区储存512字节（相当于0.5KB）。  

操作系统读取硬盘的时候，不会一个个扇区地读取，这样效率太低，而是一次性连续读取多个扇区，即一次性读取一个"块"（block）。  
这种由多个扇区组成的"块"，是文件存取的最小单位。"块"的大小，最常见的是4KB，即连续八个 sector组成一个 block。  
文件数据都储存在"块"中，那么很显然，我们还必须找到一个地方储存文件的元信息，  
比如文件的创建者、文件的创建日期、文件的大小等等。这种储存文件元信息的区域就叫做inode，中文译名为"索引节点"。  

# 二、inode的内容  
inode包含文件的元信息，具体来说有以下内容：  
　　* 文件的字节数  
　　* 文件拥有者的User ID  
　　* 文件的Group ID  
　　* 文件的读、写、执行权限  
　　* 文件的时间戳，共有三个：ctime指inode上一次变动的时间，mtime指文件内容上一次变动的时间，atime指文件上一次打开的时间。  
　　* 链接数，即有多少文件名指向这个inode  
　　* 文件数据block的位置  
  
# 三、inode的大小
inode也会消耗硬盘空间，所以硬盘格式化的时候，操作系统自动将硬盘分成两个区域。一个是数据区，存放文件数据；另一个是inode区（inode table），存放inode所包含的信息。
每个inode节点的大小，一般是128字节或256字节。inode节点的总数，在格式化时就给定，一般是每1KB或每2KB就设置一个inode。  
假定在一块1GB的硬盘中，每个inode节点的大小为128字节，每1KB就设置一个inode，那么inode table的大小就会达到128MB，占整块硬盘的12.8%。  
  
# 四、inode号码
每个inode都有一个号码，操作系统用inode号码来识别不同的文件。  

# 五、inode的特殊作用  
由于inode号码与文件名分离，这种机制导致了一些Unix/Linux系统特有的现象。  
　　1. 有时，文件名包含特殊字符，无法正常删除。这时，直接删除inode节点，就能起到删除文件的作用。  
　　2. 移动文件或重命名文件，只是改变文件名，不影响inode号码。  
　　3. 打开一个文件以后，系统就以inode号码来识别这个文件，不再考虑文件名。因此，通常来说，系统无法从inode号码得知文件名  
  
# 六 实际问题

在一台配置较低的Linux服务器（内存、硬盘比较小）的/data分区内创建文件时，系统提示磁盘空间不足，用df -h命令查看了一下磁盘使用情况，发现/data分区只使用了66%，还有12G的剩余空间，按理说不会出现这种问题。   
后来用
```
> df -i
```
查看了一下/data分区的索引节点(inode)，发现已经用满(IUsed=100%)，导致系统无法创建新目录和文件。   

# Document
http://www.cnblogs.com/itech/archive/2012/05/15/2502284.html