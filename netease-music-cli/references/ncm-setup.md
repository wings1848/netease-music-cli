# ncm-cli 安装配置

## 安装

```bash
# 1. 检查ncm-cli，不存在则安装
ncm-cli --version || npm install -g @music163/ncm-cli

# 2. 检查mpv（播放需要），不存在则安装
mpv --version || python3 scripts/install_mpv.py
```

## 配置

```bash
# 设置 API Key（必须）
ncm-cli config set appId <AppId>
ncm-cli config set privateKey <PrivateKey>

# 询问设置播放器
ncm-cli config set player mpv # 内置播放器
# 或
ncm-cli config set player orpheus  # macOS 云音乐客户端
```

## 登录

```bash
ncm-cli login --check # 检查登录
ncm-cli login --background # 引导登录，将登录链接给到用户
```

## 常见问题

| 问题 | 解决 |
|------|------|
| `command not found` | 检查 npm 全局 bin 是否在 PATH：`npm bin -g` |
| `mpv not found` | 重新运行 `python3 scripts/install_mpv.py` |
| 登录超时 | 重新执行 `ncm-cli login --background` |

## 要求

- Node.js >= 18