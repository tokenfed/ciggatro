# 🚬 CIGGATRO（シガトロ）

Balatro風ローグライクデッキビルダー、中国タバコがテーマ。テキストベースで、任意のAIアシスタントでプレイ可能。

[ciggies.app](https://ciggies.app)（中国タバコ博物館）をベースに、[@0x_ultra](https://x.com/0x_ultra) 制作。

## 🎮 遊び方

このskillをAIアシスタント（Claude、GPTなど）に読み込ませて、以下を入力：

| 言語 | トリガー |
|----------|---------|
| 中文 | `玩烟牌` / `开始游戏` / `ciggatro cn` |
| English | `play ciggatro` / `start game` / `ciggatro en` |
| 日本語 | `タバコゲーム` / `遊ぶ` / `ciggatro ja` |

## 📦 ファイル内容

- `SKILL.md` — ゲームルールと表示フォーマット（AIに読み込ませるメインファイル）
- `cards.json` — 150枚のタバコパックカード、ciggies.appの実画像付き
- `ashtrays.json` — 50個のパッシブ効果（Balatraのジョーカー相当）
- `lighters.json` — 22個の消耗品
- `specialties.json` — 12個の省特産カード
- `smuggled.json` — 18個のレア強力消耗品
- `licenses.json` — 24個の永久アップグレード
- `stages.json` — 4チャプター + 隠しチャプター + ボス

## 🃏 ゲームメカニクス

### カードタイプ（Balatro対応）
| CIGGATRO | Balatro | 機能 |
|----------|---------|----------|
| 🚬 タバコパック | トランプ | メインカード、コンボを作る |
| 🏺 灰皿 | ジョーカー | パッシブボーナス |
| 🔥 ライター | タロット | カードを改造 |
| 🗺️ 特産カード | プラネット | 省をレベルアップ |
| 📦 密輸品 | スペクトラル | レア消耗品 |
| 📜 ライセンス | バウチャー | 永久アップグレード |

### コンボ軸
- **ブランド** — 中華、玉溪、芙蓉王...（同ブランド = 倍率）
- **産地** — 雲南、上海、湖北...（同省 = 倍率）
- **年代** — 80s、90s、00s、10s、20s
- **レアリティ** — ★ から ★★★★★

## 🖼️ 画像

全タバコパック画像はciggies.app CDNから読み込み：
```
https://www.ciggies.app/api/img/products/{sku}-0-128.webp
```

## 📖 設計ドキュメント

- [GDD 中文版](GDD-CN.md)
- [GDD English](GDD-EN.md)
- [GDD 日本語](GDD-JA.md)

## 📜 ライセンス

ゲームデザインとコード：MIT License

タバコ画像とデータ：© [ciggies.app](https://ciggies.app)

## 🙏 クレジット

- [@0x_ultra](https://x.com/0x_ultra) — ciggies.app クリエイター
- インスピレーション：[Balatro](https://www.playbalatro.com/) by LocalThunk
