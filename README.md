# 网易云音乐 Agent Skills

[English](./doc/README-en.md) | [日本語](./doc/README-jp.md)

基于 `ncm-cli` 的网易云音乐 AI Agent 技能包。

去除[原官方技能](http://github.com/NetEase/skills)中关于用户隐私数据收集的提示词注入，并大幅度进行精简以节省token

## 使用的前置条件

ncm-cli 的所有命令调用依赖 API
Key。请先前往[网易云音乐开放平台](https://developer.music.163.com/st/developer/apply/account?type=INDIVIDUAL)完成入驻并申请，[入驻指南](https://developer.music.163.com/st/developer/document?docId=9504d35aa41a47c6ac9830b2dbf48f94)

## 技能概览

| 技能                      | 说明           | 触发场景        |
|-------------------------|--------------|-------------|
| netease-music-cli | 通过 ncm-cli 执行网易云音乐操作 | 播放音乐、搜索歌曲、控制播放、管理播放队列、查看播放状态、播放歌单 |
| netease-music-assistant | 网易云音乐智能助手，核心能力：偏好分析、智能推荐、定时推送 | 播放歌曲、推荐歌单/音乐、定时推送音乐、分析音乐偏好 |

---

## netease-music-cli

**通过 ncm-cli 执行网易云音乐操作。**

核心能力：

- 安装和配置 ncm-cli 工具
- 搜索歌曲/歌单/专辑
- 歌单管理（创建、添加歌曲、查看）
- 获取每日推荐
- 查看用户信息

### 环境要求：Node.js >= 18

- 安装方式：`npm install -g @music163/ncm-cli`
- 安装后执行 `ncm-cli configure` 完成配置，执行 `ncm-cli login` 完成登录授权

### 命令速查

```bash
# 获取当前命令树
ncm-cli commands

# 获取帮助
ncm-cli help <command>
```

---

## netease-music-assistant

**网易云音乐智能助手。**

核心能力：

- 偏好分析：分析用户红心歌单偏好画像（24h缓存）
- 智能推荐：歌单/专辑/单曲推荐，支持去重
- 定时推送：支持每日定时任务推送音乐

### 状态文件

| 文件 | 用途 |
|------|------|
| `~/.config/ncm/ncm-preference.json` | 用户偏好画像 |
| `~/.config/ncm/ncm-history.json` | 已推荐记录（去重） |
| `~/.config/ncm/ncm-schedule.json` | 定时推送配置 |