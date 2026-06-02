# file_transfer — 文件网络传输

## 定位

收录跨网络传输文件的工具，涵盖 FTP/SFTP 客户端、下载管理器、BT 客户端、远程同步与网盘管理。

## 子分类目录结构

```
file_transfer/
├── ftp/                      # FTP/SFTP 客户端
│   ├── filezilla.md
│   ├── winscp.md
│   └── cyberduck.md
├── dl_mgr/                   # 下载管理器
│   ├── aria2.md
│   ├── motrix.md
│   ├── internet_download_manager.md
│   └── xdown.md
├── torrent/                  # BT 客户端
│   ├── qbittorrent.md
│   └── transmission.md
├── remote_sync/              # 远程同步传输
│   ├── scp_rsync.md
│   ├── syncthing.md
│   └── rclone.md
└── cloud_disk/               # 网盘挂载与管理
    ├── alist.md
    └── rclone_gui.md
```

## 编写要点

- 标注支持的协议（FTP/SFTP/WebDAV/S3 等）
- 注意区分命令行工具与 GUI 工具
- 说明传输速度、断点续传支持情况
