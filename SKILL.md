---
name: ciggatro
description: Play CIGGATRO, a Balatro-style roguelike deckbuilder themed around Chinese cigarettes. Triggers: 玩烟牌, play ciggatro, ciggatro cn/en/ja, タバコゲーム. Collect cigarette packs from ciggies.app, build combos by brand/province/era, defeat bosses. Supports Chinese, English, Japanese.
---

# 🚬 CIGGATRO — Text-Based Roguelike Deckbuilder

A Balatro-style card game played entirely through text. You are the game engine.

---

## 🎮 Game Triggers & Language Detection

**Chinese triggers:** `玩烟牌` / `开始游戏` / `ciggatro cn` → 中文界面
**English triggers:** `play ciggatro` / `start game` / `ciggatro en` → English UI
**Japanese triggers:** `タバコゲーム` / `遊ぶ` / `ciggatro ja` → 日本語インターフェース

**Rules commands:** `规则` / `怎么玩` (中文) | `rules` / `tutorial` (English) | `ルール` / `遊び方` (日本語)

**Language switch (anytime):** 
- `切换中文` / `中文` → 中文
- `switch english` / `english` → English  
- `日本語に切替` / `日本語` → 日本語

Save language preference in save file: `"language": "zh"` / `"language": "en"` / `"language": "ja"`
After initial trigger, follow user's input language (auto-switch).

---

## 🚀 Onboarding Flow

When user triggers the game:

### Step 1: Check for existing save
```
Load saves/[username].json
- If exists AND has progress → ask "继续游戏" or "新游戏"
- If not exists → new player flow
```

### Step 2: New Player Welcome

**中文欢迎 (触发词: 玩烟牌 / 开始游戏 / ciggatro cn)**
```
╔══════════════════════════════════════════╗
║       🚬 C I G G A T R O 🚬              ║
║      中国卷烟博物馆 · 收藏之旅           ║
╚══════════════════════════════════════════╝

欢迎来到 CIGGATRO！

这是一款以中国香烟为主题的卡牌游戏。
通过收集烟盒、组合出牌，挑战各路 Boss。

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

🖼️ 显示模式：
A. 图片模式 — 显示 ciggies.app 真实烟盒图片（可能加载较慢或失败）
B. 文字模式 — 纯文字，速度快

📖 游戏模式：
1️⃣ 新手教学 — 带你玩一局，边玩边学
2️⃣ 直接开始 — 我会玩，跳过教程
3️⃣ 查看规则 — 先看看规则再决定

💰 起始资源：50 烟票
🏺 起始装备：玻璃烟灰缸（+5分）

回复: A1 / A2 / B1 / B2 / A3 / B3
```

**English Welcome (triggers: play ciggatro / start game / ciggatro en)**
```
╔══════════════════════════════════════════╗
║       🚬 C I G G A T R O 🚬              ║
║     Chinese Cigarette Museum Adventure   ║
╚══════════════════════════════════════════╝

Welcome to CIGGATRO!

A Balatro-style roguelike deckbuilder themed around
Chinese cigarettes. Collect packs, build combos, beat bosses.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

🖼️ Display Mode:
A. Image Mode — Real cigarette images from ciggies.app (may load slowly or fail)
B. Text Mode — Text only, fast

📖 Game Mode:
1️⃣ Tutorial — Learn as you play
2️⃣ Jump In — I know how to play
3️⃣ View Rules — Read rules first

💰 Starting: 50 Tickets
🏺 Starting Gear: Glass Ashtray (+5 pts)

Reply: A1 / A2 / B1 / B2 / A3 / B3
```

**日本語ウェルカム (トリガー: タバコゲーム / 遊ぶ / ciggatro ja)**
```
╔══════════════════════════════════════════╗
║       🚬 C I G G A T R O 🚬              ║
║      中国タバコ博物館 · コレクション旅   ║
╚══════════════════════════════════════════╝

CIGGATROへようこそ！

中国タバコをテーマにしたローグライク
デッキビルダーです。パックを集めて、
コンボを組んで、ボスを倒そう。

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

🖼️ 表示モード：
A. 画像モード — ciggies.appの実物写真（読み込み遅い場合あり）
B. テキストモード — 文字のみ、高速

📖 ゲームモード：
1️⃣ チュートリアル — 遊びながら学ぶ
2️⃣ すぐ始める — ルール知ってる
3️⃣ ルール確認 — 先にルールを見る

💰 初期資金：50 チケット
🏺 初期装備：ガラス灰皿（+5点）

返信: A1 / A2 / B1 / B2 / A3 / B3
```

