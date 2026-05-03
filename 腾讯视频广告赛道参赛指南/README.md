# EmotionSense Ad · 情绪智投

> 基于多模态情绪感知与强化学习的智能广告决策引擎
>
> Multimodal Emotion Sensing + Reinforcement Learning for Smarter Ad Delivery

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Platform](https://img.shields.io/badge/platform-PC%20%7C%20Mobile%20%7C%20Tablet-blue)](https://github.com)
[![AI Model](https://img.shields.io/badge/AI-face--api.js%20%7C%20TencentCloud%20%7C%20BaiduAI-green)](https://github.com)

---

## 产品介绍

**EmotionSense Ad（情绪智投）** 是一款基于 AI 多模态情绪感知与强化学习的智能广告决策系统。

- 不是千人一面的大众广告，而是读懂你此刻情绪的专属体验
- 每一次广告决策都基于你独有的情绪基线，越用越懂你
- 所有情绪数据仅存储于本地，隐私安全有保障

> 本项目为 EmotionSense Ad 的 Web 原型，可直接在浏览器中体验完整功能。

---

## 核心特性

| 特性 | 说明 |
|------|------|
| **多模态情绪感知** | 面部微表情 + 视频播放行为 + 凝视轨迹，融合 240 维状态空间 |
| **个性化决策引擎** | 为每位用户独立学习 Q-Learning 策略，动态适配个人偏好 |
| **个人情绪基线** | 首次使用自动建立个人表情基准，决策更精准 |
| **强化学习大脑** | ε-greedy Q-Learning，持续自我迭代优化 |
| **边缘 AI 隐私保护** | 所有推理在本地完成，差分隐私技术保护个体数据 |
| **实时可视化** | 6 种情绪实时检测，情绪历史曲线，Q 值热力图 |

---

## 快速体验

### 方式一：直接打开（无需安装）

双击打开 `index.html`，或通过以下方式部署：

```bash
# GitHub Pages（部署到免费托管）
# 将项目推送到 GitHub，在 Settings → Pages 中选择 main 分支即可

# 或使用任意静态服务器
npx serve .
python -m http.server 8080
```

### 方式二：本地开发

```bash
# 克隆项目
git clone https://github.com/YOUR_USERNAME/EmotionSense-Ad.git
cd EmotionSense-Ad

# 直接用浏览器打开 index.html
# 或使用任意 HTTP 服务器（避免 CORS 问题）
npx serve .
```

---

## AI 模式切换

本原型支持 **4 种 AI 接入模式**，点击右上角 **配置 API 密钥** 自由切换：

| 模式 | 说明 | 精度 | 隐私 |
|------|------|------|------|
| **face-api.js**（默认） | 纯浏览器端推理，无需服务器 | 中 | 最高（数据不离开设备） |
| **腾讯云 API** | 腾讯云人脸检测与情绪分析 | 高 | 云端处理 |
| **百度 AI** | 百度 AI 开放平台情绪识别 | 高 | 云端处理 |
| **模拟演示** | 无摄像头时生成模拟情绪数据 | — | — |

---

## 技术架构

```
┌─────────────────────────────────────────────────────┐
│              EmotionSense Ad 技术架构                │
├─────────────────────────────────────────────────────┤
│  模块一：多模态情绪感知引擎                          │
│  ├── 面部微表情（CNN+Transformer，22个AU）          │
│  ├── 视频播放行为（暂停次数/拖拽频率/凝视时长）       │
│  ├── 凝视轨迹（眼部EAR/视线位置/眨眼频率）           │
│  └── 历史偏好数据（个人情绪基线）                   │
├─────────────────────────────────────────────────────┤
│  模块二：强化学习决策大脑                           │
│  ├── 状态空间：240维情绪状态向量                    │
│  ├── 动作空间：{不投放, 广告A/B/C...N}             │
│  ├── 探索策略：ε-greedy → 稳态 exploitation        │
│  └── 奖励函数：R = α×点击率 + β×完成率 - γ×流失率  │
├─────────────────────────────────────────────────────┤
│  模块三：广告位微表情专项追踪                       │
│  ├── 广告前5秒：密集采样，预测情绪走向              │
│  └── 广告后15秒：AU4/AU9皱眉检测，四级干预         │
├─────────────────────────────────────────────────────┤
│  模块四：AI数据库自进化系统                         │
│  ├── IndexedDB 本地存储，每150ms一条记录             │
│  ├── 一键导出 CSV/JSON，用于 TensorFlow/PyTorch    │
│  └── 弱监督标签 + 半自动标注，每7天模型迭代          │
└─────────────────────────────────────────────────────┘
```

---

## 项目结构

```
EmotionSense-Ad/
├── index.html          # 主页面（完整 H5 原型，扫码即用）
├── README.md           # 项目说明文档（本文件）
├── PROJECT.md          # 详细产品文档
├── LICENSE             # MIT 开源许可证
└── .gitignore          # Git 忽略配置
```

---

## 部署方案

| 方案 | 适用场景 | 成本 | 精度 |
|------|---------|------|------|
| face-api.js（当前） | 演示 / 原型 / 个人项目 | $0 | 中 |
| 腾讯云 API | 正式产品 / 企业 | 按调用计费 | 高 |
| 百度 AI | POC 验证 / 快速原型 | 新用户免费 | 高 |
| DeepFace 自建 | 企业级 / 私有化部署 | GPU 成本 | 最高 |

---

## 未来规划

- [ ] 跨平台（APP 端 / PC 端 / 电视端）统一体验
- [ ] 云端数据库同步，支持多用户协同数据采集
- [ ] 强化学习模型在线更新
- [ ] 联邦学习聚合多方用户数据

---

## 开源协议

本项目采用 [MIT License](LICENSE) 开源，欢迎 Fork 和 Star！

---

## 致谢

- [face-api.js](https://github.com/justadudewhohacks/face-api.js/) — 浏览器端人脸识别
- [Tencent Cloud](https://cloud.tencent.com/) — 云端 AI API
- [Baidu AI](https://ai.baidu.com/) — 情绪识别 API
- [DeepFace](https://github.com/serengil/deepface) — 企业级人脸分析
