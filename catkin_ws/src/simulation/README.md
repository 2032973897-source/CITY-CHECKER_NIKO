# simulation

> Gazebo 仿真配置包

## 📦 包描述

Gazebo 仿真环境配置，包含地图、模型、场景设置。

## 📁 目录结构

```
simulation/
├── gazebo/
│   ├── worlds/
│   │   ├── city_checker.world      # 主世界文件
│   │   ├── training_track.world    # 训练赛道
│   │   └── final_track.world       # 决赛赛道
│   └── models/
│       ├── robot_vehicle/          # 机器人模型
│       ├── traffic_light/          # 红绿灯模型
│       ├── parking_spot/           # 停车位
│       └── obstacles/               # 障碍物
├── launch/
│   ├── empty_world.launch          # 空世界启动
│   ├── city_world.launch           # 城市场景启动
│   └── spawn_robot.launch          # 机器人出生
├── config/
│   ├── gazebo_params.yaml         # Gazebo 参数
│   └── camera_info.yaml           # 相机参数
├── scripts/
│   ├── reset_simulation.py         # 重置仿真
│   └── spawn_objects.py           # 动态生成物体
└── README.md
```

## 🚀 启动方式

```bash
# 启动空世界
roslaunch simulation empty_world.launch

# 启动城市场景
roslaunch simulation city_world.launch

# 启动并生成机器人
roslaunch simulation full_simulation.launch
```

## 🗺️ 世界文件说明

| 文件 | 说明 |
|------|------|
| `city_checker.world` | 区域赛赛道，包含初赛任务示意 |
| `training_track.world` | 训练用简化赛道 |
| `final_track.world` | 决赛赛道 |

## 📦 模型说明

| 模型 | 说明 |
|------|------|
| `robot_vehicle` | 机器人载体模型 |
| `traffic_light` | 可交互红绿灯 |
| `parking_spot` | 停车位标志 |
| `obstacles` | 临时障碍物 |

## 📝 TODO

- [ ] 完成城市场景搭建
- [ ] 配置红绿灯模型
- [ ] 标定传感器参数
- [ ] 优化渲染性能
