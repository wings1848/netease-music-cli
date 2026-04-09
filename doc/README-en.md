# NetEase Music Agent Skills

AI Agent skill package for NetEase Music based on `ncm-cli`.

Removes prompt injections related to user privacy data collection from the [original official skills](http://github.com/NetEase/skills), and significantly simplifies to save tokens.

## Prerequisites

All ncm-cli command invocations depend on the API Key. Please complete registration and apply at the [NetEase Music Open Platform](https://developer.music.163.com/st/developer/apply/account?type=INDIVIDUAL) first. [Registration Guide](https://developer.music.163.com/st/developer/document?docId=9504d35aa41a47c6ac9830b2dbf48f94)

## Skills Overview

| Skill | Description | Trigger Scenarios |
|-------|-------------|-------------------|
| netease-music-cli | Execute NetEase Music operations via ncm-cli | Play music, search songs, control playback, manage playback queue, view playback status, play playlists |
| netease-music-assistant | NetEase Music intelligent assistant, core capabilities: preference analysis, smart recommendations, scheduled push | Play songs, recommend playlists/music, scheduled music push, analyze music preferences |

---

## netease-music-cli

**Execute NetEase Music operations via ncm-cli.**

Core capabilities:

- Install and configure ncm-cli tool
- Search songs/playlists/albums
- Playlist management (create, add songs, view)
- Get daily recommendations
- View user information

### Environment Requirements: Node.js >= 18

- Installation: `npm install -g @music163/ncm-cli`
- After installation, run `ncm-cli configure` to complete configuration, and `ncm-cli login` to complete login authorization

### Command Quick Reference

```bash
# Get current command tree
ncm-cli commands

# Get help
ncm-cli help <command>
```

---

## netease-music-assistant

**NetEase Music intelligent assistant.**

Core capabilities:

- Preference analysis: Analyze user's liked songs playlist preference profile (24h cache)
- Smart recommendations: playlist/album/single song recommendations, supports deduplication
- Scheduled push: supports daily scheduled task for music push

### State Files

| File | Purpose |
|------|---------|
| `~/.config/ncm/ncm-preference.json` | User preference profile |
| `~/.config/ncm/ncm-history.json` | Recommended records (deduplication) |
| `~/.config/ncm/ncm-schedule.json` | Scheduled push configuration |