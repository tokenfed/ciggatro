# CIGGIES — Game Design Document
### A Balatro-style Roguelike Deckbuilder

**Version:** 0.1.0  
**Date:** 2026-03-05  
**Based on:** [ciggies.app](https://ciggies.app) by [@0x_ultra](https://x.com/0x_ultra)

---

## 📋 Table of Contents

1. [Overview](#1-overview)
2. [Core Loop](#2-core-loop)
3. [Card System](#3-card-system)
4. [Ashtray System (Jokers)](#4-ashtray-system-jokers)
5. [Combo System](#5-combo-system)
6. [Shop & Economy](#6-shop--economy)
7. [Bosses & Stages](#7-bosses--stages)
8. [Collection & Meta-Progression](#8-collection--meta-progression)
9. [Visuals & Audio](#9-visuals--audio)
10. [Technical Specifications](#10-technical-specifications)

---

## 1. Overview

### 1.1 High Concept

**CIGGIES** is a roguelike deckbuilding game themed around Chinese cigarette culture. Players collect cigarette packs, equip ashtrays (passive effects), and combine high-scoring combos to progress through stages.

Inspirations:
- **Balatro** — Core gameplay framework
- **ciggies.app** — Theme, art, data source
- **Chinese Tobacco Culture** — Social aspects, collector culture, regional identity

### 1.2 Key Selling Points

- 🎨 **Authentic Pack Art** — Real cigarette pack designs from ciggies.app
- 🗺️ **Regional Culture** — Each province has unique tobacco styles and bonuses
- 🎰 **Deep Strategy** — Four-dimensional combos: Brand, Origin, Era, Type
- 📦 **Collection-Driven** — Meta-progression system unlocks rare packs

### 1.3 Target Platforms

- Web (Priority — can embed directly into ciggies.app)
- iOS / Android (PWA)
- Steam (Later phase)

### 1.4 Target Audience

- ciggies.app community users
- Balatro players
- Players interested in Chinese culture and collecting
- Smokers and ex-smokers (nostalgia appeal)

---

## 2. Core Loop

```
┌─────────────────────────────────────────────────────┐
│                                                      │
│   Draw → Select → Light Up (Play) → Score → Next    │
│     ↓                                                │
│   Round End → Shop → Buy Packs/Ashtrays → Next Stage│
│     ↓                                                │
│   Boss Stage → Defeat → Unlock Content → Next Chapter│
│                                                      │
└─────────────────────────────────────────────────────┘
```

### 2.1 Single Round Flow

1. **Draw Phase**: Draw 8 cigarette packs from deck to hand
2. **Select Phase**: Choose 1-5 packs to play
3. **Light Up Phase**: Play selected packs, trigger effects
4. **Score Phase**: Calculate combo + ashtray bonuses → Score
5. **Discard Phase**: Optionally discard cards (limited uses)

### 2.2 Win Condition

Each stage has a target score. Reach it within the turn limit to advance.

### 2.3 Lose Conditions

- Run out of turns without reaching target
- Specific boss mechanics cause failure

---

## 3. Card System

### 3.1 Pack Attributes

Each cigarette pack card has these attributes:

| Attribute | Description | Examples |
|-----------|-------------|----------|
| **Brand** | Cigarette brand name | Chunghwa, Yuxi, Yellow Crane Tower |
| **Origin** | Province of production | Shanghai, Yunnan, Hubei |
| **Era** | Design decade | 80s, 90s, 00s, 10s, 20s |
| **Type** | Tobacco type | Flue-cured, Blended, Cigar-style, Slim |
| **Rarity** | Rarity tier | Common→Uncommon→Rare→Epic→Legendary |
| **Base Score** | Base point value | 10-100 |

### 3.2 Rarity System

| Tier | Name | Color | Score Multiplier | Drop Rate | Example Brands |
|------|------|-------|------------------|-----------|----------------|
| ★ | Common | White/Gray | ×1.0 | 45% | Double Happiness, Red Plum, Hatamen, Daqianmen |
| ★★ | Uncommon | Green | ×1.5 | 30% | Liqun, Yunyan, Golden Leaf, Septwolves |
| ★★★ | Rare | Blue | ×2.0 | 15% | Furong Wang, Yuxi, Yellow Crane Tower, Suyan |
| ★★★★ | Epic | Purple | ×3.0 | 8% | Nanjing Slim, Tianye, Lotus |
| ★★★★★ | Legendary | Gold | ×5.0 | 2% | Panda, Grand Chongqiu, Harmony, Soft Chunghwa |

### 3.3 Origin System

Major Chinese tobacco-producing regions, each with unique bonuses:

| Origin | Representative Brands | Special Bonus |
|--------|----------------------|---------------|
| **Yunnan** | Yuxi, Yunyan, Hongta | Flue-cured Kingdom: Flue-cured type +20% |
| **Hunan** | Furong Wang, Baisha | Lotus Land: Same-origin combo +1 tier |
| **Shanghai** | Chunghwa, Double Happiness, Peony | Magic City: Legendary drop rate +10% |
| **Hubei** | Yellow Crane Tower | Famous Tower: Single card max score +15 |
| **Jiangsu** | Suyan, Nanjing | Six Dynasties Capital: Slim type +25% |
| **Guangdong** | Double Happiness, Wuyeshen | Canton: Common base score ×1.3 |
| **Guizhou** | Guiyan | Maotai Country: Random card upgrades every 3 rounds |
| **Zhejiang** | Liqun, Dahongying | Merchant Guild: Shop prices -10% |
| **Fujian** | Septwolves | Hokkien Traders: +5 coins at stage start |
| **Henan** | Golden Leaf, Dihao | Central Plains: Combo tolerance +1 card |

### 3.4 Era System

| Era | Design Style | Special Effect |
|-----|--------------|----------------|
| **80s** | Revolutionary, Industrial | Nostalgia: Consecutive plays +5/card |
| **90s** | Reform Era, Hong Kong Style | Golden Age: Paired with Legendary ×1.5 |
| **00s** | Modern Minimalist | Stable: Immune to negative effects |
| **10s** | National Trend, Slim Style | Contemporary: Slim type +10 extra |
| **20s** | Ultra-minimalist, Eco | Future: Can count as any era |

### 3.5 Tobacco Types

| Type | Flavor Profile | Mechanic Effect |
|------|----------------|-----------------|
| **Flue-cured** | Rich, aromatic | Standard type, no special effect |
| **Blended** | Balanced, smooth | Can form combos with any type |
| **Cigar-style** | Bold, heavy | Single card +30%, but must play solo |
| **Slim** | Light, fashionable | Can play 1 extra card |
| **Capsule** | Variable, fun | Random effect trigger on play |

---

## 4. Ashtray System (Jokers)

Ashtrays = Balatro's Joker cards, providing passive bonuses.

### 4.1 Ashtray Slots

- Starting: 3 slots
- Maximum: 5 slots (unlocked through upgrades)

### 4.2 Ashtray List

#### Common — White Border

| Name | Effect | Flavor Text |
|------|--------|-------------|
| **Glass Ashtray** | +5 base score per round | "Cheap but functional." |
| **Tin Can** | Common rarity +10 score | "The working class choice." |
| **Disposable Paper Cup** | +1 discard | "Temporary solution, permanent habit." |
| **Water Bottle Cap** | +3 score per discard | "Days without an ashtray." |
| **Takeout Box** | Random card +5 score per round | "Late night standard equipment." |

#### Uncommon — Green Border

| Name | Effect | Flavor Text |
|------|--------|-------------|
| **Jingdezhen Blue Porcelain** | Jiangxi origin +15 score | "A thousand years of kiln fire, a wisp of smoke." |
| **Antique Bronze** | 80s/90s era +20% | "Tribute to the golden age." |
| **Stainless Steel Ashtray** | Immune to next negative effect | "Built to last." |
| **Portable Ashtray** | Draw 2 extra cards at stage start | "Ritual on the go." |
| **Mahjong Table Ashtray** | Same origin 4-card ×2 | "Got a full table." |

#### Rare — Blue Border

| Name | Effect | Flavor Text |
|------|--------|-------------|
| **Zippo Lighter** | First light each round ×2 | "The first drag is always the best." |
| **Crystal Ashtray** | Legendary rarity +50 score | "Worthy of the finest." |
| **Executive Desk Ashtray** | Each Rare+ card: all cards +3% | "Boardroom power symbol." |
| **KTV Special** | Night mode: all scores +20% | "Tonight we don't go home sober." |
| **High-Speed Rail Pack** | Slim type can play twice | "Quick fix on the journey." |

#### Epic — Purple Border

| Name | Effect | Flavor Text |
|------|--------|-------------|
| **Veteran Smoker's Lungs** | End of round: each card on field +2 (stacks) | "Can't quit the habit." |
| **Maotai Bottle Cap** | Guizhou origin ×3 | "Good wine, good smokes, good friends." |
| **Panda Ashtray** | Each Legendary: all cards +8% | "Collector's pride." |
| **Vintage Radio** | 80s cards: permanent +1 base when played | "Old songs, old smokes." |
| **Museum Display Case** | After 5 different brands: +100 score | "The curator's satisfaction." |

#### Legendary — Gold Border

| Name | Effect | Flavor Text |
|------|--------|-------------|
| **Great Hall Ashtray** | All Chunghwa brand ×5 | "State banquet tier." |
| **Macau Casino Ashtray** | 50% ×2 / 50% ×0.5 | "Gambling on the rush." |
| **Nicotine Patch** | Play 1 fewer card, but score ×1.5 | "Restraint is its own power." |
| **Time Capsule Pack** | Choose any era as current | "Time stops here." |
| **Tobacco Bureau Seal** | All cards +1 rarity tier | "Wholesale price becomes retail." |

### 4.3 Special Ashtrays (Unlock Conditions)

| Name | Unlock Condition | Effect |
|------|------------------|--------|
| **Collector's Badge** | Total collection reaches 100 | Each unique brand +5 score |
| **Chain Smoker's Lungs** | Play 1000 cards total | All Commons treated as Uncommon |
| **King of Yunnan** | Complete Yunnan collection | Yunnan cards always ×2 |
| **Withdrawal Success** | Clear a run without Legendary cards | Next run starts +3 ashtray slots |

---

## 5. Combo System

### 5.1 Basic Combos (Brand)

| Combo Name | Condition | Multiplier | Description |
|------------|-----------|------------|-------------|
| **Single** | 1 card | ×1 | No bonus |
| **Pair** | Same brand ×2 | ×1.5 | Double down |
| **Three of a Kind** | Same brand ×3 | ×2.5 | Loyal customer |
| **Four of a Kind** | Same brand ×4 | ×4 | Brand devotee |
| **Full Carton** | Same brand ×5 | ×8 | Wholesale bulk |

### 5.2 Origin Combos

| Combo Name | Condition | Multiplier |
|------------|-----------|------------|
| **Neighbors** | Same origin ×2 | ×1.3 |
| **Hometown Reunion** | Same origin ×3 | ×2 |
| **Provincial Team** | Same origin ×4 | ×3 |
| **Province Domination** | Same origin ×5 | ×5 |

### 5.3 Era Combos

| Combo Name | Condition | Multiplier |
|------------|-----------|------------|
| **Same Generation** | Same era ×2 | ×1.2 |
| **Era Show** | Same era ×3 | ×1.8 |
| **Time Capsule** | Same era ×5 | ×3 |
| **Time Travel** | 80s + 20s | ×2.5 |

### 5.4 Type Combos

| Combo Name | Condition | Multiplier |
|------------|-----------|------------|
| **Tobacco Sampler** | 4 different types | ×2 |
| **Slim Squad** | 3 Slims | ×2.5 |
| **Capsule Party** | 2 Capsules | ×2 + random effect |

### 5.5 Special Combos

| Combo Name | Condition | Effect |
|------------|-----------|--------|
| **Grand Slam** | Same brand + origin + era | ×10 |
| **Variety Store** | 5 all different | +50 flat score |
| **Last Cigarette** | Play last card in hand | That card ×3 |
| **Opening Flourish** | First play of round is Legendary | All scores this round +30% |

### 5.6 Combo Stacking Rules

- Brand, Origin, Era, Type combos can stack
- Calculation order: Base score → Type bonus → Combo multiplier → Ashtray bonus
- Formula: `Final Score = Σ(Card Base × Rarity Mult) × Combo Mult × Ashtray Bonus`

---

## 6. Shop & Economy

### 6.1 Currency: Cigarette Tickets

- Earn tickets based on round score
- 1000 score = 10 tickets
- Perfect clear (no discards) = +5 bonus tickets

### 6.2 Shop Contents

After each stage, enter shop to purchase:

| Type | Price Range | Description |
|------|-------------|-------------|
| **Packs** | 5-50 tickets | Add to deck |
| **Ashtrays** | 20-100 tickets | Passive effects |
| **Upgrades** | 30-80 tickets | Permanently enhance a card |
| **Remove** | 15 tickets | Remove a card from deck |
| **Slot** | 100 tickets | +1 ashtray slot |

### 6.3 Upgrade System

Spend tickets to upgrade individual packs:

| Upgrade | Effect | Price |
|---------|--------|-------|
| **Gilded** | Base score +10 | 30 tickets |
| **Holographic** | +10% tickets when scored | 40 tickets |
| **Autographed** | Always appears in opening hand | 50 tickets |
| **Limited Edition** | Rarity +1 tier | 80 tickets |

### 6.4 Special Shops

- **Black Market**: Appears every 3 stages, has Legendary packs but double prices
- **Auction House**: Players bid against each other (multiplayer mode)
- **Smuggler**: Cheap prices but chance of counterfeit (negative effects)

---

## 7. Bosses & Stages

### 7.1 Chapter Structure

**Chapter 1: Beginner (3 stages + Boss)**
- Low target scores, learn basics
- Boss: Smoking Control Officer

**Chapter 2: Intermediate (4 stages + Boss)**
- Introduces origin combos
- Boss: Counterfeit Dealer

**Chapter 3: Advanced (4 stages + Boss)**
- Introduces era combos
- Boss: Customs Bureau

**Chapter 4: Collector (5 stages + Boss)**
- Full integration of all elements
- Boss: Willpower to Quit

**Hidden Chapter: Black Market (Unlock: Complete collection)**
- Extreme difficulty
- Boss: Tobacco Administration

### 7.2 Boss Detailed Design

#### Boss 1: Smoking Control Officer

**Visual**: Middle-aged official with megaphone, "No Smoking" signs in background

**Mechanics**:
- Each round, randomly seals 1 brand (that brand scores 0 this round)
- HP: 2000 points

**Strategy**:
- Build multi-brand decks
- Bring seal-removing ashtrays

**Dialogue**:
- "According to the Public Smoking Control Regulations, you cannot smoke here."
- "I don't make the rules. Orders from above."

---

#### Boss 2: Counterfeit Dealer

**Visual**: Man in sunglasses, warehouse stacked with cigarette boxes behind him

**Mechanics**:
- Each round, 1-2 hand cards become "counterfeits" (negative score)
- Counterfeits look identical to real ones, must spot subtle differences
- HP: 3500 points

**Strategy**:
- Bring authentication ashtrays (can identify fakes)
- Discard more to remove counterfeits

**Dialogue**:
- "Boss, these are authentic. Look at this anti-counterfeit label..."
- "You get what you pay for? No no no, this is channel advantage."

---

#### Boss 3: Customs Bureau

**Visual**: Uniformed customs officer, X-ray machine in background

**Mechanics**:
- Legendary rarity cards are seized, cannot play
- Release 1 card every 2 rounds (but must pay tax: -20 tickets)
- HP: 5000 points

**Strategy**:
- Reduce reliance on Legendary cards
- Or bring extra tickets to cover taxes

**Dialogue**:
- "Please present your declaration form."
- "You've exceeded the duty-free limit. Please proceed to the processing desk."

---

#### Boss 4: Willpower to Quit

**Visual**: Abstract inner world, smoke forming a struggling human figure

**Mechanics**:
- Each card played: next card -10% score (stacks)
- Debuff resets every 3 rounds
- HP: 8000 points

**Strategy**:
- Play fewer cards before reset
- Or go all-in burst damage

**Dialogue**:
- "Do you really need another one?"
- "Think about your lungs."
- "That's already the third pack..."

---

#### Hidden Boss: Tobacco Administration

**Visual**: Massive government building, logo barely visible

**Mechanics**:
- Combines all boss abilities
- Switches mechanism every 5 rounds
- HP: 15000 points

**Strategy**:
- Ultimate test, requires perfect build

**Dialogue**:
- "The market requires regulation."
- "The monopoly system exists for a reason."

---

## 8. Collection & Meta-Progression

### 8.1 Collection System

Linked with ciggies.app — in-game collection = website collection

**Collection Dimensions**:
- By Brand
- By Origin
- By Era
- By Rarity

**Collection Rewards**:
| Milestone | Reward |
|-----------|--------|
| Collect 10 types | Unlock: Jingdezhen Blue Porcelain |
| Collect 50 types | Unlock: Hidden character |
| Collect 100 types | Unlock: Museum Display Case |
| Complete any province | Unlock: Province-specific ashtray |
| Complete all | Unlock: Hidden chapter + "Museum Curator" achievement |

### 8.2 Achievement System

| Achievement | Condition | Reward |
|-------------|-----------|--------|
| First Drag | Complete tutorial | 10 tickets |
| Full Carton | Achieve "Full Carton" combo | Ashtray: Wholesale Discount |
| Counterfeit Expert | Identify 10 fakes in one run | Ashtray: Anti-Fraud Office |
| Quit Successfully | Clear a run without using any cards | ??? |
| Chain Smoker | Play 10,000 cards total | Title + gold border |
| Governor | 100% collection in one province | Province-exclusive skin |
| Curator | Complete collection | Full unlock |

### 8.3 Daily Challenges

- One special-rule stage per day
- Leaderboard competition
- Rewards: Rare tickets, limited ashtrays

### 8.4 Season System

- One new season per month
- Season-exclusive packs (limited-time collection)
- After season ends, packs become "Vintage" category

---

## 9. Visuals & Audio

### 9.1 Art Style

**Overall**:
- Pixel art + Chinese elements
- Main colors: Red, Gold, White
- Font: Pixelated Song/Hei typefaces

**Pack Cards**:
- Use real cigarette pack images from ciggies.app (requires licensing)
- Pixelated processing for unified style
- Rarity indicated by border color

**UI**:
- Red wrapping paper texture
- Gold outlines
- Traditional Chinese pattern accents

### 9.2 Animations

| Animation | Description | Duration |
|-----------|-------------|----------|
| Light Up | Sparks fly → Tip glows → Smoke rises | 0.5s |
| Combo | Packs connect → Explosion effect → Score popup | 0.8s |
| Score | Numbers fly to total + stacking sound | 0.3s |
| Draw | Pack slides from deck + flip | 0.4s |
| Legendary | Golden shimmer + special sound | 1.0s |

### 9.3 Sound Effects

| Scene | Sound Description |
|-------|-------------------|
| Light Up | Lighter "click" + inhale sound |
| Combo | Stacking "ding" chimes |
| High Score | Celebration + crowd cheering |
| Boss Entrance | Deep drums + warning tone |
| Counterfeit | Dissonant "buzz" |
| Shop | Old cash register sound |

### 9.4 Background Music

| Scene | Style |
|-------|-------|
| Main Menu | Nostalgic piano + Lo-fi |
| Gameplay | Upbeat electronic + Chinese instrument samples |
| Boss Battle | Tense drums + Pipa |
| Shop | Relaxed jazz |
| Victory | Festive Suona |

---

## 10. Technical Specifications

### 10.1 Development Framework

**Recommended**:
- **Godot 4** — Open source, lightweight, multi-platform
- or **Phaser.js** — Pure web, easy to embed in ciggies.app

### 10.2 Data Structures

```typescript
interface CigarettePack {
  id: string;
  brand: string;
  brandCN: string;
  origin: Province;
  era: Era;
  type: TobaccoType;
  rarity: Rarity;
  baseScore: number;
  imageUrl: string;
  description: string;
  history?: string;
}

interface Ashtray {
  id: string;
  name: string;
  nameCN: string;
  rarity: Rarity;
  effect: Effect;
  flavorText: string;
  imageUrl: string;
}

interface GameState {
  deck: CigarettePack[];
  hand: CigarettePack[];
  ashtrays: Ashtray[];
  score: number;
  tickets: number;
  round: number;
  chapter: number;
}
```

### 10.3 API Integration

Linked with ciggies.app:
- User login sync
- Two-way collection data sync
- Leaderboard API

### 10.4 Save System

- Local saves (localStorage / IndexedDB)
- Cloud saves (via ciggies.app account)
- Encrypted saves for anti-cheat

### 10.5 Performance Targets

| Metric | Target |
|--------|--------|
| First Load | < 3s |
| Animation FPS | 60 FPS |
| Memory Usage | < 200 MB |
| Install Size | < 50 MB |

---

## Appendix

### A. Brand Data Source

Brand data from ciggies.app. Requires licensing confirmation with @0x_ultra.

### B. Reference Games

- **Balatro** — Core gameplay framework
- **Slay the Spire** — Roguelike progression design
- **Showa Candy Shop** — Nostalgic collection feel

### C. Version Roadmap

| Version | Content | Est. Time |
|---------|---------|-----------|
| 0.1 (MVP) | Core loop + 50 packs + 10 ashtrays | 4 weeks |
| 0.5 (Alpha) | Full Chapter 1 + shop + collection | 8 weeks |
| 1.0 (Release) | Full content + balance tuning | 16 weeks |
| 1.x | Season content, events, collaborations | Ongoing |

---

*"To collect is to gamble with fate. Every pack is a bet."*

**CIGGIES** — A game by ciggies.app

---

Document Version: 0.1.0 (English)  
Last Updated: 2026-03-05
