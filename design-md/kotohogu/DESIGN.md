# DESIGN.md — KOTOHOGU

> KOTOHOGU（https://kanata-kotohogu.vercel.app/）のデザイン仕様書。
> KANATA一般社団法人が運営する、若手プロフェッショナルと社会をつなぐ福祉プラットフォーム。
> サイト構成・テキスト内容に基づくデザイントークン推定値（2026-04-06）。

---

## 1. Visual Theme & Atmosphere

- **デザイン方針**: あたたかく信頼感のあるソーシャルデザイン。余白を活かしたクリーンなレイアウトにやさしいトーンの色彩を組み合わせ、福祉×テクノロジーの融合を表現
- **密度**: ゆったり。1セクション=1メッセージの大きな構成。スクロールで物語が展開するストーリーテリング型
- **キーワード**: やさしい、信頼、架け橋、あたたかい、プロフェッショナル、つながり

---

## 2. Color Palette & Roles

### Primary（ブランドカラー）

- **Primary** (`#6B8F71`): やさしいグリーン。自然・成長・福祉を象徴。CTAボタン、アクセントに使用
- **Primary Dark** (`#4A6B50`): ホバー・プレス時のプライマリカラー
- **Primary Light** (`#E8F0E9`): 背景のアクセント、カードの薄い背景

### Secondary

- **Warm Beige** (`#F5F0EB`): あたたかみのある背景色。セクション背景の交互使用
- **Soft Gold** (`#C4A265`): アクセント。番号ラベル、装飾要素

### Semantic（意味的な色）

- **Danger** (`#D64545`): エラー、削除、危険な操作
- **Warning** (`#E6A23C`): 警告、注意喚起
- **Success** (`#6B8F71`): 成功、完了（Primary と共用）

### Neutral（ニュートラル）

- **Text Primary** (`#2D2D2D`): 本文テキスト。純黒を避けた柔らかいダークグレー
- **Text Secondary** (`#6B7280`): 補足テキスト、ラベル、キャプション
- **Text Light** (`#9CA3AF`): プレースホルダー、無効状態
- **Border** (`#E5E7EB`): 区切り線、カード枠
- **Background** (`#FFFFFF`): メイン背景
- **Surface** (`#FAFAFA`): カード、セクション背景
- **Dark BG** (`#1A1A2E`): ダークセクション背景（SOCIAL IMPACT等）

---

## 3. Typography Rules

### 3.1 和文フォント

- **Noto Sans JP**: Google Fonts。本文・UI テキストに使用。Weight 300〜700
- **Noto Serif JP**: Google Fonts。ビジョンステートメント・引用・強調見出しに使用。品格と温かみを両立

### 3.2 欧文フォント

- **Inter**: Google Fonts。セクションラベル（"VISION", "BRIDGE" 等）の欧文見出し用。Weight 400〜800
- **Noto Sans JP 内蔵欧文グリフ**: 本文中の英数字

### 3.3 font-family 指定

```css
/* 本文・UI */
font-family: "Noto Sans JP", "Hiragino Kaku Gothic ProN", "Yu Gothic", "Meiryo", sans-serif;

/* ビジョン・引用 */
font-family: "Noto Serif JP", "Hiragino Mincho ProN", "Yu Mincho", serif;

/* 欧文ラベル（セクションタイトル） */
font-family: "Inter", "Helvetica Neue", Arial, sans-serif;
```

**フォールバックの考え方**:
- 和文ゴシック → Noto Sans JP 優先、ヒラギノ・游ゴシック・メイリオで OS カバー
- 和文明朝 → Noto Serif JP 優先、ヒラギノ明朝・游明朝でフォールバック
- 欧文ラベル → Inter 優先（幾何学的で現代的な印象）

### 3.4 文字サイズ・ウェイト階層

