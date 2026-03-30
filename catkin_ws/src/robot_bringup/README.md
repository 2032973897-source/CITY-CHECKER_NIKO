# robot_bringup

> 机器人启动入口包 — 一键启动所有功能

## 📦 包描述

机器人启动入口，包含所有模块的一键启动 launch 文件。

## 🚀 启动方式

```bash
# 启动完整仿真
roslaunch robot_bringup simulation.launch

# 启动导航
roslaunch robot_bringup navigation.launch

# 启动视觉检测
roslaunch robot_bringup vision.launch

# 启动语音播报
roslaunch robot_bringup voice.launch
```

## 📁 .launch 文件

| 文件 | 功能 |
|------|------|
| `simulation.launch` | 启动完整 Gazebo 仿真环境 |
| `navigation.launch` | 启动 SLAM + 导航 |
| `vision.launch` | 启动视觉检测节点 |
| `voice.launch` | 启动语音播报模块 |
| `bringup.launch` | 启动机器人基础驱动 |

## 🔧 参数配置

```yaml
# config/bringup.yaml
robot_name: "city_checker"
sim_mode: true
auto_start: true
```

## 📝 TODO

- [ ] 完成 simulation.launch
- [ ] 完成 navigation.launch
- [ ] 测试多机启动
