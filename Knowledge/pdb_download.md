# How to download PDB database

如何下载整个PDB数据库

## 基于PDB ID一个个下载

参考：https://www.rcsb.org/docs/programmatic-access/file-download-services#automated-download-of-data

可推荐的方案：用Python脚本一个个发起下载指令，PDB下载链接为：

```
https://files.rcsb.org/download/4hhb.pdb
```

前提：你知道你需要的蛋白质列表

## 全部下载整个PDB数据库

使用wwPDB的ftp site：https://www.wwpdb.org/ftp/pdb-ftp-sites

推荐wwPDB的主要原因是在于，你可以根据你所在的位置选择更适合的服务器，如国内可以考虑使用PDBj (Japan) 进而提升下载速度。

```bash
rsync -rlpt -v -z --delete ftp.pdbj.org::ftp_data/structures/divided/pdb/ ./pdb
```

总大小 37.2 GB, 占用空间 202 GB
