---
target: prototype/index.html
total_score: 19
p0_count: 2
p1_count: 3
timestamp: 2026-07-18T10-38-36Z
slug: prototype-index-html
---
Method: dual-agent (A: design-review · B: detector+browser)

## Design Health Score

| # | Heuristic | Score | Key Issue |
|---|-----------|-------|-----------|
| 1 | 系統狀態可見性 | 2 | 三個計數器矛盾（頂部餘額5／您有0枚／已投入5）；旋轉中無「抽獎中…」狀態 |
| 2 | 貼近真實世界 | 3 | 投幣/轉盤隱喻強；但餘額「1」與等級章羅馬數字 I 外觀相同易混淆 |
| 3 | 使用者控制與自由 | 2 | 個資表單無關閉鈕；已投入幣不可收回；「歸零」無確認 |
| 4 | 一致性與標準 | 2 | 頂部 spin-btn 與浮動 draw-btn 功能相同文案不同；金卡樣式同、行為不同 |
| 5 | 錯誤預防 | 3 | 投1枚確認彈窗是亮點；但空白表單可送出領幣、旋轉中刷新＝扣幣無獎 |
| 6 | 辨識而非回憶 | 1 | 點等級章切換「完全不可發現」——#tier-hint 提示膠囊是死 CSS，DOM/JS 從未建立 |
| 7 | 彈性與效率 | 2 | 投5枚要重複5次；無「全部投入」；無鍵盤路徑 |
| 8 | 美學與極簡 | 2 | 資產精美，但高屏中段約 300px 死空白、disabled 灰巨型 CTA 佔最顯眼位 |
| 9 | 錯誤辨識與復原 | 1 | 抽到「銘謝惠顧」仍彈「恭喜中獎＋兌換碼＋請至櫃台核銷」——輸局假慶祝 |
| 10 | 說明與文件 | 1 | 文案引用「詳見活動規則」但規則頁不存在；無玩法/兌獎說明 |
| **Total** | | **19/40** | **Poor — 核心體驗有結構性缺陷，一流資產掩蓋不了** |

## Anti-Patterns Verdict

**LLM 評估**：不會被說「AI 做的」——燙金分層轉盤（金/銀/銅三套盤面）、壓印紙紋、訂製金幣是真正的手工視覺，通過「五星飯店辦的活動」門檻。洩底的是 UI chrome：灰色 disabled 巨型 CTA、高屏中段死空白、右下「歸零」除錯鈕、Cormorant+Inter（reflex-reject 名單字體）——讀起來是「工程師原型感」而非 AI 感。

**偵測器（deterministic）**：CLI 4 筆（overused-font:Inter、bounce-easing ×2、em-dash ×64）；頁內注入 33 筆（warning 26／advisory 7）：tiny-text ×12（條款區 11px）、金邊細框+柔影 ×7（advisory）、bounce-easing ×4、clipped-overflow ×3、low-contrast ×2（stack-label 3.1:1、need-hint 4.1:1）、wide-tracking、skipped-heading（h1→h6）、gradient-text、nested-cards（winticker）各 ×1。

**誤判**：em-dash＝中文正規標點；gradient-text＋金邊柔影＝刻意燙金工藝；overused-font 部分誤判（中文走 CJK 字型）。**兩邊交集**：低對比 muted 小字、11px 條款字、可發現性問題。**偵測器補抓**：skipped-heading、nested-cards、隱藏 modal 內 tiny-text。

**視覺 overlay**：本 session 僅 headless，無使用者可見 overlay（fallback：注入偵測成功、console 證據已收）。

## Overall Impression

視覺資產是真五星（銅盤面尤美），互動骨架也對（投幣儀式、確認彈窗）；但「獎品是真的」這條信念階梯在程式層是斷的（洲遊幣+N 不入帳、輸局假慶祝、假跑馬燈、前端亂數兌換碼），а11y 層面鍵盤/報讀者無法遊玩。最大機會：把工程原型 chrome 修掉，讓輸局變成品牌時刻。

## What's Working

1. **燙金分層轉盤系統**：五層同心＋SVG 獎牌式金字隨盤連動，金/銀/銅三等級切換發光轉場——撐得起「質感即信任」。
2. **投 1 枚確認彈窗**：「確定抽三等獎／再想想」＋升級誘導，錯誤預防＋轉換＋禮賓語氣三合一。
3. **個資告知合規完整度**：雙蒐集者獨立勾選、目的代碼、國際傳輸、獨立撤回、「不同意仍可參加」——遠超一般活動頁。

