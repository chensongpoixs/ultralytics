# YOLO11 Pose 实时视频分析完全指南

## 📺 RTSP实时流检测命令

### **基础命令**

```bash
yolo pose predict model=yolo11n-pose.pt source='rtsp://admin:hik@12345@192.168.9.164/streaming/channels/101'
```

---

## 🎯 命令参数详解

### **完整命令（推荐）**

```bash
yolo pose predict \
  model=yolo11n-pose.pt \
  source='rtsp://admin:hik@12345@192.168.9.164/streaming/channels/101' \
  conf=0.5 \
  iou=0.45 \
  device=0 \
  imgsz=640 \
  vid_stride=1 \
  line_width=2 \
  visualize=False \
  save=False \
  show=True \
  line_thickness=2 \
  font_size=0.5
```

---

## 📊 参数说明

| 参数               | 类型    | 默认值     | 说明           | 示例                                                    |
| ------------------ | ------- | ---------- | -------------- | ------------------------------------------------------- |
| **model**          | str     | yolo11n.pt | 使用的模型     | `yolo11n-pose.pt`, `yolo11s-pose.pt`, `yolo11m-pose.pt` |
| **source**         | str     | 0          | 输入源         | `rtsp://...`, `http://...`, `video.mp4`, `0`(摄像头)    |
| **conf**           | float   | 0.25       | 置信度阈值     | 0.5 (50%), 0.6 (60%), 0.7 (70%)                         |
| **iou**            | float   | 0.45       | NMS IoU阈值    | 0.4-0.6之间                                             |
| **device**         | int/str | 0          | GPU设备ID      | `0`, `1`, `2` 或 `cpu`                                  |
| **imgsz**          | int     | 640        | 推理图像大小   | 320, 416, 480, 640, 1280                                |
| **vid_stride**     | int     | 1          | 视频帧跳过     | 1(每帧), 2(隔帧), 5(每5帧)                              |
| **line_width**     | int     | 2          | 骨架线条宽度   | 1-5                                                     |
| **line_thickness** | int     | 2          | 关键点线条宽度 | 1-5                                                     |
| **font_size**      | float   | 0.5        | 文字大小       | 0.3-1.0                                                 |
| **show**           | bool    | False      | 实时显示       | `True` (显示), `False` (不显示)                         |
| **save**           | bool    | False      | 保存视频       | `True` (保存), `False` (不保存)                         |
| **visualize**      | bool    | False      | 可视化特征     | `True`, `False`                                         |
| **save_frames**    | bool    | False      | 保存帧         | `True`, `False`                                         |
| **save_txt**       | bool    | False      | 保存文本结果   | `True`, `False`                                         |
| **exist_ok**       | bool    | False      | 覆盖输出       | `True` (覆盖), `False` (新建)                           |
| **project**        | str     | runs       | 项目目录       | `runs/pose`                                             |
| **name**           | str     | predict    | 结果目录名     | `exp1`, `rtsp_stream_1`                                 |
| **half**           | bool    | False      | FP16推理       | `True` (更快，内存少), `False`                          |
| **verbose**        | bool    | True       | 详细输出       | `True` (输出详细), `False` (静默)                       |
| **augment**        | bool    | False      | 测试增强       | `True`, `False`                                         |
| **flip**           | bool    | False      | 图像翻转       | `True`, `False`                                         |

---

## 🚀 常用场景命令

### **1️⃣ 实时监控（最简单）**

```bash
yolo pose predict model=yolo11n-pose.pt source='rtsp://admin:hik@12345@192.168.9.164/streaming/channels/101' show=True
```

**特点**:

- ✅ 实时显示视频和检测结果
- ✅ 低延迟，快速反应
- ❌ 不保存视频

---

### **2️⃣ 实时监控 + 保存视频**

```bash
yolo pose predict \
  model=yolo11n-pose.pt \
  source='rtsp://admin:hik@12345@192.168.9.164/streaming/channels/101' \
  show=True \
  save=True \
  project=runs/pose \
  name=rtsp_stream_1 \
  vid_stride=1
```

**特点**:

- ✅ 实时显示 + 保存视频
- ✅ 所有帧都分析
- 📁 输出目录: `runs/pose/rtsp_stream_1/`

---

### **3️⃣ 高精度监控（提高准确率）**

```bash
yolo pose predict \
  model=yolo11m-pose.pt \
  source='rtsp://admin:hik@12345@192.168.9.164/streaming/channels/101' \
  imgsz=1280 \
  conf=0.6 \
  show=True \
  device=0
```

**特点**:

- ✅ 使用更大模型 (yolo11m)
- ✅ 更高分辨率 (1280)
- ✅ 更严格的置信度 (0.6)
- ⏱️ 处理速度较慢

---

### **4️⃣ 轻量级监控（更快）**

