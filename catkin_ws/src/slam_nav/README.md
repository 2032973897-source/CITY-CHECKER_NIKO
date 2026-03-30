# slam_nav

> SLAM 建图与自主导航包

## 📦 包描述

实现机器人的 SLAM 建图、定位（amcl）和自主导航功能。

## 📁 目录结构

```
slam_nav/
├── launch/
│   ├── slam.launch          # SLAM 建图
│   ├── navigation.launch    # 自主导航
│   └── localization.launch  # 定位（amcl）
├── config/
│   ├── gmapping_params.yaml # GMapping 参数
│   ├── amcl_params.yaml     # AMCL 参数
│   └── move_base_params.yaml # move_base 参数
├── scripts/
│   ├── goal_sender.py        # 目标点发送
│   └── path_follower.py     # 路径跟随
├── msg/
│   └── PathPoint.msg         # 自定义路径消息
└── README.md
```

## 🚀 启动方式

```bash
# 1. SLAM 建图（需要在仿真环境中手动控制移动）
roslaunch slam_nav slam.launch

# 2. 保存地图
rosrun map_server map_saver -f ~/city-checker/maps/my_map

# 3. 自主导航（需要先有地图）
roslaunch slam_nav navigation.launch map_file:=/path/to/map.yaml
```

## 📐 技术方案

| 模块 | 算法 | 说明 |
|------|------|------|
| SLAM | gmapping | 2D 激光扫描建图 |
| 定位 | AMCL | 自适应蒙特卡洛定位 |
| 导航 | move_base | 全局路径规划 + 局部路径规划 |
| 规划 | navfn/Dijkstra | 全局最优路径 |

## 📝 TODO

- [ ] 配置 gmapping_params.yaml
- [ ] 配置 move_base_params.yaml
- [ ] 实现自主泊车逻辑
- [ ] 优化路径平滑算法
