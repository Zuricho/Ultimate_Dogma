# Linux Tips

## tar

[linux下解压命令大全](https://www.cnblogs.com/eoiioe/archive/2008/09/20/1294681.html)

.tar

解包：tar xvf FileName.tar

打包：tar cvf FileName.tar DirName

（注：tar是打包，不是压缩！）

———————————————

.gz

解压1：gunzip FileName.gz

解压2：gzip -d FileName.gz

压缩：gzip FileName


.tar.gz 和 .tgz

解压：tar zxvf FileName.tar.gz

压缩：tar zcvf FileName.tar.gz DirName

———————————————

.bz2

解压1：bzip2 -d FileName.bz2

解压2：bunzip2 FileName.bz2

压缩： bzip2 -z FileName

.tar.bz2

解压：tar jxvf FileName.tar.bz2

压缩：tar jcvf FileName.tar.bz2 DirName

———————————————

.bz

解压1：bzip2 -d FileName.bz

解压2：bunzip2 FileName.bz

压缩：未知

.tar.bz

解压：tar jxvf FileName.tar.bz

压缩：未知

———————————————

.Z

解压：uncompress FileName.Z

压缩：compress FileName

.tar.Z

解压：tar Zxvf FileName.tar.Z

压缩：tar Zcvf FileName.tar.Z DirName

———————————————

.zip

解压：unzip FileName.zip

压缩：zip FileName.zip DirName

———————————————

.rar

解压：rar x FileName.rar

压缩：rar a FileName.rar DirName

———————————————

gzip 命令

减少文件大小有两个明显的好处，一是可以减少存储空间，二是通过网络传输文件时，可以减少传输的时间。gzip 是在 Linux 系统中经常使用的一个对文件进行压缩和解压缩的命令，既方便又好用。

语法：gzip [选项] 压缩（解压缩）的文件名该命令的各选项含义如下：

-c 将输出写到标准输出上，并保留原有文件。-d 将压缩文件解压。-l 对每个压缩文件，显示下列字段：   压缩文件的大小；未压缩文件的大小；压缩比；未压缩文件的名字-r 递归式地查找指定目录并压缩其中的所有文件或者是解压缩。-t 测试，检查压缩文件是否完整。-v 对每一个压缩和解压的文件，显示文件名和压缩比。-num 用指定的数字 num 调整压缩的速度，-1 或 --fast 表示最快压缩方法（低压缩比），-9 或--best表示最慢压缩方法（高压缩比）。系统缺省值为 6。指令实例：

gzip *% 把当前目录下的每个文件压缩成 .gz 文件。gzip -dv * 把当前目录下每个压缩的文件解压，并列出详细的信息。gzip -l *% 详细显示例1中每个压缩的文件的信息，并不解压。gzip usr.tar% 压缩 tar 备份文件 usr.tar，此时压缩文件的扩展名为.tar.gz。

ls *.tar.gz | xargs -n1 tar xzvf 解压文件夹下全部的.tar.gz

加速gzip：pigz方法

https://leimao.github.io/blog/Parallel-Gzip-Pigz/

## 传输文件

rsync: https://www.jianshu.com/p/b862af872cbd

超算文档：https://docs.hpc.sjtu.edu.cn/transport/index.html?highlight=rsync



## 账户

https://blog.csdn.net/yychuyu/article/details/84190390



## Conda 镜像源

https://www.cnblogs.com/yirufeng/p/12242290.html



## Link使用方式

https://blog.51cto.com/u_14074978/2416657



## AMBER installation

https://blog.csdn.net/qq_33953882/article/details/113995531

https://blog.csdn.net/qq_36408389/article/details/88749207



## 其他

```bash
ls | wc -l  # 看文件夹下有多少个文件
du -sh # 查看文件夹大小
```

./run_alphafold.sh -d data -o output -p monomer_ptm -i input/GA98.fasta -t 1800-01-01 -f

./run_alphafold.sh -d data -o output -p monomer_ptm -i input/GA98.fasta -t 1800-01-01
