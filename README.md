# GlassBoard Skins

GlassBoardRebuild 的 Dock 在线皮肤仓库。应用内「设置 → Dock 与面板 → 在线皮肤仓库…」填入 `kkalho/glassboard-skins` 即可浏览与安装。

## 仓库结构

```
catalog.json
skins/
  aurora/
    skin.json
    preview.png
  sunset/
    skin.json
    preview.png
  mint/
    skin.json
    preview.png
  graphite/
    skin.json
    preview.png
```

## catalog.json

```json
{
  "name": "GlassBoard Skins",
  "version": 1,
  "skins": [
    {
      "id": "aurora",
      "name": "极光 Aurora",
      "author": "kkalho",
      "description": "深海蓝绿渐变与冷色高光，适合深色壁纸。",
      "version": "1.0.0",
      "skin": "skins/aurora/skin.json",
      "preview": "skins/aurora/preview.png"
    }
  ]
}
```

- `skin` / `preview` 使用相对 `catalog.json` 所在目录的路径。
- 最多读取 50 个条目；预览图 ≤ 2MB，`skin.json` ≤ 256KB。

## skin.json

`skin.json` 只包含外观参数，不执行任何代码：

| 字段 | 说明 |
|---|---|
| `Id` / `Name` | 皮肤标识与显示名；`Id` 会净化为小写字母、数字、`-`、`_` |
| `Kind` | 0 普通玻璃 / 1 浅色 / 2 深色 / 3 霓虹 |
| `Tint` | 表面色调，`#RRGGBB`，留空表示不使用 |
| `OpacityPercent` | 不透明度 30–100 |
| `Radius` | 圆角 0–48 |
| `Gloss` / `Grain` / `Saturation` | 光泽、颗粒、饱和度 |
| `TintAlpha` / `TintBlend` | 色调强度 0–0.5、是否混合 |
| `Hairline` / `Specular` / `Shadow` | 发丝线、镜面高光、阴影 |
| `SurfaceGradient` | 表面是否使用纵向渐变 |
| `Background` | 可选背景图文件名，需与 `skin.json` 同目录（PNG/JPG/BMP/GIF，≤ 8MB） |
| `SliceLeft/Top/Right/Bottom` / `BackgroundOpacity` | 九宫格切片与背景不透明度 |

示例：

```json
{
  "Id": "aurora",
  "Name": "极光 Aurora",
  "Kind": 3,
  "Tint": "#0B2E3A",
  "OpacityPercent": 58,
  "Radius": 26,
  "Gloss": 0.3,
  "TintAlpha": 0.14,
  "TintBlend": true,
  "Hairline": true,
  "Specular": true,
  "Shadow": true,
  "Grain": 0.03,
  "Saturation": 1.2,
  "IconPack": 0,
  "SurfaceGradient": true
}
```

## 添加皮肤

1. 新建 `skins/<id>/skin.json`，可附 `preview.png` 与背景图。
2. 在 `catalog.json` 的 `skins` 数组追加条目。
3. 提交并推送，应用内重新加载仓库即可看到。