### Step 3a: Tutorial Mode (选择1)
- Start a guided game with explanations
- First hand: explain card attributes (brand, origin, era, rarity)
- First play: explain combo system with examples
- First shop: explain purchasing
- After tutorial round: "教学结束！现在你可以自己玩了。要重新开始正式游戏吗？"

### Step 3b: Direct Start (选择2)
- Initialize new game
- Deal cards
- Show hand WITHOUT hints
- Wait for player commands

### Step 3c: Show Rules (选择3)
- Display RULES.md content
- After rules: "看完了？准备好开始了吗？回复「开始」进入游戏"

### Returning Player Flow

**中文:**
```
欢迎回来，[玩家名]！

📍 上次进度: 第X章 · 第X关
💰 烟票: XX
🃏 牌组: XX张

1️⃣ **继续游戏**
2️⃣ **重新开始** (进度会清零)

回复 1 或 2
```

**English:**
```
Welcome back, [player]!

📍 Last progress: Chapter X · Stage X
💰 Tickets: XX
🃏 Deck: XX cards

1️⃣ **Continue**
2️⃣ **Restart** (progress will reset)

Reply 1 or 2
```

**日本語:**
```
おかえりなさい、[プレイヤー名]！

📍 前回の進行: 第X章 · ステージX
💰 チケット: XX
🃏 デッキ: XX枚

1️⃣ **続きから**
2️⃣ **最初から** (進行リセット)

返信 1 か 2
```

---

## 📖 Tutorial Script

When in tutorial mode, add explanations after each action:

**Hand display (first time):**

中文:
```
💡 教学提示：
每张牌有4个关键属性：
• 品牌 — 中华、玉溪等（相同品牌可触发 combo）
• 产地 — 省份（相同省份也有 combo）
• 年代 — 80s/90s/00s 等
• 稀有度 — ★越多，基础分越高
```

English:
```
💡 Tutorial Tip:
Each card has 4 key attributes:
• Brand — Chunghwa, Yuxi, etc. (same brand = combo)
• Origin — Province (same province = combo)
• Era — 80s/90s/00s, etc.
• Rarity — More ★ = higher base score
```

日本語:
```
💡 チュートリアル：
各カードには4つの属性があります：
• ブランド — 中華、玉溪など（同ブランド＝コンボ）
• 産地 — 省（同じ省＝コンボ）
• 年代 — 80s/90s/00s など
• レア度 — ★が多いほど基礎点が高い
```

**After first play:**

中文:
```
💡 教学提示：
刚才触发了「同乡」combo（两张云南）！
相同产地的牌一起出会有加成：
• 2张同产地 = ×1.3
• 3张同产地 = ×2.0
• 以此类推...

品牌 combo 加成更高，试试收集同品牌的牌！
```

English:
```
💡 Tutorial Tip:
You triggered a "Hometown" combo (two Yunnan cards)!
Same-origin cards get multipliers:
• 2 same origin = ×1.3
• 3 same origin = ×2.0
• And so on...

Brand combos give even higher bonuses!
```

日本語:
```
💡 チュートリアル：
「同郷」コンボ発動（雲南2枚）！
同じ産地のカードにはボーナス：
• 同産地2枚 = ×1.3
• 同産地3枚 = ×2.0
• 以下同様...

ブランドコンボはさらに高いボーナス！
```

**Save file flags:**
```json
{
  "tutorialMode": true,
  "tutorialStep": 1,
  "imageMode": true
}
```

- `tutorialMode`: Set false after tutorial completes
- `imageMode`: true = show images, false = text only

---

## 🖼️ Display Modes

### Image Mode (imageMode: true)

```
⚠️⚠️⚠️ CRITICAL — 必须严格执行 ⚠️⚠️⚠️

显示手牌前检查清单：
☐ 每张卡都有 image_url 链接？
☐ 链接单独一行，不在代码块里？
☐ 每条消息最多 4 张卡？
☐ 包含 flavor 文字？

如果不确定，重新读这个 section！
```

**核心原则：每张卡下方都放图片链接！**

即使 Discord 不嵌入预览，用户也能点击链接查看。

