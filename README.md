# Pre_2025 — pre-2025 works repository

本仓库存放 **2025 年之前** 的项目文本汇报 (主要是 PDF)。它是
[dorawolf.com](https://dorawolf.com) **作品档案页 (`/archive/`) 的数据源之一**——
网站从这里抓取每份 PDF 的下载链接，所以只要按下面的格式摆放文件，新文档会
**自动**出现在网站上。

> 与 `crabsatellite/2025` / `crabsatellite/2026` 不同：本仓库以 PDF 为主，
> 一般不含模型和图纸源文件。结构因此略简化——多了一层"年份"外壳。

---

## 1. 一份文档放哪里

```
<year-or-undated>/<YYYY-MM-DD-or-undated>_<type>_<slug>/docs/<原始文件名>.pdf
```

- **年份外壳** (`2022/`, `2023/`, `undated/`)：先按年份归档；不知道年份的进 `undated/`。
- **项目文件夹**：与 2025/2026 仓库一致，`YYYY-MM-DD_<type>_<slug>/`，
  日期未知时用 `undated_<type>_<slug>/`。
- `<type>` 在本仓库里通常是 `project` (项目方案文本)。
- `docs/` 子目录放 PDF 本身——**保留原文件名**，不必改名。

完整例子：

```
2022/2022-01-23_project_jiangxia-star-combined-report/docs/20220123-江夏之星两方案合稿okokok.pdf
2023/2023-03-24_project_yangtze-new-district-framework/docs/20230324长江新区文本框架汇总定稿okokok.pdf
undated/undated_project_optics-valley-exhibition-center/docs/中信院光谷展示中心两方案文本S.pdf
```

---

## 2. 项目内部 (可选目录)

虽然历史文档主要只有 `docs/`，但同一份命名规则也支持完整结构。如果以后给某个老项目补图、补模型，按这个布局放即可：

```
2023-03-24_project_yangtze-new-district-framework/
├── images/         ← 历史效果图、扫描图 (有就放，没有就不建这个目录)
│   ├── 1.jpg  2.jpg ...  ↑ 数字命名，1.jpg 自动当封面
│   └── _raw/             ↑ 不展示的图
├── models/
│   ├── rhino/  *.3dm
│   ├── sketchup/  *.skp *.skb
│   └── cad/  *.dwg *.dxf
├── docs/           ← *.pdf  *.docx  *.pptx (主体在这里)
└── data/           ← *.xlsx *.csv (面积表、概算表等)
```

---

## 3. 网站怎么读取这里

1. 网站构建时跑 `crabsatellite/dorawolf_portfolio/tools/organize.py`
2. 脚本走 `<year>/<project_id>/` 两层结构 (本仓库特有)，匹配
   `YYYY-MM-DD_<type>_<slug>/` 或 `undated_<type>_<slug>/` 的项目
3. 每份 PDF 进网站的"文档下载"列表，URL 直链
   `raw.githubusercontent.com/crabsatellite/Pre_2025/main/...`
4. 如果项目里有 `images/` (一般没有)，自动当画廊和封面

> 网页本身一字节都不存——你 push 进来的 PDF，网站下次 build 就能下载到。

---

## 4. 添加一份新文档 — 三步

```text
① 想清楚：年份 (确定就 YYYY/，不确定就 undated/) + 日期 (YYYY-MM-DD 或 undated)
   + 类型 (一般 project) + 一个英文 slug
② mkdir -p <year>/<id>/docs && cp <你的.pdf> <year>/<id>/docs/
③ git add . && git commit -m "add <slug>: <短描述>" && git push
```

完成。

---

## 5. 想给作品加文字介绍？

让 crabsatellite 在 `crabsatellite/dorawolf_portfolio/tools/organize.py` 里的
`PROJECT_COPY` 字典加一条 (key 用本仓库里的项目 ID，例如
`"2023-03-24_project_yangtze-new-district-framework"`)。本仓库不需要任何配置。

> 如果是与现有网站 `/projects/` 页 (jiangxia-star, hanjiang-bay-foreign-language-school
> 等) 重合的项目，把这里的 slug 改成与那边一致 (例如 `cybersecurity-center-phase-ii`)，
> 文档就会显示在那条主线项目下当作"补充材料"。

---

## 6. 命名细节

- **日期填什么**：PDF 上的日期 (例如 `20220123-江夏之星...` 用 `2022-01-23`)。
  实在没有的进 `undated/` 子目录。
- **slug 要不要改**：尽量不改 (URL 一部分)。如果一定要改，通知 crabsatellite
  同步更新 site 端 `PROJECT_COPY` 字典的 key。
- **同一项目的多版本**：用 slug 后缀区分 (`-concept` / `-combined-report` /
  `-baicao-variant` 等)，参考已有命名风格。

---

## 7. 不确定的就 ping crabsatellite

任何关于命名、文件放哪、网站显示效果的问题，问 crabsatellite。
他维护 `crabsatellite/dorawolf_portfolio` 这个网站仓库，从这里读数据。
