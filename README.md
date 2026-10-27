# MPV 配置

配置参考以下资料，并按个人使用习惯精简调整：

- 大河李斯特视频工作室：[《看番教程48：草履虫也能学会的视频基础知识，MPV画质链路完全解析。缩放、去色带、抖动算法这些都是啥？》](https://www.bilibili.com/video/BV1pkdTBAE9k/)
- [平泽唯也能看懂的yomitan/Lapis/mpvacious/ShareX配置教程](https://dcnyv3xgibev.feishu.cn/wiki/Qa1HwnZJBiGyyLk4mO4cw4Nhn0d)

用于观影、弹幕和字幕制卡。

## 文件

- `mpv.conf`：画质、字幕、音量和截图。
- `input.conf`：自定义快捷键。
- `script-opts/`：插件设置。

## 插件

按下表安装插件及所需字体。

| 插件 | 用途 | 安装位置 |
| --- | --- | --- |
| [uosc](https://github.com/tomasklaen/uosc) | 播放界面、右键菜单 | 发行包解压到配置目录，保留脚本和字体资源 |
| [thumbfast](https://github.com/po5/thumbfast) | 悬停进度条预览缩略图 | `scripts/thumbfast.lua` |
| [input-event](https://github.com/natural-harmonia-gropius/input-event) | 右方向键短按跳转、长按加速 | `scripts/inputevent.lua` |
| [uosc_danmaku](https://github.com/Tony15246/uosc_danmaku) | 搜索和加载弹幕 | `scripts/uosc_danmaku/main.lua` 及完整目录 |
| [mpvacious 双语过滤版](https://github.com/HuangAntimony/mpvacious) | 复制日语字幕、制作 Anki 卡片 | `scripts/subs2srs/main.lua` 及完整目录 |

当前 input-event 使用 `#@click`、`#@press`、`#@release` 语法，更新脚本时需核对兼容性。

## 快捷键

以下在没有菜单接管按键时生效。`Shift` 组合键对应脚本中的大写字母。

| 按键 | 功能 |
| --- | --- |
| 左键 / `Space` | 暂停或继续 |
| 右键 | uosc 菜单 |
| `↑` / `↓` | 音量 ±5 |
| 滚轮 | 普通画面区域音量 ±1，控件上按控件功能执行 |
| `←` / `→` 短按 | 后退 / 前进 5 秒 |
| `→` 长按 | 临时 3 倍速，松开恢复原倍速和暂停状态 |
| `Ctrl+←` / `Ctrl+→` | 后退 / 前进 1 秒 |
| `Enter` / `Esc` | 全屏并播放 / 退出全屏并暂停 |
| `f` / `m` / `q` | 切换全屏 / 静音 / 退出并保存进度 |
| `[` / `]` / `Backspace` | 减速 / 加速 / 恢复正常速度 |
| `s` / `Shift+s` | 带字幕 / 不带字幕截图，保存位置由 `mpv.local.conf` 设置 |
| `Ctrl+d` / `j` | 搜索弹幕 / 开关弹幕 |
| `Shift+j` / `v` | 反向切换字幕轨 / 开关主字幕 |
| `Ctrl+c` / `Ctrl+Shift+c` | 复制主字幕 / 副字幕 |
| `Ctrl+t` | 开关字幕自动复制 |
| `Alt+m` / `Alt+d` | 切换或重置双语过滤 / 过滤调试面板 |
| `Shift+h` / `Shift+l` | 上一句 / 下一句字幕 |
| `Alt+h` / `Alt+l` | 上一句 / 下一句字幕并暂停 |
| `Ctrl+h` / `Ctrl+Shift+h` | 回到当前句开头 / 重播当前句后暂停 |
| `Ctrl+v` | 开关副字幕 |
| `a` / `Ctrl+n` | 制卡菜单 / 导出 Anki 笔记 |
| `Ctrl+b` / `Ctrl+m` | 更新选中笔记 / 最近添加的笔记，加 `Shift` 为覆盖更新 |

`j` 已用于弹幕开关；菜单打开后 `Esc`、`q` 等按键按菜单功能执行。mpv 默认按键见 [官方手册](https://mpv.io/manual/stable/#interactive-control)。

## Anki 制卡

安装 [Anki](https://apps.ankiweb.net/)、[AnkiConnect](https://ankiweb.net/shared/info/2055492159) 和 [FFmpeg](https://ffmpeg.org/download.html)，保持 Anki 运行，并将 FFmpeg 加入 `PATH`。

本配置使用 [Lapis 笔记模板](https://github.com/donkuri/lapis)。

播放带文本字幕的视频，按 `a` 打开菜单：`c` 选择当前句，或用 `s`、`e` 设置片段起止位置；`n` 导出，`r` 清除选择，`Esc` 关闭菜单。

## 本机设置

首次使用，将 `mpv.local.conf.example` 复制为 `mpv.local.conf`，设置截图路径并创建对应文件夹，重启 mpv 生效。