**规则（必须全部遵守）：**
1. ✅ 每条消息最多 4 张卡（Discord embed 限制）
2. ✅ 图片 URL 必须**单独一行**，**不能**放在代码块里
3. ✅ 用 `message` 工具分批发送
4. ✅ **无论是否能预览，链接必须保留**
5. ✅ 从 cards.json 读取 `image_url` 字段

**正确格式（每条消息）：**

🃏 你的手牌 (1-4):

**[1] 🚬 中华（硬）★★★★★**
上海 · 00s · 烤烟 · 基础分: 50
*"国宴标配。"*
https://www.ciggies.app/api/img/products/202507301114199930.jpg

**[2] 🚬 玉溪（软）★★★**
云南 · 10s · 烤烟 · 基础分: 30
*"云南烤烟的代表。"*
https://www.ciggies.app/api/img/products/20060117165155.png

**[3] 🚬 芙蓉王（硬）★★★**
湖南 · 00s · 烤烟 · 基础分: 32
*"芙蓉国里尽朝晖。"*
https://www.ciggies.app/api/img/products/20051206113448.jpg

**[4] 🚬 利群（软）★★**
浙江 · 00s · 烤烟 · 基础分: 18
*"商帮之选。"*
https://www.ciggies.app/api/img/products/20050913105155.jpg

（然后发第二条消息显示 5-8 张，格式相同）

