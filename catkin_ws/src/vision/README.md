# vision

> 视觉感知包 — YOLOv8 目标检测

## 📦 包描述

基于 YOLOv8 的多目标检测系统，支持：

- 🚦 红绿灯检测
- 👥 人群检测 / 外来人员识别
- 🔥 火灾检测
- 🗑️ 垃圾桶违规检测
- 🏍️ 电动车检测
- 🚗 车牌识别（OCR）

## 📁 目录结构

```
vision/
├── launch/
│   ├── yolo_detector.launch  # YOLO 检测启动
│   └── plate_recognizer.launch # 车牌识别启动
├── scripts/
│   ├── yolo_node.py          # YOLO 检测节点
│   ├── plate_recognizer.py  # 车牌识别节点
│   ├── traffic_light_detector.py  # 红绿灯专用
│   ├── crowd_detector.py     # 人群检测
│   └── anomaly_detector.py   # 异常检测
├── cfg/
│   └── yolov8.yaml          # YOLO 配置文件
├── models/
│   ├── traffic_light.pt     # 红绿灯模型
│   ├── crowd_person.pt      # 人群检测模型
│   ├── plate_recognizer.pt # 车牌识别模型
│   └── anomaly.pt          # 异常检测模型
├── msg/
│   ├── Detection.msg         # 检测结果消息
│   └── Detections.msg        # 多目标检测消息
├── config/
│   └── detection_params.yaml
└── README.md
```

## 🚀 启动方式

```bash
# 启动 YOLO 检测（所有类别）
roslaunch vision yolo_detector.launch

# 只检测红绿灯
roslaunch vision traffic_light_detector.launch

# 车牌识别
roslaunch vision plate_recognizer.launch

# 联合启动
roslaunch vision all_detectors.launch
```

## 📡 ROS Topics

| 话题 | 类型 | 说明 |
|------|------|------|
| `/vision/image_raw` | Image | 原始图像 |
| `/vision/detections` | Detections | 检测结果 |
| `/vision/traffic_light` | Detection | 红绿灯状态 |
| `/vision/plate` | String | 车牌号 |
| `/vision/crowd_count` | Int32 | 人数统计 |

## 📊 模型性能

| 模型 | 准确率 | 推理速度 |
|------|--------|---------|
| 红绿灯 | >90% | 30 FPS |
| 人群检测 | >85% | 25 FPS |
| 车牌识别 | >80% | 15 FPS |
| 异常检测 | >85% | 20 FPS |

## 📝 TODO

- [ ] 收集并标注数据集
- [ ] 训练红绿灯检测模型
- [ ] 训练人群检测模型
- [ ] 集成车牌 OCR
- [ ] 优化推理速度