```bash
yolo pose predict \
  model=yolo11n-pose.pt \
  source='rtsp://admin:hik@12345@192.168.9.164/streaming/channels/101' \
  imgsz=416 \
  conf=0.5 \
  vid_stride=2 \
  show=True \
  half=True
```

**特点**:

- ✅ 更小的输入大小 (416)
- ✅ 隔帧处理 (vid_stride=2)
- ✅ FP16推理 (half=True)
- ⚡ 快速处理，适合低端GPU

---

### **5️⃣ 保存详细分析结果**

```bash
yolo pose predict \
  model=yolo11n-pose.pt \
  source='rtsp://admin:hik@12345@192.168.9.164/streaming/channels/101' \
  save=True \
  save_txt=True \
  save_frames=True \
  show=True \
  project=runs/pose \
  name=stream_analysis
```

**输出内容**:

- 📹 `*.mp4` - 标注后的视频
- 📄 `*.txt` - 关键点坐标数据
- 🖼️ `*.jpg` - 每一帧的图片
- 📊 `results.txt` - 统计结果

---

### **6️⃣ 多GPU并行处理**

```bash
yolo pose predict \
  model=yolo11n-pose.pt \
  source='rtsp://admin:hik@12345@192.168.9.164/streaming/channels/101' \
  device=0 \
  batch=4 \
  show=True
```

---

### **7️⃣ 无显示监控（服务器场景）**

```bash
yolo pose predict \
  model=yolo11n-pose.pt \
  source='rtsp://admin:hik@12345@192.168.9.164/streaming/channels/101' \
  save=True \
  show=False \
  verbose=True
```

**适用于**:

- 服务器/无显示屏的环境
- Docker容器
- 后台服务

---

### **8️⃣ CPU推理（无GPU）**

```bash
yolo pose predict \
  model=yolo11n-pose.pt \
  source='rtsp://admin:hik@12345@192.168.9.164/streaming/channels/101' \
  device=cpu \
  imgsz=416 \
  conf=0.5 \
  show=True
```

---

## 🎨 显示参数优化

### **改进可视化效果**

```bash
yolo pose predict \
  model=yolo11n-pose.pt \
  source='rtsp://admin:hik@12345@192.168.9.164/streaming/channels/101' \
  show=True \
  line_width=3 \
  line_thickness=3 \
  font_size=0.7 \
  conf=0.5
```

### **参数说明**:

- `line_width=3` - 骨架连接线更粗
- `line_thickness=3` - 关键点圆圈更明显
- `font_size=0.7` - 文字更大，更易读

---

## 📈 性能优化技巧

### **根据GPU内存选择**

**NVIDIA RTX 3060 (12GB)**:

```bash
yolo pose predict model=yolo11m-pose.pt source='rtsp://...' imgsz=640 batch=2
```

**NVIDIA RTX 2060 (6GB)**:

```bash
yolo pose predict model=yolo11n-pose.pt source='rtsp://...' imgsz=416 batch=1 half=True
```

**NVIDIA T4 (16GB)**:

```bash
yolo pose predict model=yolo11l-pose.pt source='rtsp://...' imgsz=1280 batch=4
```

### **模型大小对比**

| 模型             | 参数量 | 速度   | 精度       | 内存 |
| ---------------- | ------ | ------ | ---------- | ---- |
| **yolo11n-pose** | 2.7M   | ⚡⚡⚡ | ⭐⭐⭐     | 最低 |
| **yolo11s-pose** | 9.8M   | ⚡⚡   | ⭐⭐⭐⭐   | 中等 |
| **yolo11m-pose** | 20.1M  | ⚡     | ⭐⭐⭐⭐⭐ | 较高 |
| **yolo11l-pose** | 33.4M  | 慢     | ⭐⭐⭐⭐⭐ | 很高 |

---

## 🔌 RTSP连接参数

### **常见RTSP摄像头URL格式**

**海康威视 (Hikvision)**:

```
rtsp://username:password@192.168.1.100:554/Streaming/Channels/101
```

**大华 (Dahua)**:

```
rtsp://username:password@192.168.1.100:554/live
```

**Axis**:

```
rtsp://username:password@192.168.1.100:554/axis-media/media.amp?videocodec=h264
```

**通用格式**:

```
rtsp://[username:password@]ip:port/path
```

### **连接测试**:

```bash
# 使用ffmpeg测试RTSP连接
ffplay 'rtsp://admin:hik@12345@192.168.9.164/streaming/channels/101'
```

---

## 💾 输出目录结构

当使用 `save=True` 时，输出结构：

```
runs/
└── pose/
    └── rtsp_stream_1/
        ├── results.avi          # 检测结果视频
        ├── results.txt          # 统计摘要
        ├── keypoints.txt        # 关键点坐标
        └── frames/              # 每一帧（如果 save_frames=True）
            ├── 0000000.jpg
            ├── 0000001.jpg
            └── ...
```

---

## 🔍 关键点索引说明