## Priority Issues

1. **[P0] 「洲遊幣 +N」獎品從未入帳＋輸局假慶祝**：spin() 只記 S.won 不加 balance；銘謝惠顧/再接再厲照樣顯示恭喜＋兌換碼。破壞「獎品是真的」，輸局假慶祝會成負評素材。**Fix**：獎項加 type(coin/physical/lose)；coin 入帳＋金幣動畫；lose 走專屬溫柔文案；僅實體獎出碼。→ /impeccable harden + delight
2. **[P0] 鍵盤／螢幕報讀者無法完成主流程**：投幣僅 pointer 拖曳 div/canvas，不可聚焦；modal 無 dialog 語意/焦點管理；input:focus 移除 outline。**Fix**：加真按鈕「投入 1 枚」；modal 補 role=dialog+焦點圈；結果 aria-live。→ /impeccable polish
3. **[P1] 等級切換不可發現＋預設門檻過高**：唯一入口是透明熱區，設計好的 #tier-hint 是死 CSS；新用戶預設一等獎（要 5 枚）。**Fix**：掛回提示膠囊或做可見等級 chip；預設 bestAffordableTier。→ /impeccable onboard
4. **[P1] 階層崩壞：雙主鈕＋三數字矛盾＋高屏死空白**：spin-btn 與 draw-btn 重複；「再投4枚開始抽獎／再2枚可抽二等獎／已投入1枚·再投4枚抽一等獎」同屏打架；高屏中段 300px 空白、轉盤反被壓小。**Fix**：主鈕去重、數字提示統一為單一語句、空間讓給轉盤/錢包動線。→ /impeccable layout
5. **[P1] WCAG 對比與小字**：muted #8A8477 3.1–3.35:1、gold #A16207 小字 4.13–4.44:1、條款 11px ×12、disabled CTA 1.56:1（載引導文案）。**Fix**：muted/gold 各深一階、條款 12px、disabled 改可讀灰。→ /impeccable polish

## Persona Red Flags

- **Casey（單手行動）**：投5枚重複5次；瀏覽獎品觸控目標僅約25px 高；旋轉中刷新＝幣扣獎失（先扣款 save、5.4s 後才記獎）。
- **Jordan（LINE 首訪）**：兩張同款脈動金卡不知先點哪張；「再投5枚抽一等獎」但不知幣從哪來；不可能發現可切到三等獎便宜玩；靜止時轉盤頂端常見裁切的「銘謝惠顧」字樣。
- **Sam（a11y）**：無法投幣＝無法遊玩（P0）；focus 樣式被移除；drawFloat/auraPulse/canupPulse/hintPulse 未支援 prefers-reduced-motion（半套）；muted 3.1:1。
- **小雅（中秋搶好康粉絲）**：任務未驗證即得幣（誠實系統）；跑馬燈假名單被識破反傷「官方活動」信任；兌換碼前端 Math.random() 生成、截圖可偽造、櫃台無從對驗。

## Minor Observations

- 跑馬燈示意名單＋客端兌換碼＝誠實性/舞弊風險，正式版須後端簽發＋標示或移除
- leads 個資明文 localStorage（原型已警語；正式必走後端）；訪客密碼明碼在 JS
- 旋轉中頂端文字與投幣口/穹頂圖層重疊斷字（「再接再」「5 銘謝惠…」）
- 「歸零」z-index 90 壓過 modal 內容（含法務註記）
- 中獎彈窗點背景不能關（與個資彈窗不一致）；.tuner/applyPlate 鷹架代碼殘留
- skipped-heading（h1→h6）、winticker nested-cards、stack-label wide-tracking（偵測器）
- 320×568 版面反而最緊湊漂亮；高屏未善用
- bounce-easing ×2（modal pop、金幣回彈）幅度輕微，遊戲語境可辯護，列觀察

## Questions to Consider

1. 投幣是最好的儀式，為何投 5 枚是同一動作重複 5 次，而不是一段會升溫的儀式（第 5 枚有專屬音畫）？
2. 三等獎近半玩家會輸——洲際禮賓員面對抽到銘謝惠顧的客人會說什麼？現在的答案是「恭喜中獎，請至櫃台核銷」。
3. 等級章是全遊戲唯一策略決策，為何是隱形熱區而不是三枚可觸摸、可比較獎品的實體徽章？
