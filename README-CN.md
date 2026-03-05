# 🚬 CIGGATRO（烟牌）

Balatro 风格的 roguelike 卡牌构筑游戏，以中国香烟为主题。纯文字玩法，支持任意 AI 助手。

基于 [ciggies.app](https://ciggies.app) — 中国卷烟博物馆，作者 [@0x_ultra](https://x.com/0x_ultra)。

## 🎮 怎么玩

把这个 skill 喂给你的 AI 助手（Claude、GPT 等），然后说：

| 语言 | 触发词 |
|----------|---------|
| 中文 | `玩烟牌` / `开始游戏` / `ciggatro cn` |
| English | `play ciggatro` / `start game` / `ciggatro en` |
| 日本語 | `タバコゲーム` / `遊ぶ` / `ciggatro ja` |

## 📦 文件内容

- `SKILL.md` — 游戏规则和显示格式（喂给 AI 的主文件）
- `cards.json` — 150 张烟盒卡，带 ciggies.app 真实图片
- `ashtrays.json` — 50 个被动效果（类似 Balatro 的小丑）
- `lighters.json` — 22 个消耗品
- `specialties.json` — 12 个省份特产卡
- `smuggled.json` — 18 个稀有强力消耗品
- `licenses.json` — 24 个永久升级
- `stages.json` — 4 章节 + 隐藏章节 + Boss

## 🃏 游戏机制

### 卡牌类型（Balatro 对照）
| CIGGATRO | Balatro | 功能 |
|----------|---------|----------|
| 🚬 烟盒 | 扑克牌 | 主牌，打 combo |
| 🏺 烟灰缸 | 小丑 | 被动加成 |
| 🔥 打火机 | 塔罗牌 | 改造卡牌 |
| 🗺️ 特产卡 | 星球牌 | 升级省份 |
| 📦 走私品 | 幽灵牌 | 稀有消耗品 |
| 📜 许可证 | 凭证 | 永久升级 |

### Combo 维度
- **品牌** — 中华、玉溪、芙蓉王...（同品牌 = 倍率）
- **产地** — 云南、上海、湖北...（同省份 = 倍率）
- **年代** — 80s、90s、00s、10s、20s
- **稀有度** — ★ 到 ★★★★★

## 🖼️ 图片

所有烟盒图片从 ciggies.app CDN 加载：
```
https://www.ciggies.app/api/img/products/{sku}-0-128.webp
```

## 📖 设计文档

- [GDD 中文版](GDD-CN.md)
- [GDD English](GDD-EN.md)
- [GDD 日本語](GDD-JA.md)

## 📜 许可

游戏设计和代码：MIT License

香烟图片和数据：© [ciggies.app](https://ciggies.app)

## 🙏 鸣谢

- [@0x_ultra](https://x.com/0x_ultra) — ciggies.app 创作者
- 灵感来自 [Balatro](https://www.playbalatro.com/) by LocalThunk
