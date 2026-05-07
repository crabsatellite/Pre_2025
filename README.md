# Pre_2025 — pre-2025 works

存放 **2025 年之前** 的项目文本汇报 (主要是 PDF)。
[dorawolf.com](https://dorawolf.com) 的「档案」页从这里读文档下载链接。
**按下面的规则整理文件，整理完 push 上来即可**——网站会自动显示。

> 与 `2025` / `2026` 不同：本仓库以 PDF 为主，结构多了一层"年份"外壳。

---

## 1. 一份文档放哪里

路径格式：

```
<年份>/<日期_类型_英文名>/docs/<原始文件名.pdf>
```

举例：

```
2022/2022-01-23_project_jiangxia-star-combined-report/docs/20220123-江夏之星两方案合稿okokok.pdf
2023/2023-03-24_project_yangtze-new-district-framework/docs/20230324长江新区文本框架汇总定稿okokok.pdf
undated/undated_project_optics-valley-exhibition-center/docs/中信院光谷展示中心两方案文本S.pdf
```

| 段位 | 规则 |
|------|------|
| **年份外壳** | 知道年份就 `2022/`、`2023/`；不知道就 `undated/` |
| **项目文件夹名** | `日期_类型_英文名`；不知道日期用 `undated_类型_英文名` |
| **类型** | 一般是 `project` (项目方案文本) |
| **英文名** | 全小写英文 + `-`。**不要拼音首字母** |
| **PDF** | **保留原文件名**，不必改 |

---

## 2. 想给老项目补图、补模型？

虽然历史文档主要只有 PDF，但同一份命名规则也支持完整结构。如果以后给某个老项目补图、补模型：

```
2023-03-24_project_yangtze-new-district-framework/
├─ images/         ← 历史效果图、扫描图
│   ├─ 1.jpg  2.jpg ...   ← 命名 1、2、3，1 自动当封面
│   └─ _raw/                ← 不展示的图
├─ models/
│   ├─ rhino/  *.3dm
│   ├─ sketchup/  *.skp *.skb
│   └─ cad/  *.dwg *.dxf
├─ docs/           ← *.pdf  *.docx  *.pptx
└─ data/           ← *.xlsx *.csv
```

---

## 3. 想给作品加中英文标题 / 简介？

不用你写文字——告诉 crabsatellite 你想要的中文标题、英文标题、简介就行，
他在网站那边加上。

> 如果是与现有 `/projects/` 页 (jiangxia-star、cybersecurity-center-phase-ii 等) 重合的项目，
> **告诉 crabsatellite 用相同的英文名**——文档就会显示在那条主线项目下当作"补充材料"。

---

## 4. 几个小提醒

- **日期填什么**：PDF 上的日期 (例如 `20220123-...` 用 `2022-01-23`)。实在没有的进 `undated/`。
- **英文名 (slug) 别轻易改**——是网站链接的一部分。
- **同一项目多版本**：用 slug 后缀区分 (`-concept` / `-combined-report` / `-baicao-variant` 等)。
- **想删 / 重命名一个项目**？先 ping crabsatellite，他在网站端同步更新后你再动。

---

## 5. 流程

你按规则整理 + push → crabsatellite 定期同步 → dorawolf.com 自动更新。

不确定就 ping crabsatellite。
