---
name: 洲遊幣 Lite · InterCoins
description: 五星飯店質感的中秋蒐幣抽獎轉盤——壓印紙上燙金箔的行動遊戲介面
colors:
  gilt-gold: "#935D08"
  foil-bright: "#C99A3B"
  foil-line: "#B8860B"
  stamped-paper: "#EDEBE6"
  silk-surface: "#F5F3EE"
  ink: "#2B2620"
  stone-ink: "#6B665B"
  seal-red: "#B4471F"
  pill-gold-hi: "#F6D989"
  pill-gold-lo: "#DCA948"
  deep-bronze-text: "#5A3A08"
  night-panel: "#2B2620"
  moon-gold: "#F4D489"
typography:
  display:
    fontFamily: "Cormorant Garamond, Georgia, serif"
    fontSize: "19px–25px"
    fontWeight: 700
    lineHeight: 1
    letterSpacing: "0.08em"
  headline:
    fontFamily: "Noto Serif TC, serif"
    fontSize: "28px"
    fontWeight: 700
    lineHeight: 1.2
  title:
    fontFamily: "Noto Serif TC, serif"
    fontSize: "15px–19px"
    fontWeight: 600
    letterSpacing: "0.05em–0.12em"
  body:
    fontFamily: "Inter, system-ui, sans-serif"
    fontSize: "12px–15px"
    fontWeight: 400
    lineHeight: 1.6
  label:
    fontFamily: "Noto Serif TC, serif"
    fontSize: "12px–13px"
    fontWeight: 600
    letterSpacing: "0.04em–0.1em"
rounded:
  input: "10px"
  button: "12px"
  card: "14px"
  sheet: "22px"
  pill: "999px"
spacing:
  xs: "4px"
  sm: "9px"
  md: "12px"
  lg: "16px"
  gutter: "18px"
  section: "24px"
components:
  button-cta:
    backgroundColor: "linear-gradient(180deg, {colors.foil-bright}, #9C6410)"
    textColor: "#FFFFFF"
    typography: "{typography.title}"
    rounded: "{rounded.card}"
    padding: "16px"
  button-draw-pill:
    backgroundColor: "linear-gradient(180deg, {colors.pill-gold-hi}, {colors.pill-gold-lo})"
    textColor: "{colors.deep-bronze-text}"
    rounded: "{rounded.pill}"
    padding: "11px 22px"
  card-gold-task:
    backgroundColor: "linear-gradient(180deg, #FBEECB, #E6C877)"
    textColor: "{colors.deep-bronze-text}"
    rounded: "{rounded.card}"
    padding: "12px"
  card-result:
    backgroundColor: "{colors.silk-surface}"
    textColor: "{colors.ink}"
    rounded: "{rounded.sheet}"
    padding: "28px 24px"
  input-field:
    backgroundColor: "#FFFFFF"
    textColor: "{colors.ink}"
    rounded: "{rounded.input}"
    padding: "10px 12px"
  pill-balance:
    backgroundColor: "{colors.silk-surface}"
    textColor: "{colors.gilt-gold}"
    rounded: "{rounded.pill}"
    padding: "5px 12px 5px 6px"
---

# Design System: 洲遊幣 Lite · InterCoins

## 1. Overview

**Creative North Star: 「燙金月餅禮盒」（The Gilt Gift Box）**

整個介面是一只五星飯店送出的中秋禮盒：壓印紙紋做底、金箔燙印做飾、禮賓員語氣做聲音。每一個表面都要撐得起 PRODUCT.md 的那句話——「質感即信任」。視覺主體是六層同心燙金轉盤（金／銀／銅三套等級盤面），UI chrome 退居襯托：低彩度的紙面、絹面卡片、以及只在「儀式時刻」（投幣、旋轉、開獎）才放大的動畫投資。

本系統明確拒絕（引 PRODUCT.md 反參照）：「制式電商活動頁——高彩度紅黃、硬推銷橫幅的雙 11 風」、「廉價手遊抽獎風——螢光色、爆炸貼紙、倒數計時壓迫感」、「過度嚴肅冰冷的企業官網風」。奢華為骨、玩心為點綴；先典雅，再俏皮。

**Key Characteristics:**
- 壓印紙底 × 燙金箔飾：材質感由真實分層美術（1920² PNG）承載，不靠 CSS 特效模擬
- 單手直立手機、單屏鎖定（轉盤釘底出血是刻意的固定比例，不是裁切錯誤）
- 三個儀式時刻（投幣／旋轉／開獎）動畫加倍投資，其餘保持安靜
- 全獎盤：每格都是獎，不存在「銘謝惠顧」的品牌傷害時刻