| Role | Font | Size | Weight | Line Height | Letter Spacing | 備考 |
|------|------|------|--------|-------------|----------------|------|
| Display | Noto Serif JP | 48px | 700 | 1.3 | 0.02em | ヒーローキャッチコピー |
| Section Label | Inter | 14px | 700 | 1.0 | 0.15em | "VISION", "BRIDGE" 等の英語ラベル |
| Heading 1 | Noto Serif JP | 36px | 600 | 1.4 | 0.02em | セクション見出し |
| Heading 2 | Noto Sans JP | 24px | 700 | 1.5 | 0.04em | サブ見出し |
| Heading 3 | Noto Sans JP | 20px | 600 | 1.5 | 0.04em | カード見出し |
| Body | Noto Sans JP | 16px | 400 | 1.8 | 0.04em | 本文 |
| Body Small | Noto Sans JP | 14px | 400 | 1.7 | 0.04em | 補足テキスト |
| Caption | Noto Sans JP | 12px | 400 | 1.6 | 0.02em | 注釈、フッター |
| Number | Inter | 48px | 800 | 1.0 | 0 | "01", "02", "3x" 等の数字強調 |

### 3.5 行間・字間

**行間 (line-height)**:
- Display 見出し: `1.3` — やや詰め（改行で意味のまとまりを作る）
- セクション見出し: `1.4` — 読みやすさと凝縮感のバランス
- 本文: `1.8` — 日本語に適したゆったりとした行間
- 欧文ラベル: `1.0` — タイトに

**字間 (letter-spacing)**:
- 欧文ラベル: `0.15em` — トラッキング広め（"VISION" 等を大文字で開く）
- 和文見出し: `0.02em` — わずかに開く
- 和文本文: `0.04em` — 可読性向上のための微字間
- 数字: `0` — そのまま

### 3.6 禁則処理・改行ルール

```css
word-break: keep-all;
overflow-wrap: break-word;
line-break: strict;
```

**禁則対象**:
- 行頭禁止: `）」』】〕〉》」】、。，．・：；？！`
- 行末禁止: `（「『【〔〈《「【`

### 3.7 OpenType 機能

```css
font-feature-settings: "palt" 1, "kern" 1;
```

- **palt**: 見出し・ナビゲーションに適用（プロポーショナル字詰め）
- **kern**: 欧文カーニング。和欧混植時に有効
- 本文には `palt` を適用しない（等幅の方が可読性が高い）

### 3.8 縦書き

- 該当なし

---

## 4. Component Stylings

### Buttons

**Primary（"参加する", "プロフェッショナル登録"）**
- Background: `#6B8F71`
- Text: `#FFFFFF`
- Padding: 16px 32px
- Border Radius: 8px
- Font Size: 16px
- Font Weight: 600
- Font: Noto Sans JP
- Hover: Background `#4A6B50`

**Secondary（"仕組みを知る", "施設・個人のお問い合わせ"）**
- Background: `transparent`
- Text: `#6B8F71`
- Border: 1.5px solid `#6B8F71`
- Padding: 16px 32px
- Border Radius: 8px
- Font Size: 16px
- Font Weight: 600
- Hover: Background `#E8F0E9`

### Cards（3つの価値・エコシステム）

- Background: `#FFFFFF`
- Border: 1px solid `#E5E7EB`
- Border Radius: 12px
- Padding: 32px
- Shadow: `0 2px 8px rgba(0,0,0,0.06)`
- Hover Shadow: `0 4px 16px rgba(0,0,0,0.1)`

### Number Badge（"01", "02", "03"）

- Font: Inter
- Size: 48px
- Weight: 800
- Color: `#C4A265`（Soft Gold）
- Opacity: 0.3（装飾的に薄く表示）

---

## 5. Layout Principles

### Spacing Scale

| Token | Value |
|-------|-------|
| XS | 4px |
| S | 8px |
| M | 16px |
| L | 24px |
| XL | 40px |
| XXL | 64px |
| XXXL | 96px |

### Container

- Max Width: 1200px
- Padding (horizontal): 24px（モバイル）/ 40px（デスクトップ）

### Grid

