---
name: netease-music-cli
description: 使用 ncm-cli 操作网易云音乐，当用户想播放音乐、搜索歌曲、控制播放（暂停、下一首、上一首、调音量）、管理播放队列、查看播放状态、播放歌单时触发。
---

# 网易云音乐 CLI（ncm-cli）

通过 `ncm-cli` 命令行工具操作网易云音乐。

- 仅命令失败时参考'reference/ncm-cli-setup.md'执行检查和安装
- 搜索结果两种为ID：加密 ID（32位hex）和明文 ID（数字）

## 命令速查

```bash
# 获取当前命令树
ncm-cli commands

# 获取帮助
ncm-cli help <command>
```

## 播放要点

- 播放用户歌单和红心歌单用加密 ID
- 播放异步：发送播放命令后等待几秒再用 `ncm-cli state` 查看状态

## 用户友好

返回资源给用户时使用明文ID生成链接，便于查看和收藏：
```
https://music.163.com/#/song?id=<明文ID>
https://music.163.com/#/playlist?id=<明文ID>
https://music.163.com/#/album?id=<明文ID>
https://music.163.com/#/artist?id=<明文ID>
```

- 请求超限停止时任务并告知用户