COCO-Pose 有17个关键点（索引0-16）：

```
 0 - nose(鼻子)
 1 - left_eye(左眼)
 2 - right_eye(右眼)
 3 - left_ear(左耳)
 4 - right_ear(右耳)
 5 - left_shoulder(左肩)
 6 - right_shoulder(右肩)
 7 - left_elbow(左肘)
 8 - right_elbow(右肘)
 9 - left_wrist(左腕)
10 - right_wrist(右腕)
11 - left_hip(左髋)
12 - right_hip(右髋)
13 - left_knee(左膝)
14 - right_knee(右膝)
15 - left_ankle(左踝)
16 - right_ankle(右踝)
```

---

## 🐍 Python脚本方式

如果需要更多控制，可以用Python脚本：

```python
import cv2

from ultralytics import YOLO

# 加载模型
model = YOLO("yolo11n-pose.pt")

# RTSP流地址
rtsp_url = "rtsp://admin:hik@12345@192.168.9.164/streaming/channels/101"

# 打开视频流
cap = cv2.VideoCapture(rtsp_url)

# 获取视频信息
fps = cap.get(cv2.CAP_PROP_FPS)
width = int(cap.get(cv2.CAP_PROP_FRAME_WIDTH))
height = int(cap.get(cv2.CAP_PROP_FRAME_HEIGHT))

# 创建视频写入器（保存结果）
fourcc = cv2.VideoWriter_fourcc(*"mp4v")
out = cv2.VideoWriter("output.mp4", fourcc, fps, (width, height))

frame_count = 0
while True:
    ret, frame = cap.read()
    if not ret:
        break

    # 进行姿态估计
    results = model.predict(frame, conf=0.5)

    # 绘制结果
    annotated_frame = results[0].plot()

    # 显示
    cv2.imshow("YOLO11 Pose", annotated_frame)

    # 保存
    out.write(annotated_frame)

    # 打印信息
    frame_count += 1
    if frame_count % 30 == 0:
        print(f"Processed {frame_count} frames")

    # 按'q'退出
    if cv2.waitKey(1) & 0xFF == ord("q"):
        break

# 释放资源
cap.release()
out.release()
cv2.destroyAllWindows()
```

**运行方式**:

```bash
python pose_rtsp.py
```

---

## ⚙️ 故障排除

### **问题1: 连接超时**

```bash
# 检查RTSP URL是否正确
ffplay 'rtsp://...'

# 检查网络连接
ping 192.168.9.164

# 检查防火墙
```

### **问题2: 内存不足**

```bash
# 使用更小的模型和分辨率
yolo pose predict model=yolo11n-pose.pt source='rtsp://...' imgsz=416 half=True
```

### **问题3: 处理速度慢**

```bash
# 增加帧跳过
yolo pose predict model=yolo11n-pose.pt source='rtsp://...' vid_stride=2

# 或减小分辨率
yolo pose predict model=yolo11n-pose.pt source='rtsp://...' imgsz=416
```

### **问题4: 结果不准确**

```bash
# 提高置信度阈值
yolo pose predict model=yolo11n-pose.pt source='rtsp://...' conf=0.6

# 使用更大的模型
yolo pose predict model=yolo11m-pose.pt source='rtsp://...'
```

---

## 📊 实时性能监控

添加性能检查的完整命令：

```bash
yolo pose predict \
  model=yolo11n-pose.pt \
  source='rtsp://admin:hik@12345@192.168.9.164/streaming/channels/101' \
  show=True \
  save=True \
  verbose=True \
  project=runs/pose \
  name=performance_test
```

查看速度统计：

```bash
# 训练完成后查看结果
cat runs/pose/performance_test/results.txt
```

---

## 🎯 推荐配置

### **实时监控系统** (需要流畅显示)

```bash
yolo pose predict \
  model=yolo11n-pose.pt \
  source='rtsp://admin:hik@12345@192.168.9.164/streaming/channels/101' \
  imgsz=416 \
  conf=0.5 \
  vid_stride=2 \
  show=True \
  half=True
```

### **精确分析** (需要高准确率)

```bash
yolo pose predict \
  model=yolo11m-pose.pt \
  source='rtsp://admin:hik@12345@192.168.9.164/streaming/channels/101' \
  imgsz=1280 \
  conf=0.6 \
  save=True
```

### **24小时监控** (长时间运行)

```bash
yolo pose predict \
  model=yolo11n-pose.pt \
  source='rtsp://admin:hik@12345@192.168.9.164/streaming/channels/101' \
  imgsz=480 \
  conf=0.5 \
  save=True \
  exist_ok=True
```

---

## 📚 相关文档

- 官方文档: https://docs.ultralytics.com/tasks/pose/
- YOLOv11 Models: https://docs.ultralytics.com/models/yolov11/
- Predict Mode: https://docs.ultralytics.com/modes/predict/
- GitHub: https://github.com/ultralytics/ultralytics
