# 🚬 CIGGATRO

**[中文](README-CN.md) | [日本語](README-JA.md)**

A Balatro-style roguelike deckbuilder themed around Chinese cigarettes. Play entirely through text with any AI assistant.

Based on [ciggies.app](https://ciggies.app) — Chinese Cigarette Museum by [@0x_ultra](https://x.com/0x_ultra).

## 🎮 How to Play

Feed this skill to your AI assistant (Claude, GPT, etc.) and say:

| Language | Trigger |
|----------|---------|
| 中文 | `玩烟牌` / `开始游戏` / `ciggatro cn` |
| English | `play ciggatro` / `start game` / `ciggatro en` |
| 日本語 | `タバコゲーム` / `遊ぶ` / `ciggatro ja` |

## 📦 What's Included

- `SKILL.md` — Game rules and display formats (feed this to your AI)
- `cards.json` — 150 cigarette pack cards with real images from ciggies.app
- `ashtrays.json` — 50 passive bonus effects (like Jokers in Balatro)
- `lighters.json` — 22 consumable items
- `specialties.json` — 12 province specialty cards
- `smuggled.json` — 18 rare powerful consumables
- `licenses.json` — 24 permanent upgrades
- `stages.json` — 4 chapters + hidden chapter with bosses

## 🃏 Game Mechanics

### Card Types (Balatro Mapping)
| CIGGATRO | Balatro | Function |
|----------|---------|----------|
| 🚬 烟盒 Packs | Playing Cards | Main cards, make combos |
| 🏺 烟灰缸 Ashtrays | Jokers | Passive bonuses |
| 🔥 打火机 Lighters | Tarot | Modify cards |
| 🗺️ 特产卡 Specialties | Planet | Level up provinces |
| 📦 走私品 Smuggled | Spectral | Rare consumables |
| 📜 许可证 Licenses | Vouchers | Permanent upgrades |

### Combo Dimensions
- **Brand** — 中华, 玉溪, 芙蓉王... (same brand = multiplier)
- **Province** — 云南, 上海, 湖北... (same origin = multiplier)
- **Era** — 80s, 90s, 00s, 10s, 20s
- **Rarity** — ★ to ★★★★★

## 🖼️ Images

All cigarette pack images are loaded from ciggies.app CDN:
```
https://www.ciggies.app/api/img/products/{sku}-0-128.webp
```

## 📖 Design Documents

- [GDD 中文版](GDD-CN.md)
- [GDD English](GDD-EN.md)
- [GDD 日本語](GDD-JA.md)

## 📜 License

Game design and code: MIT License

Cigarette images and data: © [ciggies.app](https://ciggies.app)

## 🙏 Credits

- [@0x_ultra](https://x.com/0x_ultra) — ciggies.app creator
- Inspired by [Balatro](https://www.playbalatro.com/) by LocalThunk
