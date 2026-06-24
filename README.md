<p align="center">
<img src="Yachiyo.png" width="220" alt="Yachiyo">
</p>

<h1 align="center">Yachiyo 八千代</h1>

<p align="center">动画《超时空辉夜姬！》月见八千代（Tsukimi Yachiyo）的同人 Live2D 模型 (｡･ω･｡)ﾉ♡</p>

<p align="center">
<a href="https://github.com/7l4i8y1a4n3g8-7l4i8y1a4n3g8-1438-9748/moesora"><img alt="theme" src="https://img.shields.io/badge/配套主题-Moesora-f9a8d4?style=flat-square"/></a>
<img alt="cubism" src="https://img.shields.io/badge/Live2D-Cubism%203-9aa5ff?style=flat-square"/>
</p>

基于 **Live2D Cubism 3** 制作的角色模型，精细装配、配备完整物理与多组表情，可用于网页看板娘、直播 / VTuber、桌面宠物等场景。也是 [Moesora](https://github.com/7l4i8y1a4n3g8-7l4i8y1a4n3g8-1438-9748/moesora) 主题的配套看板娘模型。

## 一、模型规格

| 项目 | 内容 |
| --- | --- |
| 格式 | Live2D Cubism 3（`model3.json` Version 3） |
| 核心模型 | `Yachiyo.moc3`（约 7.1 MB） |
| 贴图 | 2 张，均为 `4097 × 4097`（4K） |
| 参数 | 796 个 |
| 参数组 | 54 组 |
| 部件 | 109 个 |
| 表情 | 4 个 |
| 物理设定 | 183 条 |
| 动作文件 | 无（暂为「表情 only」） |

## 二、文件结构

```
Yachiyo/
├── Yachiyo.model3.json      # 模型入口配置（引用以下所有资源）
├── Yachiyo.moc3             # 编译后的核心模型数据
├── Yachiyo.physics3.json    # 物理设定（183 条）
├── Yachiyo.cdi3.json        # 显示信息：参数 / 参数组 / 部件命名
├── Yachiyo.png              # 预览图（500 × 500）
├── Yachiyo/
│   ├── texture_00.png       # 贴图 0（4097 × 4097）
│   └── texture_01.png       # 贴图 1（4097 × 4097）
├── smiling.exp3.json        # 表情：微笑
├── squinty.exp3.json        # 表情：眯眼
├── teardrop.exp3.json       # 表情：含泪
└── tears.exp3.json          # 表情：哭泣
```

## 三、表情

入口配置中已注册 4 个表情，可在运行时切换：

| 名称 | 文件 | 说明 |
| --- | --- | --- |
| `smiling` | `smiling.exp3.json` | 微笑 |
| `squinty` | `squinty.exp3.json` | 眯眼 |
| `teardrop` | `teardrop.exp3.json` | 含泪 |
| `tears` | `tears.exp3.json` | 哭泣 |

## 四、功能特性

- **自动眨眼**：`EyeBlink` 组已绑定眼睛开合参数，加载后即可启用自动眨眼。
- **丰富物理**：183 条物理设定覆盖侧发 / 前发 / 后发 / 下垂发、眼球、睫毛、表情、外套、裙摆、头饰、挂件等，发丝与服饰会随头身摆动自然飘动。
- **头身追踪**：提供标准的角度 / 位置参数，便于接入鼠标或视线跟随。
- **表情混合**：表情以叠加方式混合，可与眨眼、追踪共存而不冲突。

> ⚠️ **口型同步**：入口已声明 `LipSync` 组，但未绑定嘴部参数。如需音频驱动口型，请在 Cubism Editor 中将相应嘴部参数加入 `LipSync` 组后重新导出，或在运行时手动驱动。
>
> ⚠️ **动作**：仓库暂未包含 `.motion3.json` 动作文件。如需待机 / 点击等动作，请自行在 Cubism Editor 制作并在 `model3.json` 的 `Motions` 中注册。

## 五、使用方法

### 网页 / 看板娘（pixi-live2d-display）

```html
<script src="https://cdn.jsdelivr.net/npm/pixi.js@6/dist/browser/pixi.min.js"></script>
<!-- Live2D Cubism Core 运行库，需自行从 Live2D 官网获取 -->
<script src="live2dcubismcore.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/pixi-live2d-display/dist/cubism4.min.js"></script>

<canvas id="canvas"></canvas>
<script>
  (async () => {
    const app = new PIXI.Application({ view: document.getElementById('canvas') });
    const model = await PIXI.live2d.Live2DModel.from('Yachiyo.model3.json');
    app.stage.addChild(model);
    model.expression('smiling'); // 切换表情
  })();
</script>
```

### 作为 Moesora 主题的看板娘

在 [Moesora](https://github.com/7l4i8y1a4n3g8-7l4i8y1a4n3g8-1438-9748/moesora) 后台的「Live2D 看板娘」设置里，把模型地址填为本仓库 `Yachiyo.model3.json` 的可访问 URL 即可。

### 原生 / 引擎集成

使用官方 **Cubism SDK**（Native / Web / Unity）时，将 `Yachiyo.model3.json` 作为入口加载，SDK 会自动解析其引用的 moc3、贴图、物理与表情资源。

> 💡 贴图为 4K（单张 4097×4097），用于网页时建议按需压缩或降采样，以减小首屏体积与显存占用。

## 六、角色版权与说明

> ⚠️ 本模型为**非官方同人（二次创作）作品**，仅供学习交流与个人非商业用途。

- **角色**：月见八千代（Tsukimi Yachiyo）
- **出自**：动画电影《超时空辉夜姬！》（超かぐや姫！ / *Cosmic Princess Kaguya!*，2026）
- **原作 / 版权**：Studio Colorido × STUDIO CHROMATO（角色设计：へちま、永江彰浩）。角色形象及相关美术素材的一切权利，归原作品及其版权方所有。

本仓库仅为该角色的 Live2D 二次创作模型，**与原作官方无任何关联，亦未获其授权**。请勿用于商业用途；如需商用，须自行向版权方取得许可。