**❌ 错误示范：**
- 把 URL 放在 ``` 代码块里（不会预览）
- 把 URL 放在 `<>` 角括号里（会抑制预览）
- 省略链接（用户无法点击查看）

### Text Mode (imageMode: false)
- 纯文字，不显示图片链接
- 速度快，适合弱网环境
- 示例：
```
[1] 🚬 中华（硬）★★★★★ | 上海 · 00s | 基础分: 50
[2] 🚬 玉溪（软）★★★ | 云南 · 10s | 基础分: 30
[3] 🚬 芙蓉王（硬）★★★ | 湖南 · 00s | 基础分: 32
```

### Switching modes mid-game
Player can say `切换模式` / `switch mode` to toggle imageMode

---

## 🎴 Card Types Overview

| Type | Icon | Count | Function |
|------|------|-------|----------|
| **烟盒** Packs | 🚬 | 150 | Main cards, make combos |
| **烟灰缸** Ashtrays | 🏺 | 50 | Passive bonuses (Jokers) |
| **打火机** Lighters | 🔥 | 22 | Consumables, modify packs |
| **特产卡** Specialties | 🗺️ | 12 | Level up province combos |
| **走私品** Smuggled | 📦 | 18 | Rare powerful consumables |
| **许可证** Licenses | 📜 | 24 | Permanent shop upgrades |

---

## Game State Structure

```json
{
  "player": "username",
  "chapter": 1,
  "stage": 1,
  "round": 1,
  "maxRounds": 4,
  "score": 0,
  "targetScore": 200,
  "tickets": 50,
  "deck": [...],
  "hand": [...],
  "discards": 3,
  "discardsUsed": 0,
  "ashtrays": [...],
  "ashtraySlots": 3,
  "consumables": [],
  "consumableSlots": 2,
  "licenses": [],
  "provinceLevels": {
    "云南": 1, "上海": 1, "湖南": 1, ...
  },
  "collection": []
}
```

---

## 🚬 烟盒 Packs (150 Cards)

### Attributes

| Attribute | Description | Examples |
|-----------|-------------|----------|
| **Brand** | Cigarette brand | 中华, 玉溪, 芙蓉王 |
| **Origin** | Province | 云南, 上海, 湖北 |
| **Era** | Decade | 80s, 90s, 00s, 10s, 20s |
| **Type** | Tobacco type | 烤烟, 混合, 细支, 爆珠, 雪茄 |
| **Rarity** | Star rating | ★ to ★★★★★ |
| **Price** | RMB price tier | ¥10-500+ |

### Rarity System

| Rarity | Stars | Mult | Price Range | Examples |
|--------|-------|------|-------------|----------|
| Common | ★ | ×1.0 | ¥5-15 | 红双喜, 红梅, 白沙 |
| Uncommon | ★★ | ×1.5 | ¥15-30 | 利群, 云烟, 红塔山 |
| Rare | ★★★ | ×2.0 | ¥30-60 | 玉溪, 芙蓉王, 黄鹤楼 |
| Epic | ★★★★ | ×3.0 | ¥60-100 | 南京九五, 天叶, 荷花 |
| Legendary | ★★★★★ | ×5.0 | ¥100+ | 中华, 熊猫, 大重九 |

### Pack Modifiers (Applied by Lighters)

| Modifier | Icon | Effect |
|----------|------|--------|
| **镀金** Gilded | 💰 | +15 base score |
| **全息** Holo | ✨ | +20% tickets when scored |
| **限量** Limited | 🔢 | Count as 2 cards for combos |
| **老版** Vintage | 📜 | Era counts as any |
| **外烟** Foreign | 🌍 | Origin counts as any |
| **封印** Sealed | 🔒 | Cannot be discarded |

---

## 🏺 烟灰缸 Ashtrays (50 Cards)

Passive effects. Max 5 slots.

### Rarity Distribution

| Rarity | Count | Slot Cost |
|--------|-------|-----------|
| Common | 20 | 1 slot |
| Uncommon | 15 | 1 slot |
| Rare | 10 | 1 slot |
| Legendary | 5 | 2 slots |

### Effect Types

| Type | Description | Example |
|------|-------------|---------|
| `flat_bonus` | +X score per round | 玻璃烟灰缸 +5 |
| `mult_bonus` | ×X to final score | Zippo ×1.5 first play |
| `rarity_bonus` | +X per rarity type | 铁皮罐: Common +10 |
| `origin_bonus` | +X per province | 景德镇缸: 江西 +15 |
| `brand_mult` | ×X for brand | 大会堂缸: 中华 ×5 |
| `combo_enhance` | Better combos | 麻将桌: +1 combo tier |
| `economy` | More tickets | 商人缸: +20% tickets |
| `transform` | Change cards | 升级缸: Random upgrade |

---

## 🔥 打火机 Lighters (22 Cards)

Consumables that modify your packs. Use once, then gone.

### Lighter List

| Name | Effect | Rarity |
|------|--------|--------|
| **一次性打火机** | 随机1张牌 +10 基础分 | Common |
| **Zippo经典款** | 选1张牌变镀金 | Common |
| **防风打火机** | 选1张牌封印(不可弃) | Common |
| **USB充电打火机** | 选1张牌变全息 | Uncommon |
| **煤油打火机** | 选2张牌交换品牌 | Uncommon |
| **雪茄剪火机** | 雪茄型烟+50分本局 | Uncommon |
| **金色Zippo** | 选1张牌变限量版 | Rare |
| **复古火柴盒** | 选1张牌变老版 | Rare |
| **镶钻打火机** | 选1张牌+2★稀有度 | Rare |
| **外贸样品机** | 选1张牌变外烟 | Rare |
| **登喜路打火机** | 复制1张牌(加入手牌) | Epic |
| **Cartier打火机** | 选1张牌变★★★★★ | Legendary |

### Usage

```
> use lighter 1 on 3
🔥 使用【一次性打火机】在【红双喜】上
红双喜 基础分: 10 → 20
```

---

## 🗺️ 特产卡 Specialties (12 Cards)

Level up province combo bonuses. Permanent upgrade to that province.

### Province Specialty Cards

| Province | Card Name | Level Up Effect |
|----------|-----------|-----------------|
| **云南** | 普洱茶饼 | 云南combo ×1.2 per level |
| **上海** | 南翔小笼 | 上海combo ×1.2 per level |
| **湖南** | 臭豆腐 | 湖南combo ×1.2 per level |
| **湖北** | 热干面 | 湖北combo ×1.2 per level |
| **江苏** | 阳澄湖蟹 | 江苏combo ×1.2 per level |
| **浙江** | 龙井茶 | 浙江combo ×1.2 per level |
| **广东** | 广式早茶 | 广东combo ×1.2 per level |
| **福建** | 铁观音 | 福建combo ×1.2 per level |
| **四川** | 火锅底料 | 四川combo ×1.2 per level |
| **贵州** | 茅台酒 | 贵州combo ×1.2 per level |
| **河南** | 胡辣汤 | 河南combo ×1.2 per level |
| **山东** | 煎饼卷葱 | 山东combo ×1.2 per level |

### Usage

```
> use specialty 云南
🗺️ 使用【普洱茶饼】
云南产地等级: Lv.1 → Lv.2
云南combo倍率: ×1.0 → ×1.2
```

---

## 📦 走私品 Smuggled Goods (18 Cards)

Rare, powerful consumables. Hard to find.

### Smuggled Goods List

| Name | Effect | Rarity |
|------|--------|--------|
| **免税烟** | 下次购买免费 | Uncommon |
| **假烟鉴定器** | 揭示Boss下回合封印 | Uncommon |
| **快递包裹** | 随机获得2张烟盒 | Uncommon |
| **海关通行证** | 本局限定烟不被扣押 | Rare |
| **黑市名片** | 下次商店全是稀有品 | Rare |
| **保税仓库** | 复制1个烟灰缸 | Rare |
| **走私船票** | 跳过当前Boss | Epic |
| **洗钱机** | 烟票×2 | Epic |
| **外交豁免** | 本章免疫所有Boss技能 | Epic |
| **熊猫繁殖证** | 复制所有熊猫牌 | Legendary |
| **时光机** | 重新开始本关(保留升级) | Legendary |
| **烟草垄断权** | 所有烟+1★稀有度(永久) | Legendary |

---

## 📜 许可证 Licenses (24 Cards)

Permanent upgrades. Buy from shop, always active.

### License Categories

**经营类 Operations**
| Name | Effect | Price |
|------|--------|-------|
| **零售许可证** | 商店+1个烟盒选择 | 50票 |
| **批发许可证** | 商店烟盒-20%价格 | 80票 |
| **进口许可证** | 解锁国际品牌 | 100票 |
| **专卖许可证** | 商店必出1张限定 | 150票 |

**仓储类 Storage**
| Name | Effect | Price |
|------|--------|-------|
| **烟灰缸架** | +1 烟灰缸槽位 | 60票 |
| **消耗品柜** | +1 消耗品槽位 | 40票 |
| **恒温仓库** | 起手多抽2张 | 70票 |
| **保险柜** | 烟灰缸不会被Boss偷 | 90票 |

**技术类 Technical**
| Name | Effect | Price |
|------|--------|-------|
| **鉴定资质** | 显示牌的隐藏属性 | 30票 |
| **防伪认证** | 免疫假烟效果 | 50票 |
| **质检证书** | 每关开始升级1张随机牌 | 120票 |

**金融类 Financial**
| Name | Effect | Price |
|------|--------|-------|
| **记账本** | 显示预计得分 | 25票 |
| **收银机** | 每回合+3烟票 | 80票 |
| **信用额度** | 可透支50烟票 | 100票 |

---

## Display Formats

### Main Game Display

```
╔═══════════════════════════════════════════════════════════════╗
║  🚬 CIGGATRO — 第1章 第2关                                      ║
╠═══════════════════════════════════════════════════════════════╣
║  🎯 目标: 300分  |  📊 当前: 145分  |  🔄 回合: 2/4            ║
║  🎫 烟票: 75     |  🗑️ 弃牌: 3次    |  📦 消耗品: 2/2         ║
╠═══════════════════════════════════════════════════════════════╣
║  你的手牌:                                                     ║
║                                                                ║
║  [1] 🚬 中华(硬) 💰 (上海/00s) ★★★★★ 基础:65              ║
║  [2] 🚬 玉溪(软) (云南/10s) ★★★ 基础:30                     ║
║  [3] 🚬 芙蓉王 ✨ (湖南/00s) ★★★ 基础:32                    ║
║  [4] 🚬 红双喜 🔒 (上海/80s) ★ 基础:10                       ║
║  [5] 🚬 利群 (浙江/10s) ★★ 基础:20                          ║
║  [6] 🚬 云烟 (云南/90s) ★★ 基础:20                          ║
║  [7] 🚬 黄鹤楼1916 (湖北/10s) ★★★★★ 基础:60               ║
║  [8] 🚬 白沙 (湖南/90s) ★ 基础:12                            ║
╠═══════════════════════════════════════════════════════════════╣
║  🏺 烟灰缸: [Zippo打火机 ×2首发] [景德镇缸 江西+15] [空]      ║
╠═══════════════════════════════════════════════════════════════╣
║  📦 消耗品: [🔥金色Zippo] [🗺️普洱茶饼]                        ║
╠═══════════════════════════════════════════════════════════════╣
║  💡 可用combo: 上海×2 | 云南×2 | 湖南×2                       ║
╚═══════════════════════════════════════════════════════════════╝
```

### Shop Display

```
╔═══════════════════════════════════════════════════════════════╗
║  🏪 商店                                         🎫 烟票: 120  ║
╠═══════════════════════════════════════════════════════════════╣
║  🚬 烟盒                                                       ║
║  [1] 苏烟(金砂) ★★★ — 28票                                   ║
║  [2] 黄金叶(天叶) ★★★★ — 45票                                ║
║                                                                ║
║  🏺 烟灰缸                                                     ║
║  [3] 茅台酒瓶盖 (贵州×3) — 75票                                ║
║                                                                ║
║  📦 消耗品                                                     ║
║  [4] 🔥 USB充电打火机 — 15票                                   ║
║  [5] 📦 快递包裹 — 20票                                        ║
║                                                                ║
║  📜 许可证                                                     ║
║  [6] 烟灰缸架 (+1槽位) — 60票                                  ║
║                                                                ║
║  🗑️ 服务                                                       ║
║  [7] 移除1张牌 — 10票                                          ║
╠═══════════════════════════════════════════════════════════════╣
║  命令: buy 1 | buy 3 | skip                                    ║
╚═══════════════════════════════════════════════════════════════╝
```

---

## Commands

### Basic Commands

| Command | Action | Example |
|---------|--------|---------|
| `play [n...]` | Play cards | `play 1 4 7` |
| `discard [n...]` | Discard cards | `discard 2 5` |
| `hand` | Show hand | `hand` |
| `info [n]` | Card details | `info 3` |

### Consumable Commands

| Command | Action | Example |
|---------|--------|---------|
| `items` | Show consumables | `items` |
| `use [item] on [card]` | Use consumable | `use 1 on 3` |
| `use [item]` | Use without target | `use 2` |

### Shop Commands

| Command | Action | Example |
|---------|--------|---------|
| `shop` | Show shop | `shop` |
| `buy [n]` | Buy item | `buy 3` |
| `skip` | Leave shop | `skip` |

---

## 🏁 Stage Clear Flow

When player reaches target score:

```
╔════════════════════════════════════════╗
║      🎉 关 卡 通 过 ！                 ║
║                                        ║
║      得分: XXX / 目标                  ║
║      获得烟票: +XX 💰                  ║
╚════════════════════════════════════════╝

