# Ultralytics YOLOv8/11 数据集详细说明

## 📋 目录
1. [目标检测数据集](#目标检测数据集)
2. [分割数据集](#分割数据集)
3. [姿态估计数据集](#姿态估计数据集)
4. [旋转框检测数据集](#旋转框检测数据集)
5. [特定领域数据集](#特定领域数据集)

---

## 🎯 目标检测数据集

### 1. **COCO 2017 (coco.yaml)**
- **来源**: Microsoft - https://cocodataset.org
- **数据量**:
  - 训练集: 118,287 张图像
  - 验证集: 5,000 张图像
  - 测试集: 20,288 张图像
- **类别**: 80 个（person, bicycle, car, motorcycle, airplane, bus, train, truck, boat, traffic light等）
- **数据大小**: 20.1 GB
- **格式**: 图像 + JSON标注
- **使用**: `yolo train data=coco.yaml`
- **说明**: 最常用的大规模目标检测数据集，包含日常物体检测

### 2. **COCO8 (coco8.yaml)**
- **来源**: Ultralytics - COCO 2017 前8张图像
- **数据量**:
  - 训练集: 4 张图像
  - 验证集: 4 张图像
- **类别**: 80 个（与COCO相同）
- **数据大小**: 1 MB
- **用途**: 快速测试、调试、完整性检查
- **说明**: 极小的测试数据集，用于快速验证模型代码

### 3. **COCO128 (coco128.yaml)**
- **来源**: Ultralytics - https://www.kaggle.com/datasets/ultralytics/coco128
- **数据量**:
  - 训练集: 128 张图像
  - 验证集: 128 张图像
- **类别**: 80 个
- **数据大小**: 7 MB
- **用途**: 快速原型设计和模型测试
- **说明**: COCO数据集的最小版本，适合快速模型验证

### 4. **PASCAL VOC (VOC.yaml)**
- **来源**: University of Oxford - http://host.robots.ox.ac.uk/pascal/VOC
- **数据量**:
  - 训练集: 16,551 张图像（2007+2012）
  - 验证集: 4,952 张图像
  - 测试集: 4,952 张图像
- **类别**: 20 个（aeroplane, bicycle, bird, boat, bottle, bus, car, cat, chair, cow, diningtable, dog, horse, motorbike, person, pottedplant, sheep, sofa, train, tvmonitor）
- **数据大小**: 2.8 GB
- **标注格式**: XML（自动转换为YOLO格式）
- **用途**: 经典的目标检测基准
- **说明**: 年代较久但影响深远的检测数据集，用于检测性能评估

### 5. **xView (xView.yaml)**
- **来源**: U.S. National Geospatial-Intelligence Agency (NGA) - https://challenge.xviewdataset.org
- **数据量**:
  - 训练集: 763 张图像（90%）
  - 验证集: 84 张图像（10%）
- **类别**: 60 个（Fixed-wing Aircraft, Small Aircraft, Cargo Plane, Helicopter, 车辆, 船舶, 工程机械, 建筑等）
- **数据大小**: 20.7 GB
- **图像特性**: 航拍/卫星影像，超高分辨率
- **获取方式**: 需要手动下载（需注册）
- **说明**: 从卫星/航拍图像中检测物体，包含60种不同的对象类别

### 6. **VisDrone (VisDrone.yaml)**
- **来源**: Tianjin University - https://github.com/VisDrone/VisDrone-Dataset
- **数据量**:
  - 训练集: 6,471 张图像
  - 验证集: 548 张图像
  - 测试集: 1,610 张图像
- **类别**: 10 个（pedestrian, people, bicycle, car, van, truck, tricycle, awning-tricycle, bus, motor）
- **数据大小**: 2.3 GB
- **图像特性**: 无人机（UAV）视角
- **说明**: 专为无人机目标检测设计，包含多种交通工具和行人

### 7. **Argoverse (Argoverse.yaml)**
- **来源**: Argo AI - https://www.cs.cmu.edu/~mengtial/proj/streaming/
- **数据量**:
  - 训练集: 39,384 张图像
  - 验证集: 15,062 张图像
  - 测试集: 可选
- **类别**: 8 个（person, bicycle, car, motorcycle, bus, truck, traffic_light, stop_sign）
- **数据大小**: 31.5 GB
- **应用场景**: 自动驾驶
- **说明**: 来自自动驾驶场景，包含真实的街道场景数据

### 8. **KITTI (kitti.yaml)**
- **来源**: Karlsruhe Institute of Technology & Toyota Technological Institute
- **数据量**:
  - 训练集: 5,985 张图像
  - 验证集: 1,496 张图像
- **类别**: 8 个（car, van, truck, pedestrian, person_sitting, cyclist, tram, misc）
- **数据大小**: 390.5 MB
- **应用场景**: 自动驾驶
- **说明**: 经典的自动驾驶数据集，包含3D检测信息

### 9. **Objects365 (Objects365.yaml)**
- **来源**: Megvii - https://www.objects365.org/
- **数据量**:
  - 训练集: 1,742,289 张图像
  - 验证集: 80,000 张图像
- **类别**: 365 个（Person, Sneakers, Chair, Car, Lamp, Glasses, Bottle, Desk, Cup, Street Lights等）
- **数据大小**: 712 GB
- **说明**: 超大规模的通用目标检测数据集，包含日常生活中的各种物体

### 10. **LVIS (lvis.yaml)**
- **来源**: Facebook AI Research - http://www.lvisdataset.org
- **数据量**:
  - 训练集: 100,170 张图像
  - 验证集: 19,809 张图像
  - 测试集: 5,000 张图像
- **类别**: 1,203 个（包括稀有物体）
- **数据大小**: 20.1 GB
- **特点**: 长尾分布，包含稀有物体
- **说明**: 包含1000多个物体类别，适合测试模型的泛化能力

### 11. **Open Images v7 (open-images-v7.yaml)**
- **来源**: Google - https://storage.googleapis.com/openimages/web/index.html
- **数据量**:
  - 训练集: 1,743,042 张图像
  - 验证集: 41,620 张图像
- **类别**: 500+ 个
- **数据大小**: 561 GB
- **说明**: 最大的开放式目标检测数据集，包含多种物体

### 12. **ImageNet (ImageNet.yaml)**
- **来源**: Stanford University - https://www.image-net.org/
- **数据量**:
  - 训练集: 1,281,167 张图像
  - 验证集: 50,000 张图像
- **类别**: 1,000 个
- **数据大小**: 144 GB
- **用途**: 图像分类（非检测）
- **说明**: 最经典的图像分类数据集

---

## 🎭 分割数据集

### 1. **COCO8-seg (coco8-seg.yaml)**
- **来源**: Ultralytics
- **任务**: 实例分割
- **数据量**: 训练/验证各4张
- **大小**: 1 MB
- **说明**: COCO8的分割版本，用于快速测试分割模型

### 2. **COCO128-seg (coco128-seg.yaml)**
- **来源**: Ultralytics
- **任务**: 实例分割
- **数据量**: 128张训练+128张验证
- **大小**: 7 MB
- **说明**: COCO128的分割版本

### 3. **Carparts-seg (carparts-seg.yaml)**
- **任务**: 汽车零件分割
- **数据量**:
  - 训练: 3,516 张
  - 验证: 276 张
  - 测试: 401 张
- **大小**: 133 MB
- **类别**: 汽车零件（back_bumper, back_door等）
- **说明**: 用于汽车零件的实例分割

### 4. **Crack-seg (crack-seg.yaml)**
- **任务**: 裂纹检测分割
- **数据量**:
  - 训练: 3,717 张
  - 验证: 112 张
  - 测试: 200 张
- **大小**: 91.6 MB
- **类别**: 1 个（crack）
- **说明**: 基础设施/材料表面的裂纹分割

### 5. **Package-seg (package-seg.yaml)**
- **任务**: 包装物分割
- **数据量**:
  - 训练: 1,920 张
  - 验证: 89 张
  - 测试: 188 张
- **大小**: 103 MB
- **说明**: 物流/包装行业的应用

---

## 🧘 姿态估计数据集

### 1. **COCO8-pose (coco8-pose.yaml)**
- **关键点**: 17 个（human body keypoints）
- **数据量**: 4张训练 + 4张验证
- **大小**: 1 MB
- **用途**: 快速测试姿态估计

### 2. **COCO-pose (coco-pose.yaml)**
- **来源**: Microsoft COCO 2017
- **关键点**: 17 个（head, shoulders, elbows, wrists, hips, knees, ankles）
- **数据量**:
  - 训练: 56,599 张
  - 验证: 2,346 张
- **大小**: 20.1 GB
- **说明**: 标准的人体姿态估计基准

### 3. **Hand-keypoints (hand-keypoints.yaml)**
- **关键点**: 21 个（手指关节）
- **数据量**:
  - 训练: 18,776 张
  - 验证: 7,992 张
- **大小**: 369 MB
- **应用**: 手势识别、虚拟现实
- **说明**: 手部细粒度的关键点检测

### 4. **Dog-pose (dog-pose.yaml)**
- **关键点**: 24 个
- **数据量**:
  - 训练: 6,773 张
  - 验证: 1,703 张
- **大小**: 337 MB
- **来源**: Stanford ImageNet Dogs
- **说明**: 宠物姿态估计（狗）

### 5. **Tiger-pose (tiger-pose.yaml)**
- **关键点**: 12 个
- **数据量**:
  - 训练: 210 张
  - 验证: 53 张
- **大小**: 49.8 MB
- **说明**: 野生动物姿态估计（虎）

---

## 📦 旋转框检测（OBB）数据集

### 1. **DOTA8 (dota8.yaml)**
- **任务**: 航拍影像中的旋转框检测
- **数据量**: 4张训练 + 4张验证
- **大小**: 1 MB
- **类别**: 16 个（plane, ship, storage tank等）
- **用途**: 快速OBB检测测试

### 2. **DOTA8-multispectral (dota8-multispectral.yaml)**
- **特点**: 多光谱（10通道）
- **数据量**: 4张训练 + 4张验证
- **大小**: 37.3 MB
- **说明**: DOTA8的多光谱版本

### 3. **DOTAv1 (DOTAv1.yaml)**
- **来源**: Wuhan University - https://captain-whu.github.io/DOTA/
- **数据量**:
  - 训练: 1,411 张
  - 验证: 458 张
  - 测试: 937 张
- **大小**: 2 GB
- **类别**: 15 个
- **说明**: 航拍影像中的旋转框检测基准

### 4. **DOTAv1.5 (DOTAv1.5.yaml)**
- **数据量**:
  - 训练: 1,411 张
  - 验证: 458 张
  - 测试: 937 张
- **大小**: 2 GB
- **说明**: DOTA的改进版本，增加了更多类别

---

## 🏢 特定领域数据集

### 1. **African-wildlife (african-wildlife.yaml)**
- **任务**: 非洲野生动物检测
- **数据量**:
  - 训练: 1,052 张
  - 验证: 225 张
  - 测试: 227 张
- **大小**: 100 MB
- **类别**: buffalo, elephant等
- **应用**: 野生动物保护、生物多样性监测

### 2. **Brain-tumor (brain-tumor.yaml)**
- **任务**: 医学影像 - 脑肿瘤检测
- **数据量**:
  - 训练: 893 张
  - 验证: 223 张
- **大小**: 4.21 MB
- **类别**: 2 个（negative, positive）
- **应用**: 医疗诊断

### 3. **Construction-PPE (construction-ppe.yaml)**
- **任务**: 建筑工地PPE（个人防护装备）检测
- **数据量**:
  - 训练: 1,132 张
  - 验证: 143 张
  - 测试: 141 张
- **大小**: 178.4 MB
- **类别**: helmet, gloves, vest等
- **应用**: 工地安全监测

### 4. **Medical-pills (medical-pills.yaml)**
- **任务**: 医药药丸检测
- **数据量**:
  - 训练: 92 张
  - 验证: 23 张
- **大小**: 8.19 MB
- **说明**: 药物识别应用

### 5. **HomeObjects-3K (HomeObjects-3K.yaml)**
- **任务**: 家居物体检测
- **数据量**:
  - 训练: 2,285 张
  - 验证: 404 张
- **大小**: 390 MB
- **类别**: bed, sofa, chair等
- **应用**: 家居自动化、机器人导航

### 6. **SKU-110K (SKU-110K.yaml)**
- **来源**: Trax Retail - https://github.com/eg4000/SKU110K_CVPR19
- **任务**: 零售货架检测
- **数据量**:
  - 训练: 8,219 张
  - 验证: 588 张
  - 测试: 2,936 张
- **大小**: 13.6 GB
- **类别**: 1 个（object）
- **应用**: 零售库存管理、货架监测

### 7. **Signature (signature.yaml)**
- **任务**: 签名检测
- **数据量**:
  - 训练: 143 张
  - 验证: 35 张
- **大小**: 11.3 MB
- **说明**: 文档处理、电子签名识别

### 8. **GlobalWheat2020 (GlobalWheat2020.yaml)**
- **来源**: University of Saskatchewan
- **任务**: 小麦穗检测
- **数据量**: 3,422 张（多个研究机构贡献）
- **大小**: 7.0 GB
- **应用**: 农业科技、作物监测
- **说明**: 来自多个国家的全球小麦数据集

---

## 📊 数据集对比总结

| 特性 | COCO | VOC | xView | VisDrone | KITTI | Objects365 |
|------|------|-----|-------|----------|-------|-----------|
| **规模** | 超大 | 中等 | 大 | 大 | 中等 | 最大 |
| **类别数** | 80 | 20 | 60 | 10 | 8 | 365 |
| **应用域** | 通用 | 通用 | 遥感 | 无人机 | 自动驾驶 | 通用 |
| **图像大小** | 中等 | 中等 | 超大 | 中等 | 中等 | 中等 |
| **标注质量** | 优 | 优 | 优 | 优 | 优 | 中 |

## 🚀 快速开始

```bash
# 训练COCO数据集
yolo detect train data=coco.yaml model=yolov8n.pt epochs=100

# 训练自定义数据集
yolo detect train data=custom.yaml model=yolov8n.pt epochs=100

# 使用COCO8快速测试
yolo detect train data=coco8.yaml model=yolov8n.pt epochs=1

# 分割任务
yolo segment train data=coco8-seg.yaml model=yolov8n-seg.pt epochs=100

# 姿态估计
yolo pose train data=coco8-pose.yaml model=yolov8n-pose.pt epochs=100
```

## 📚 更多资源

- 文档: https://docs.ultralytics.com
- GitHub: https://github.com/ultralytics/ultralytics
- 社区: https://community.ultralytics.com