- Columns: 12
- Gutter: 24px
- カード並び: 2〜3カラムが基本

---

## 6. Depth & Elevation

| Level | Shadow | 用途 |
|-------|--------|------|
| 0 | none | フラットな要素 |
| 1 | `0 2px 8px rgba(0,0,0,0.06)` | カード、セクション |
| 2 | `0 4px 16px rgba(0,0,0,0.1)` | ホバー時のカード |
| 3 | `0 8px 24px rgba(0,0,0,0.15)` | モーダル、フローティング |

---

## 7. Do's and Don'ts

### Do（推奨）

- 和文明朝体（Noto Serif JP）を見出しに使い、品格を出す
- プライマリグリーン `#6B8F71` を控えめに、アクセントとして使う
- 余白を十分にとり、呼吸感のあるレイアウトにする
- 英語セクションラベルは大文字＋広い letter-spacing で配置する
- カードは角丸12px、薄い影でやさしい印象を保つ
- テキストは `#2D2D2D`（純黒を避ける）で柔らかいコントラストにする

### Don't（禁止）

- 純黒 `#000000` をテキストに使わない（コントラストが強すぎる）
- プライマリグリーンを蛍光色に変えない（やさしさが失われる）
- 太すぎるボーダーや強い影を使わない（圧迫感が出る）
- 欧文ラベルを小文字で書かない（セクションラベルは常に大文字）
- 装飾的な数字に目立つ色を使わない（控えめなゴールド/薄い不透明度で）
- 明朝体を本文に使わない（見出し・ビジョンステートメント専用）

---

## 8. Responsive Behavior

### Breakpoints

| Name | Width | 説明 |
|------|-------|------|
| Mobile | ≤ 640px | 1カラム、フォントサイズ縮小 |
| Tablet | ≤ 1024px | 2カラム |
| Desktop | > 1024px | フルレイアウト |

### タッチターゲット

- 最小サイズ: 44px × 44px（WCAG基準）

### フォントサイズの調整

- モバイル: Display 32px / H1 28px / Body 15px
- タブレット: Display 40px / H1 32px / Body 16px

### A4 印刷対応

- 印刷サイズ: 210mm × 297mm（A4）
- 印刷用フォントサイズ: 見出し 24pt / 本文 10pt
- 塗り足し: 3mm

---

## 9. Agent Prompt Guide

### クイックリファレンス

```
Primary Green: #6B8F71
Primary Dark: #4A6B50
Primary Light: #E8F0E9
Warm Beige: #F5F0EB
Soft Gold: #C4A265
Text Primary: #2D2D2D
Text Secondary: #6B7280
Background: #FFFFFF
Dark BG: #1A1A2E
Border: #E5E7EB

JP Gothic: "Noto Sans JP", sans-serif (body/UI)
JP Serif: "Noto Serif JP", serif (headings/vision)
EN Label: "Inter", sans-serif (section labels)

Body: 16px / weight: 400 / line-height: 1.8 / letter-spacing: 0.04em
Heading: 36px / Noto Serif JP / weight: 600 / line-height: 1.4
Section Label: 14px / Inter / weight: 700 / letter-spacing: 0.15em / uppercase
Button Radius: 8px
Card Radius: 12px
```

### プロンプト例

```
KOTOHOGUのデザインに従って、A4チラシを作成してください。
- 見出しフォント: "Noto Serif JP", serif（weight 600〜700）
- 本文フォント: "Noto Sans JP", sans-serif（weight 400）
- 英語ラベル: "Inter", sans-serif（大文字、letter-spacing: 0.15em）
- ブランドカラー: #6B8F71（やさしいグリーン）
- 背景: #FFFFFF / セクション背景: #F5F0EB（Warm Beige）
- テキスト色: #2D2D2D（純黒を避ける）
- 余白を十分にとり、呼吸感のあるレイアウト
- カード: 角丸12px、薄い影
- ボタン: 角丸8px、グリーン背景 or グリーン枠線
- 全体にやさしく信頼感のある印象
```