接下来：
1️⃣ 逛商店
2️⃣ 直接下一关

回复 1 或 2
```

**Important:** Do NOT auto-enter shop. Always ask player first.

### Meta Commands

| Command | Action |
|---------|--------|
| `rules` | Show game rules (RULES.md) |
| `save` | Save game |
| `stats` | Show statistics |
| `collection` | Show collection |
| `licenses` | Show active licenses |
| `provinces` | Show province levels |
| `help` | Show all commands |
| `quit` | Exit game |

---

## Combo System

### Brand Combos

| Name | Condition | Multiplier |
|------|-----------|------------|
| 散烟 | 1 card | ×1 |
| 对子 | Same brand ×2 | ×1.5 |
| 三条 | Same brand ×3 | ×2.5 |
| 四条 | Same brand ×4 | ×4 |
| 一条龙 | Same brand ×5 | ×8 |

### Origin Combos (Affected by Province Level)

| Name | Condition | Base Mult |
|------|-----------|-----------|
| 同乡 | Same origin ×2 | ×1.3 |
| 老乡见老乡 | Same origin ×3 | ×2 |
| 省队 | Same origin ×4 | ×3 |
| 全省制霸 | Same origin ×5 | ×5 |

*Province Level bonus: Base Mult × (1 + 0.2 × Level)*

### Era Combos

| Name | Condition | Multiplier |
|------|-----------|------------|
| 同龄人 | Same era ×2 | ×1.2 |
| 年代秀 | Same era ×3 | ×1.8 |
| 时代印记 | Same era ×5 | ×3 |
| 穿越 | 80s + 20s | ×2.5 |

### Special Combos

| Name | Condition | Effect |
|------|-----------|--------|
| 大满贯 | Same brand+origin+era | ×10 |
| 杂货铺 | 5 different brands | +50 flat |
| 最后一根 | Last card in hand | ×3 |
| 外烟配中烟 | 国际+大陆 brand | ×1.5 |
| 雪茄拼盘 | 3+ cigars | ×2 + 每张+20 |

---

## Boss Mechanics

### Chapter 1 Boss: 控烟办主任

```
"根据控烟条例，本回合禁止吸【中华】！"

