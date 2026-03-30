# voice

> 语音播报包 — TTS 语音合成

## 📦 包描述

机器人语音播报模块，支持任务播报、告警提示、交互响应。

## 📁 目录结构

```
voice/
├── launch/
│   └── voice.launch         # 启动文件
├── scripts/
│   ├── tts_node.py          # TTS 主节点
│   ├── audio_player.py      # 音频播放
│   └── voice_manager.py     # 语音管理
├── config/
│   └── voice_params.yaml    # 语音参数
├── msg/
│   └── VoiceMsg.msg         # 语音消息
├── sounds/                  # 音频文件
│   ├── alert.wav           # 告警音
│   ├── success.wav         # 成功提示
│   └── turn_left.wav       # 动作提示
└── README.md
```

## 🚀 启动方式

```bash
# 启动语音播报
roslaunch voice voice.launch

# 测试播报
rostopic pub /voice/text std_msgs/String "data: '前方红灯，请停车等待'"
```

## 📡 ROS Topics

| 话题 | 类型 | 说明 |
|------|------|------|
| `/voice/text` | String | 播报文本 |
| `/voice/play` | String | 播放音频文件 |
| `/voice/enable` | Bool | 开关控制 |

## 🔊 播报内容

| 场景 | 播报内容 |
|------|---------|
| 启动 | "机器人已启动，开始执行任务" |
| 红灯 | "前方红灯，停车等待" |
| 绿灯 | "绿灯亮起，开始行驶" |
| 障碍物 | "检测到障碍物，停车等待" |
| 泊车 | "到达目标区域，开始泊车" |
| 火灾 | "警告，检测到火情，请注意" |
| 任务完成 | "任务已完成" |

## 📝 TODO

- [ ] 集成 TTS 引擎
- [ ] 预制语音文件
- [ ] 多语言支持
- [ ] 音量控制
