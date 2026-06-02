# 文件网络传输

---

## 1 分类简介

开发工作中经常需要在不同主机、服务器和云存储之间传输文件。无论是部署代码、备份数据还是下载资源，一套好用的网络传输工具能让文件搬运变得可靠可控。

!!! tip ""
    根据场景快速选择：
    - 管理远程服务器文件 → [FileZilla](ftp/filezilla.md) 或 [WinSCP](ftp/winscp.md)
    - 下载大文件 / 离线任务 → [IDM](dl_mgr/internet_download_manager.md) 或 [Motrix](dl_mgr/motrix.md)
    - 下载种子资源 → [qBittorrent](torrent/qbittorrent.md)
    - 多设备自动同步 → [Syncthing](remote_sync/syncthing.md)
    - 跨平台网盘挂载 → [Alist](cloud_disk/alist.md) 或 [Rclone](remote_sync/rclone.md)

---

## 2 为什么需要这些工具

| 场景 | 痛点 | 解决工具 |
|------|------|---------|
| 远程管理服务器文件 | 命令行 scp 不直观、不能批量 | FTP/SFTP 客户端图形化操作 |
| 下载大型安装包 / 资源 | 浏览器下载容易断、不支持多线程 | 下载管理器多线程加速 + 断点续传 |
| 下载 P2P 种子资源 | 系统没有内置 BT 客户端 | BT 客户端透明管理种子队列 |
| 多设备 / 服务器文件同步 | 手动 rsync 命令繁琐、难自动化 | 远程同步工具增量传输 + 计划任务 |
| 使用云盘 / NAS 存储 | 网页上传下载效率低、不支持挂载 | 网盘工具将云存储挂载为本地盘符 |

---

## 3 子分类速览

### 3.1 FTP/SFTP 客户端

通过 FTP / SFTP / SCP 协议连接远程服务器，像操作本地文件一样管理远程文件。

| 工具 | 一句话 |
|------|--------|
| FileZilla | 老牌开源 FTP 客户端，功能全面 |
| WinSCP | Windows 上的 SFTP 主力，支持脚本自动化 |
| Cyberduck | macOS 上最好用的 FTP 客户端，也支持云存储 |

> [进入 FTP/SFTP 客户端分类](ftp/index.md)

### 3.2 下载管理器

支持多线程下载和断点续传的下载加速工具，比浏览器直下快数倍。

| 工具 | 一句话 |
|------|--------|
| Aria2 | 命令行下载瑞士军刀，轻量无敌 |
| Motrix | Aria2 的图形壳，优雅且开源 |
| IDM | Windows 下最强大的下载器，浏览器捕获能力极强 |
| XDown | 国产轻量下载工具，支持各大网盘解析 |

> [进入下载管理器分类](dl_mgr/index.md)

### 3.3 BT 客户端

BitTorrent 协议的下载客户端，适合大文件分发。

| 工具 | 一句话 |
|------|--------|
| qBittorrent | 开源免费、无广告的 BT 客户端首选 |
| Transmission | 极简轻量、常用于 Linux 种子服务器 |

> [进入 BT 客户端分类](torrent/index.md)

### 3.4 远程同步

增量式文件同步方案，适合服务器部署、跨设备备份。

| 工具 | 一句话 |
|------|--------|
| SCP / Rsync | Linux 标配的远程复制和增量同步命令行工具 |
| Syncthing | P2P 私有文件同步，不需要中心服务器 |
| Rclone | 面向云存储的 rsync，支持 40+ 云盘后端 |

> [进入远程同步分类](remote_sync/index.md)

### 3.5 网盘工具

将网盘 / NAS 挂载为本地目录，像本地文件夹一样管理云文件。

| 工具 | 一句话 |
|------|--------|
| Alist | 统一聚合多种网盘后端，WebDAV 协议直连 |
| Rclone GUI | Rclone 的图形界面，降低记忆命令的成本 |

> [进入网盘工具分类](cloud_disk/index.md)

---

> [回到工具首页](../index.md)
