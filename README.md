# EchoRef 视频资源

EchoRef 心脏超声参考工具（[heiqingyu/echo-ref](https://github.com/heiqingyu/echo-ref)）的配套视频托管仓库。

视频文件不放进主仓库，避免把仓库体积从 35 MB 撑到 135 MB；这里单独托管，通过 GitHub Pages 提供直链：

```
https://heiqingyu.github.io/echo-ref-media/videos/<文件名>.mp4
```

## 内容

### 飞利浦云课堂 · PISA 原理、误区及应用

2026-03-23 · 徐子特 · 35:34 · 原片 1080p / 692 MB（`live_broadcast/超声/云教室/`）。原片 **moov 在文件尾**（未 faststart），
微信小程序 `<video>` 组件无法起播（点击后在浏览器才能播），故转 720p + `+faststart`：

```
ffmpeg -i pisa.mp4 -vf scale=-2:720 -c:v libx264 -preset medium -tune stillimage \
       -crf 26 -maxrate 620k -bufsize 1240k -c:a aac -b:a 48k -ac 1 -movflags +faststart pisa-lect.mp4
```

成品 40 MB / 720p / 157 kbps，幻灯片文字与超声图仍清晰。原片备份在仓库外 `videos/_raw2/pisa.mp4`。

《心脏超声术语及标准切面》上下篇 —— GE 心课堂「心脏超声基础规范学习班」学习笔记，2021-07-25 发布于微信公众号「GE超声」。共 17 段，原片 1080p / 420 MB，转存为 720p / H.264 / AAC，合计约 101 MB。

| 文件 | 内容 |
|---|---|
| kt-01-mark.mp4 | 探头标记 |
| kt-02-windows.mp4 | 常用声窗（胸骨旁 / 心尖 / 剑突下 / 胸骨上窝） |
| kt-03-maneuvers.mp4 | 探头手法总览与扫查 Sweep |
| kt-04-rotate.mp4 | 旋转 Rotate |
| kt-05-slide.mp4 | 滑行 Slide |
| kt-06-rock.mp4 | 摆动 Rock |
| kt-07-angle.mp4 | 成角 Angle |
| kt-08-plax.mp4 | 胸骨旁左室长轴 PLAX |
| kt-09-rvot.mp4 | 右室流出道 RVOT |
| kt-10-psax.mp4 | 胸骨旁短轴 PSAX 系列 |
| kt-11-apical.mp4 | 心尖切面：窗口定位 |
| kt-12-rv-a4c.mp4 | 关注右室的心尖四腔心 RV-focused A4C |
| kt-13-5c-cs.mp4 | 心尖五腔心与冠状静脉窦 |
| kt-14-a2c.mp4 | 心尖二腔心 / 长轴 A2C · A3C |
| kt-15-pulvns.mp4 | 关注肺静脉的心尖切面 |
| kt-16-subcostal.mp4 | 剑突下切面 Subcostal |
| kt-17-ssn.mp4 | 胸骨上窝主动脉弓长轴 SSN |

## 说明

- 仅供个人学习使用，版权归原作者所有。未做二次分发，如需引用请前往公众号原文。
- 原始视频挂在公众号内，`mpvideo.qpic.cn` 的直链带签名防盗链（`auth_info` / `auth_key`），短时有效且外部请求一律 403，无法直接引用，故转存于此。
- 转码参数：`-vf scale=-2:720 -c:v libx264 -preset medium -crf 26 -maxrate 900k -c:a aac -b:a 48k -ac 1 -movflags +faststart`。
