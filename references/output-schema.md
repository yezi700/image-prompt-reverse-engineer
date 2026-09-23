# Output Schema

Use the compact default unless the user asks for a detailed teardown, machine-readable data, or multiple model variants.

## Detailed human-readable format

### 1. 图片类型

- 用途：
- 媒介：
- 主主体：
- 次主体：

### 2. 画面概述

2–5 sentences describing what the image presents.

### 3. 画面骨架

- 景别：
- 机位：
- 主体位置：
- 构图：
- 透视：
- 前景：
- 中景：
- 背景：

### 4. 主体专项分析

Output only relevant fields. For a person this may include:

- 外观：
- 发型：
- 服装：
- 动作：
- 表情：
- 视线：
- 人物与环境关系：

For animals, products, still life, landscapes, or recognizable characters, output the corresponding relevant fields instead.

### 5. 光线

- 主光方向：
- 光质：
- 明暗关系：
- 阴影几何：
- 特殊光效：

Only include 阴影几何 when the shadow shape materially affects resemblance.

### 6. 色彩

- 主色：
- 辅助色：
- 整体色调：
- 饱和度：
- 明度：

### 7. 材质与质感

List only the materials that meaningfully affect the recreation.

### 8. 视觉锚点

List 3–7 items in descending importance.

### 8.5. 关系锚点

Only output when subject-object interaction is important.

Examples:

- 狗嘴里横叼一支黄色郁金香
- 单枝玫瑰插在透明玻璃瓶中
- 人物双手捧着花束

### 8.6. 构图锚点

Only output when composition strongly affects similarity.

Examples:

- 大片留白集中在主体上方和右侧
- 斜向三角形光影切割背景
- 小路作为引导线通向画面深处亮部
- 浅景深使主体清晰、背景明显虚化

### 8.7. 角色固有锚点

Only output for recognizable fictional characters, mascots, or recurring standardized designs.

Separate persistent identity traits from the current image's pose, angle, background, and rendering treatment.

### 9. 可观察事实与推测

#### 可以直接观察到

Concrete visual facts.

#### 可能的实现方式

Optional. Keep clearly separated from observations.

### 10. 正向提示词

One coherent, ready-to-use prompt. Put high-priority anchors early.

### 11. Avoid / Negative

Only when useful for the selected model/workflow.

### 12. 模型适配版本

Only when the user specifies a target model or requests comparisons.

## Compact default

For routine use, prefer:

- 画面概述
- 视觉锚点
- 关系锚点（if interaction matters）
- 构图锚点（if composition strongly affects similarity）
- 角色固有锚点（for recognizable recurring characters）
- 正向提示词
- Negative/Avoid when needed
- target-model note when needed

## JSON-friendly format

When the user requests JSON or the skill is used programmatically, use stable keys:

```json
{
  "image_type": {
    "use_case": "",
    "medium": "",
    "primary_subject": "",
    "secondary_subjects": []
  },
  "visual_skeleton": {
    "shot_size": "",
    "viewpoint": "",
    "composition": "",
    "perspective": "",
    "foreground": "",
    "midground": "",
    "background": ""
  },
  "visual_anchors": [
    {"rank": 1, "description": ""}
  ],
  "relationship_anchors": [],
  "composition_anchors": [],
  "canonical_character_anchors": [],
  "observations": [],
  "implementation_suggestions": [],
  "positive_prompt": "",
  "negative_or_avoid": "",
  "target_model": "generic"
}
```

Do not output confidence percentages unless the user asks. If uncertainty matters, use plain language such as `uncertain`, `likely`, or `appears to be`.
