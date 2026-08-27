# CHT-smart-chinese-english-IME
CHT智能中英輸入法：Windows11/10 下中英輸入法無須切換中英模式，直接輸入中文字(注音)英文字智慧判斷，準確率高>99.9%延遲低&lt;1ms,1不需網路本地使用不收集資料

程式壓縮下載:
[SmartZhEnIme.zip](https://github.com/user-attachments/files/31497676/SmartZhEnIme.zip)

點擊下載到電腦中指定folder中後，
點擊此檔案解縮到此目錄中後，選擇SmartZhEnIme-v1.1.6-Setup-x64.exe檔，滑鼠右鍵以系統管理員身分執行此程式，遵照畫面說明完成安裝。

# SmartZhEnIme 智能中英輸入法
## Windows 詳細使用說明與達成成果

---

## 1. 專案簡介

SmartZhEnIme 是以 Windows TSF（Text Services Framework）為基礎的繁體中文／英文智慧混合輸入法。主要目標是在一般使用情境下，讓使用者不必頻繁手動切換中英文模式，就能直接進行中文、英文與中英混合輸入。

三種模式： 短按 Shift 切換 (Win+Space 切換輸入法)

1. **智能中英（Smart）**：預設模式，自動判定中文或英文，圖示為「智」。
2. **英文（English）**：只處理英文輸入。
3. **中文（Chinese / Zhuyin）**：只處理中文注音輸入，圖示為「中」。

---

## 2. 系統需求

- Windows 10 x64 或 Windows 11 x64
- PowerShell
- 可新增／移除 Windows 鍵盤與輸入法
- 若需從原始碼建置：Visual Studio 2022 + Desktop development with C++

---

## 3. 安裝方式

### 3.1 建議使用版本

`SmartZhEnIme-v1.1.6-Setup-x64.exe`

此版本已修正 Windows language profile icon route 註冊問題。

### 3.2 安裝指令

```
.SmartZhEnIme-v1.1.6-Setup-x64.exe
```

### 3.3 安裝完成後的檢查重點

- 腳本應完成 TSF profile 註冊、啟用與驗證。
- Windows 輸入法清單中應能看到「繁體中文（台灣）/ CHT智能中英」。
- 工作列可切換到 SmartZhEnIme。
- 若是首次安裝或剛更新 icon，建議到 Windows 鍵盤設定重新加入該輸入法一次。

---

## 4. Windows 設定：新增與選擇輸入法

### 4.1 若安裝後未立即出現在清單

建議步驟：

1. 開啟 Windows「設定」。
2. 進入「時間與語言」→「語言與地區」。
3. 在「繁體中文（台灣）」下方進入「語言選項」。
4. 進入「鍵盤」。
5. 選擇「新增鍵盤」或新增輸入法。
6. 從清單中選擇 SmartZhEnIme / CHT智能中英。
7. 新增完成後，回到桌面工作列切換輸入法。

### 4.2 工作列選擇輸入法

安裝成功後，可從工作列右下角語言／輸入法區域選擇 SmartZhEnIme。當前模式會顯示在工作列圖示中，例如「智」、「中」或對應英文模式。

---

## 5. 卸載與移除

### 5.1 卸載指令

```
.應用程式中執行卸載完成解除安裝
```

### 5.2 建議的乾淨移除流程

1. 先關閉正在使用 SmartZhEnIme 的應用程式。
2. 執行 uninstall.ps1。
3. 開啟 Windows 語言／鍵盤設定，確認 SmartZhEnIme 已不在鍵盤清單中。
4. 若仍顯示於清單，可手動將該鍵盤移除。
5. 必要時登出再登入 Windows，讓 TSF / icon cache 完整刷新。
6. 若要重新安裝，再執行 install.ps1。

### 5.3 重新安裝但圖示未刷新時

- 先用 uninstall.ps1 卸載。
- 到 Windows 鍵盤清單確認該輸入法已移除。
- 重新安裝後，再到 Windows 鍵盤設定「新增鍵盤」一次。
- 這通常可解決 profile icon cache 沒刷新的情況。

---

## 6. 附圖操作說明

下圖為 SmartZhEnIme 在 Windows 桌面上的實際畫面，包含輸入區、候選窗、資訊視窗、工作列模式圖示與 Windows 鍵盤清單。

<img width="1152" height="648" alt="智能中英輸入2" src="https://github.com/user-attachments/assets/2f9c8964-2043-4621-88bb-ac52df79f31a" />

**圖 1　SmartZhEnIme 實際操作畫面（含候選窗、資訊視窗、工作列與鍵盤清單）**

### 6.1 圖中各區域說明

| 位置 / 標示 | 畫面內容 | 說明 |
|---|---|---|
| 左上紅框 | 文字輸入區 + 候選窗 | 顯示目前輸入內容與候選字清單。候選字仍屬未 commit 狀態，可用 Up/Down 選擇，Enter 提交。 |
| 中央視窗 | 資訊視窗 | 右鍵點擊輸入法 icon 後選擇「資訊」會開啟。內容包含模式說明、操作說明與隱私聲明。 |
| 右下綠框 | Windows 鍵盤清單 | 可看見「繁體中文（台灣）/ CHT智能中英」。若安裝後未生效，通常需要在此處重新加入 SmartZhEnIme。 |
| 右下紅框左側 | 智 | 代表目前處於 Smart 智能中英模式。 |
| 右下紅框右側 | ㄆ profile icon | 代表 SmartZhEnIme 的 language profile icon。這是 Windows 鍵盤清單／語言列中辨識此輸入法的重要圖示。 |

---

## 7. 日常使用方式

### 7.1 三種模式

- 智能中英（Smart）：直接輸入中文、英文或混合內容，系統自動判斷。
- 英文：只進行英文輸入。
- 中文：只進行注音中文輸入。

### 7.2 模式切換

- 短按 Shift：循環 Smart → English → Chinese → Smart。
- 左鍵點擊狀態 icon：依相同順序切換。
- 按住 Shift、Shift+其他鍵、長按 Shift 或自動重複，不應切換模式。
- 右鍵點擊 icon：只開啟選單，不得切換模式。

### 7.3 注音輸入與 commit

- 輸入注音 raw 後，文字維持 composition 狀態，尚未 commit 時應有底線／組字標示。
- Enter：明確 commit。
- Space 在注音 tone 階段代表 neutral tone（tone=1），不是 commit。
- 候選視窗即使顯示 top candidate，也不代表已 commit。

### 7.4 候選與游標

- Up / Down：選候選字。
- Left / Right：在組字內移動 caret。
- Backspace：刪除一個邏輯中文字／組字單位。
- 若在 caret 處刪除後輸入新 raw，候選應以新 raw 為來源。
- 若只移動 caret 再按 Up/Down，候選應以 caret 到尾端為來源。

### 7.5 特殊符號

快捷鍵：

`Ctrl + Alt + ,`

可叫出特殊符號／標點視窗。

---

## 8. 中英混合輸入範例

| 輸入內容 | 預期結果 | 重點 |
|---|---|---|
| this is a book | 保持英文與空白 | 不得變成 this is abook |
| absent火車 | 英文 token + 中文正確銜接 | 英文與中文邊界不可破壞 |
| 這句子include英文 | 中英混合正確顯示 | 不得在 include 前後殘留 raw |
| 7-11你是誰 | 7-11 保持 literal | 數字與連字號不可被錯判 |
| 37% | 原樣 commit | Enter 後不可失敗 |
| 37%提高 | % 後正確轉入中文 | 不可出現 37%wu6el 或 raw tail |

---

## 9. 達成成果

- 完成 Smart / English / Chinese 三模式架構。
- 完成短按 Shift 與點擊 icon 的模式循環規格。
- 正式定義 neutral tone：Space = tone 1，不是 commit。
- 建立 caret-aware candidate 規則。
- 建立 candidate 視窗定位優先序：下 → 上 → 右 → 左。
- 建立右鍵資訊選單與自動關閉行為。
- 修正 Windows profile icon route 註冊問題。
- 建立 numeric-percent regression：37%、37%提高。
- 完成 1K portable formal replay 驗證通過。

---

## 10. 1K 篇中英混文章輸入 驗證統計

- Articles：**1000 / 1000 accepted**
- Test A：**9000 / 9000 PASS**
- Test B：**18000 / 18000 PASS**
- Raw leak：**0**
- Accepted failures：**0**
- Accepted state_bad：**0**
- Portable latency gate：**P95 ≤ 10 ms；P99 ≤ 20 ms**
- Articles 901–1000 最高：**P95 1.485 ms；P99 9.109 ms**
- Portable gate：**PASS**

---

## 11. 目前專案狀態

目前 SmartZhEnIme 的 portable 演算法與 1K simulation gate 已通過，已達 release-candidate 水準。

- composition
- commit
- candidate
- mode
- menu
- placement
- sensitive bypass
- installer / uninstaller
- real-host latency


---

## 12. 常見問題排除

- 安裝後看不到輸入法：先確認 install.ps1 成功，再到 Windows 鍵盤設定重新加入 SmartZhEnIme。
- 圖示未更新：多半是 Windows profile icon cache；可先移除鍵盤，再重新新增。
- Enter / Space 沒反應：屬高優先級 TSF regression，應記錄 host、模式、按鍵順序與畫面結果。
- 候選位置不正確：記錄 caret、monitor、DPI 與 taskbar 位置，供定位規則檢查。
- Shift 意外切模式：若 Shift 與其他鍵一起按卻切 mode，屬回歸問題。