## 2. Colors

低彩度紙金系：紙是舞台，金是聲音，墨是內容。

### Primary
- **Gilt Gold 深燙金** (#935D08)：品牌主色。小字金（跑馬燈、提示、瀏覽獎品）、按鈕底、勾選框 accent。此值經 WCAG 驗算（≥4.6:1 於兩種底色），是「還看得清楚的燙金」下限——不得再調亮。
- **Foil Bright 金箔亮** (#C99A3B)：漸層亮端、focus 圈、發光效果。只做裝飾與狀態，不做內文。
- **Foil Line 金線** (#B8860B)：細線、邊框、轉盤獎品字的基準金。

### Secondary
- **Pill Gold（#F6D989 → #DCA948）＋ Deep Bronze Text (#5A3A08)**：「可行動的金」——抽獎浮鈕與金色任務卡專用組合（7.4:1）。與 Primary 的分工：深金底白字＝主 CTA；亮金底深棕字＝浮動行動與獎勵卡。

### Tertiary
- **Seal Red 印泥紅** (#B4471F)：僅保留給錯誤／危險。目前介面幾乎不出現，稀有即警示。
- **Moon Gold 月光金** (#F4D489)：深色面板（訪客閘門、獎勵層）上的金字。

### Neutral
- **Stamped Paper 壓印紙** (#EDEBE6)：頁面底。上面永遠鋪 bg.png 紙紋，禁止裸色塊。
- **Silk Surface 絹面** (#F5F3EE)：卡片、彈窗、膠囊底。
- **Ink 墨** (#2B2620)：主要內文（13.5:1）。
- **Stone Ink 石墨** (#6B665B)：次要小字。此值是 4.8:1 驗算結果——**禁止回退到舊值 #8A8477**（3.1:1，已淘汰）。

### Named Rules
**The Foil-Is-Earned Rule.** 金色漸層與發光只出現在「可行動」或「儀式時刻」的元素上（CTA、浮鈕、獎勵卡、開獎轉場）。靜態資訊不鍍金——金一旦到處都是，就不再是燙金。
**The Contrast Floor Rule.** 內文與資訊性小字一律 ≥4.5:1（#6B665B／#935D08 是已驗算下限）；只有純裝飾的盤面美術字允許例外（≥3:1，大字）。

## 3. Typography

**Display Font:** Cormorant Garamond（fallback Georgia, serif）— 數字與拉丁字專用
**Body Font:** Noto Serif TC（serif）— 中文標題、按鈕、儀式文案
**Label Font:** Inter（system-ui, sans-serif）— 表單、法務條款、註記

**Character:** 中文明體承擔「飯店禮賓」的溫潤儀式感；Cormorant 只負責數字與 InterCoins 標字的古典氣質；Inter 處理必須極度清楚的功能文字。三者分工嚴格，不互相客串。

### Hierarchy
- **Display**（700、19–25px、tracking 0.08em）：餘額數字、InterCoins 標字、等級數字。
- **Headline**（Noto Serif TC 700、28px）：開獎彈窗獎品名——全介面最大的中文字，只給獎品。
- **Title**（Noto Serif TC 600–700、15–19px、tracking 0.05–0.12em）：CTA、卡片標題、彈窗標籤（「恭 喜 中 獎」全形空格拉字距是本系統的儀式簽名）。
- **Body**（Inter 400、12–15px、line-height 1.6）：表單、條款（**12px 是下限**，法務文字不得再縮）。
- **Label**（Noto Serif TC 600、12–13px）：提示、跑馬燈、狀態小字。

### Named Rules
**The Ceremony Spacing Rule.** 儀式性標籤用全形空格分字（恭 喜 中 獎／填 寫 個 人 資 料），僅限四～六字的彈窗標籤；內文禁止。

## 4. Elevation

混合策略：紙面上的元素用**柔和環境影**表達「放在紙上」，儀式元素用**金色光暈**表達「發著光」。無硬邊框陰影、無玻璃擬態。

### Shadow Vocabulary
- **Ambient**（`0 6px 24px rgba(43,38,32,.14)`，token `--shadow`）：卡片、膠囊的預設紙上影。
- **Gold Glow**（`0 6px 18px rgba(161,98,7,.4~.5)`）：CTA 與抽獎浮鈕專用——影子本身帶金，是「可行動的金」的一部分。
- **Sheet**（`0 20px 50px rgba(0,0,0,.4)`）：開獎／表單彈窗，儀式時刻的最重投影。

### Named Rules
**The Glow-Means-Go Rule.** 帶金色的陰影＝可點擊的邀請。灰影元素不承諾互動。

## 5. Components

### Buttons
- **Shape:** 主 CTA 圓角卡（14px）；浮動行動鈕全膠囊（999px）。
- **Primary（智慧 CTA）:** 深金漸層（#C99A3B→#9C6410）白字 19px、tracking 0.12em；永遠可按，文案隨狀態切換（去賺幣→投幣→開始抽獎→抽獎中…）。**禁止長期 disabled 灰態**——灰色巨鈕是已修復的反面教材。
- **Draw Pill（抽獎浮鈕）:** 亮金漸層＋深棕字，浮在投幣口上方 8px，idle 浮動動畫 1.6s；disabled 時灰漸層＋#5F5A4F 字（仍 4.5:1）。
- **Hover / Focus:** `:active` scale(.96–.98)；鍵盤 `:focus-visible` 一律 2px #C99A3B 外圈（offset 2px）。

### Chips
- **Balance Pill:** 絹面底＋金幣圖＋Cormorant 數字；金細框（rgba(147,93,8,.28)）。
- **Winticker（跑馬燈）:** 半透明絹面膠囊，金色 serif 12px，4 秒輪播、進場上浮 0.5s。

### Cards / Containers
- **Corner Style:** 資訊卡 14px；彈窗卡 22px。
- **Gold Task Card:** 亮金漸層（#FBEECB→#E6C877）＋深棕字＋cardPulse 呼吸光；只給「會給你洲遊幣」的入口。
- **Border:** 一律 1px 金色低透明（rgba(147,93,8,.18~.5)）；**禁止側邊粗色條**。
- **Internal Padding:** 12–16px；彈窗 28/24px。

### Inputs / Fields
- **Style:** 白底、1px 金框（rgba 0.3）、10px 圓角、15px Inter。
- **Focus:** 邊框轉實金＋鍵盤外圈；**禁止 outline:none 裸奔**。
- **Error:** toast（role=status）＋focus 回到出錯欄位；訊息說格式（「手機格式：09 開頭共 10 碼」），不說「輸入無效」。

### Navigation
- 單層雙屏（轉盤⇄任務中心）：文字返回鈕「‹ 返回」15px serif 金字；無 tab bar、無漢堡。

### 轉盤（Signature Component）
六層同心 1920² PNG（bg／tier／orbit／plate／dome）＋SVG 獎牌式金字（字腳朝圓心、與獎項盤連動旋轉）。三等級三套盤面：金 L1／銀 L2／銅 L3，切換走 0.5s 發光轉場。舞台釘底出血（`--stage-h: min(73vw, 314px)`）是固定比例設計。等級章可點切換，首訪顯示「↑ 點徽章切換獎項等級」引導膠囊（點過即永久收起）。旋轉引擎 rAF：常態 8°/s 慢轉，抽獎疊加 easeOutCubic 5.4s 收在中獎格。

## 6. Do's and Don'ts

### Do:
- **Do** 讓每一枚洲遊幣的獲得與投入都有即時回饋（震動＋吞幣＋閃光）——「低門檻高回饋」是產品原則。
- **Do** 在三個儀式時刻（投幣、旋轉、開獎）加倍動畫投資；其餘介面保持安靜。
- **Do** 用已驗算的對比色值：#6B665B（次要字）、#935D08（金字）、12px（法務字下限）。
- **Do** 為每個動畫提供 `prefers-reduced-motion` 替代（含浮動、光暈、脈動）。
- **Do** 保持全獎盤——每一格都是獎；虛擬獎（洲遊幣 +N）直接入帳並明說「已存入你的錢包」。

### Don't:
- **Don't** 做成「制式電商活動頁」：高彩度紅黃、硬推銷橫幅、雙 11 風（PRODUCT.md 反參照原文）。
- **Don't** 做成「廉價手遊抽獎風」：螢光色、爆炸貼紙、倒數計時壓迫感。
- **Don't** 冷到像「飯店官網的企業風」——禮賓員會陪你玩，不會板著臉。
- **Don't** 使用 #8A8477 舊灰或任何 <4.5:1 的內文色；不縮法務條款字級到 12px 以下。
- **Don't** 讓主 CTA 停在灰色 disabled 態——永遠給使用者「下一步」。
- **Don't** 出現「銘謝惠顧／再接再厲」或對輸局說「恭喜中獎」；不給虛擬獎發兌換碼。
- **Don't** 側邊粗色條、gradient text、玻璃擬態、bounce 彈跳新增動畫（既有兩處輕微 overshoot 是歷史特例，不再擴散）。