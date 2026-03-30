# control

> 决策控制包 — 机器人大脑

## 📦 包描述

机器人的决策控制核心，包含状态机、任务调度、避障逻辑等。

## 📁 目录结构

```
control/
├── launch/
│   ├── control.launch       # 主控制器启动
│   └── state_machine.launch # 状态机启动
├── scripts/
│   ├── robot_brain.py        # 主控节点
│   ├── state_machine.py     # 状态机
│   ├── mission_planner.py   # 任务规划器
│   ├── obstacle_avoider.py  # 避障逻辑
│   ├── parking_controller.py # 泊车控制
│   └── cmd_vel_publisher.py # 速度发布
├── config/
│   ├── control_params.yaml  # 控制参数
│   ├── state_machine.yaml   # 状态转换配置
│   └── parking_params.yaml  # 泊车参数
├── msg/
│   ├── RobotState.msg       # 机器人状态
│   ├── Mission.msg          # 任务消息
│   └── ControlCmd.msg      # 控制命令
└── README.md
```

## 🚀 启动方式

```bash
# 启动主控制器
roslaunch control control.launch

# 启动状态机
roslaunch control state_machine.launch
```

## 🔄 状态机

```
        ┌─────────┐
        │  IDLE   │ ← 初始化
        └────┬────┘
             ↓
        ┌─────────┐
    ┌──→│ RUNNING │ ← 导航中
    │   └────┬────┘
    │        ↓
    │   ┌─────────┐     ┌──────────┐
    │   │ RED_LIGHT│ ── →│ WAITING  │
    │   └─────────┘     └──────────┘
    │        ↓
    │   ┌─────────┐
    └──←│PARKING  │ ← 到达目标点
        └─────────┘
```

| 状态 | 说明 |
|------|------|
| IDLE | 空闲待命 |
| RUNNING | 正常行驶 |
| RED_LIGHT | 红灯停 |
| WAITING | 等待（障碍物/临时） |
| PARKING | 泊车中 |
| EMERGENCY | 紧急停止 |

## 📡 ROS Topics

| 话题 | 类型 | 说明 |
|------|------|------|
| `/control/cmd_vel` | Twist | 速度控制命令 |
| `/control/robot_state` | RobotState | 当前状态 |
| `/control/mission` | Mission | 当前任务 |
| `/detections/detections` | Detections | 视觉检测结果 |

## 📝 TODO

- [ ] 实现基础状态机
- [ ] 红绿灯响应逻辑
- [ ] 避障逻辑实现
- [ ] 自主泊车算法
- [ ] 语音播报集成