机制: 每回合随机封印1个品牌
血量: 600分 / 5回合
```

### Chapter 2 Boss: 假烟贩子

```
"这批货绝对正品，你看这防伪标..."

机制: 每回合1-2张手牌变假烟(负分)
假烟标识: 🚫 (基础分变为负数)
血量: 1000分 / 5回合
```

### Chapter 3 Boss: 海关总署

```
"请出示申报单。"

机制: 限定(★★★★★)烟被扣押
每2回合释放1张(扣20烟票)
血量: 2000分 / 5回合
```

### Chapter 4 Boss: 戒烟意志

```
"你真的需要再来一根吗？"

机制: 每打出1张牌，下一张-10%
每3回合重置debuff
血量: 4000分 / 6回合
```

### Hidden Boss: 烟草总局

```
"专卖制度是有原因的。"

机制: 综合所有Boss能力，每5回合切换
血量: 15000分 / 8回合
```

---

## Scoring Formula

```
最终得分 = (Σ 卡牌分数) × 品牌Combo × 产地Combo × 年代Combo × 烟灰缸倍率 + 固定加成

卡牌分数 = 基础分 × 稀有度倍率 × 修饰符加成

产地Combo = 基础倍率 × (1 + 0.2 × 省份等级)
```

---

## Data Files

**⚠️ 重要：游戏开始时必须加载 cards.json！**

从 GitHub 获取卡牌数据：
```
https://raw.githubusercontent.com/tokenfed/ciggatro/main/cards.json
```

用 `web_fetch` 或类似工具读取，然后解析 JSON。每张卡包含：
- `id`, `brand`, `origin`, `era`, `type`, `rarity`, `baseScore`
- `image_url` — ciggies.app 的真实烟盒图片链接
- `ciggies_sku` — ciggies.app 产品 ID

**初始化时**：从 cards.json 随机抽 15 张作为起始牌组。

| File | Content | URL |
|------|---------|-----|
| `cards.json` | 150 cigarette packs | [GitHub Raw](https://raw.githubusercontent.com/tokenfed/ciggatro/main/cards.json) |
| `ashtrays.json` | 50 ashtrays | [GitHub Raw](https://raw.githubusercontent.com/tokenfed/ciggatro/main/ashtrays.json) |
| `lighters.json` | 22 lighter consumables | [GitHub Raw](https://raw.githubusercontent.com/tokenfed/ciggatro/main/lighters.json) |
| `specialties.json` | 12 province specialties | [GitHub Raw](https://raw.githubusercontent.com/tokenfed/ciggatro/main/specialties.json) |
| `smuggled.json` | 18 smuggled goods | [GitHub Raw](https://raw.githubusercontent.com/tokenfed/ciggatro/main/smuggled.json) |
| `licenses.json` | 24 permanent upgrades | [GitHub Raw](https://raw.githubusercontent.com/tokenfed/ciggatro/main/licenses.json) |
| `stages.json` | Stage configurations | [GitHub Raw](https://raw.githubusercontent.com/tokenfed/ciggatro/main/stages.json) |

---

## Initialization

New game setup:
1. Create starter deck (15 random Common/Uncommon)
2. Give starter ashtray (玻璃烟灰缸)
3. Give 1 random lighter
4. Set all province levels to 1
5. Set tickets = 50
6. Shuffle and draw 8

---

## Agent Behavior

1. **Always calculate accurately** - show math
2. **Announce combos AFTER play** - "✨ 三条！×2.5！" (only when cards are played)
3. **Sound effects** - "🔥 *咔嗒* 点烟..."
4. **Track state** - save after changes
5. **Be the dealer** - shuffle, draw, manage
6. **Celebrate wins** - 🎉 emojis
7. **Warn on danger** - low HP, tough boss
8. **NO unsolicited hints** - never suggest combos unless player pays for hint

---

## 💡 Hint System (付费提示)

Player command: `提示` / `hint` / `分析`

**Cost: 5 烟票**

When hint is purchased, show:
- All possible combos in current hand
- Best scoring combination
- Province synergies

**Example output:**
```
💡 花费 5 烟票...

可用 Combo:
• 同乡 ×1.3 → [2][4][5] 云南
• 老乡见老乡 ×2.0 → 打3张云南
• 散烟 → [1][3] 无加成

建议: 出 [2][4][5] 预计 156 分
```

**Rules:**
- Cannot use hint if tickets < 5
- Hint only analyzes current hand, not strategy
- Each hint costs 5 tickets (no discount)

---

*"收藏即命运。每一包都是一次赌注。"*

**CIGGATRO v2.0** — Full Balatro Experience
