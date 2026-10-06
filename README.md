# 🧠 Image Prompt Reverse Engineer

> **把参考图片拆解成真正影响“像不像”的视觉结构，并重组为可用于 AI 生图的高质量提示词。**

<p align="center">
  <b>🎯 Visual Fidelity · 🧩 Composition · 💡 Lighting · 🧱 Spatial Structure · ✍️ Prompt Engineering</b>
</p>

---

## ✨ What it does

This Skill turns a reference image into a structured, high-fidelity image-generation prompt.

它不是简单“看图说话”，也不是堆砌：

`masterpiece / 8K / ultra detailed / cinematic`

而是优先识别真正决定画面相似度的因素：

- 主体身份与数量
- 姿势、动作与物体交互
- 构图、视角与负空间
- 人物 / 产品轮廓
- 光线方向与阴影几何
- 色彩关系
- 材质
- 景深
- 空间层次
- 最重要的视觉锚点

---

## 🎯 Core idea

很多图片“像不像”，并不取决于形容词数量。

真正重要的往往是：

> **结构 + 关系 + 构图 + 光影 + 少数高权重视觉特征**

例如：

- 手里到底拿着什么、怎么拿
- 人物在画面的哪个位置
- 有没有明显负空间
- 光线从哪边进入
- 阴影是不是斜穿画面
- 背景是否形成通道、道路、树线或纵深
- 主体是否被浅景深隔离
- 一个角色最有辨识度的轮廓是什么

---

## 🚀 Quick Use

给 Agent 一张参考图，然后说：

```text
分析这张图，并生成可以尽量复现其视觉结构和关键特征的 AI 生图提示词。
```

或者：

```text
反推这张图片的 Prompt。
重点保留构图、视角、人物动作、光线、阴影、材质和空间关系。
```

---

## 🧩 Supported workflows

适合用于：

- GPT Image
- Qwen-Image
- Seedream
- FLUX
- SDXL
- Gemini Image
- 其他支持自然语言 Prompt 的图像模型

---

## 📁 Repository Structure

```text
image-prompt-reverse-engineer/
│
├── SKILL.md
├── README.md
├── agents/
└── references/
```

完整规则见：

👉 [SKILL.md](./SKILL.md)

---

## 🔍 Design principles

### 1. Visual fidelity first

优先保留真正影响视觉相似度的结构，而不是追求华丽措辞。

### 2. Structure before style

先确定：

- 主体
- 动作
- 构图
- 空间关系
- 光影

再处理风格、质感和细节。

### 3. Avoid hallucinated detail

如果原图太小、模糊或被压缩，不虚构无法确认的微观细节。

### 4. Prompt ≠ caption

描述“图里有什么”只是第一步。

真正有用的 Prompt 还需要描述：

**东西在哪里、怎么摆、怎么受光、彼此有什么关系。**

---

## ⭐ Why use this Skill?

普通反推提示词经常得到：

```text
A beautiful cinematic scene, highly detailed, 8K...
```

但真正复现画面时帮助有限。

这个 Skill 更关注：

```text
subject placement
pose
camera viewpoint
negative space
lighting direction
shadow geometry
material response
depth structure
visual anchors
```

目标不是写出“看起来很专业”的 Prompt。

目标是：

> **让 Prompt 对重新生成这张图真的有帮助。**

---

## ⭐ Like it?

如果这个 Skill 对你的 AI 生图工作流有帮助，可以点一个 **Star ⭐**。
