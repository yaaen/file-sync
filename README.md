# file-sync
数据同步工具<br/>

一.问题背景<br/>
经常碰到要同步数据的情况，而系统自带的复制功能又不能实现增量同步，每次都要做全量复制，发生异常情况后只能重头再来，非常麻烦，优其是对那种大文件的处理，更是耗时。<br/>
二.解決方案<br/>
1.计算源目录数据指纹<br/>
2.计算目标目录数据指纹<br/>
3.对比指纹数据，找出差异项，得到需要添加,删除或更新的文件列表，计算出需要更新的数据大小<br/>
4.挨个同步差异项，如果碰到大文件，则缓存其指纹数据到目标文件夹中，供下次同步数据时使用<br/>
三.数据指纹说明<br/>
数据指纹顾名思义，就是对某一文件夹或文件的唯一标识，其格式为:<br/>
文件相对路径＋:(分隔符)＋修改日期＋:+数据长度＋:+內容指纹<br/>
內容指纹是由多个内容块的md5组成<br/>
内容块就是对大文件进行分割处理，每次比较数据，最小的同步对象就是內容块，避免对整个文件做处理，也是实现增量同步的关健点<br/>

<br/>
<br/>

<br/>
使用说明：<br/>
1.安装Jre<br/>
2.下载fileSync.jar<br/>
3.运行命令：java -jar fileSync.jar 源目录 目标目录<br/>
<br/>
特性说明：<br/>
可增量同步，程序会检测源目录和目标目录已经同步好的数据，<br/>
对比之后继续同步未同步的数据<br/>

<br/>
<br/>
<img src="https://raw.githubusercontent.com/xxonehjh/file-sync/master/run.png"/><br/>