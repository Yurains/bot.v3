# 說明
因為朋友的一句話「俊諺，我好想看周湯豪喔，你有辦法搞機器人嗎?」
展開了一場奇妙的OCR開發之旅，在此期間搶到了周杰倫、陳華等演唱會。但，機器人始終都沒完善，都還是要透過Java修改，但是我好想看芒果醬演唱會.....，終於又熬夜改東改西，把問題降低到最少，本機器人基於 [Max蛋黃車上車機器人](https://github.com/lovefirst02/tix_bot) 進行開發，
並進行了大幅度的修改，包括：
- 優化語法，刪除重複函數，提高運作速度。
- 重新設計 GUI 介面。
- 透過 OCR 技術進行字符辨識，並進行相關比較研究。
- 開發環境基於 **Python 3.11** 及 **conda**，並在 macOS開發 在 Windows RTX4090底下進行測試。
---
## OCR 比較測試

現今流行的搶票方法多透過 OCR 進行字符辨識，然而傳統上的OCR仍有許多限制，例如辨識不佳、架構層數有問題
Max 上車機器人使用的 OCR 甚至只是個 beta 版本，因此我選擇了兩種較優的 OCR：

1. **ddddOCR**(https://github.com/sml2h3/ddddocr)
2. **PaddleOCR**(https://github.com/PaddlePaddle/PaddleOCR)

OCR 的辨識效果就是他媽個玄學(Sml2h3 2024 et al. ddddocr)，為了測試兩種OCR的效能
透過驗證碼速度研究進行比較，並在Mac Mini M4Pro底下train，避免誤差錯誤，並在Linux、Windows操作，並進行交叉驗證，結果如下：
### 📊 測試結果統計

- **測試時間**：2025/02/22 23:12:18
- **總測試圖片數量**：5500 張

|  方法   | 成功數量 | 平均處理時間 |
|------------|----------|--------------|
| ddddOCR    | 5500     | 0.0072 秒    |
| PaddleOCR  | 5500     | 0.0102 秒    |

📌 **結論**：
- 使用 **ddddOCR** (`main.py`)來處理演唱會搶票優於 **PaddleOCR**。 (都已重新train過。
- 若電腦硬體資源不足，仍可選擇速度較慢的 **PaddleOCR** (`main(pa).py`)，來執行搶票也是不錯的方案，其實我覺得使用體感不會差到哪。

---

## 環境安裝
先安裝vscode https://code.visualstudio.com/docs/?dv=win64user

###  使用 pip 安裝
請確保已安裝 **Python 版本 >= 3.8**。

#### 安裝步驟：
```bash
# Clone 專案到本地端
git clone https://github.com/your-repo/tix_bot.git

# 安裝必要套件>pip install資料夾裡
pip install -r requirements.txt
（有兩個 擇一即可） 有一個是paddleOCR! 要看清楚哦！

# 或者手動安裝所需套件
```

---

##  影片說明

>[單開有聲音說明](https://www.youtube.com/watch?v=sXyOsXwPsKo)
>>[多開示範](https://www.youtube.com/watch?v=ZzHeHpx6tek)

---

## ⚠注意事項

📌 **免責聲明**
- 本人不對該程式的使用負責。
- 網路速度也會影響搶票速度，這並不是100%能搶得到票的。
- 若涉及黃牛、濫用等行為，請自行承擔相關法律責任。
- 該機器人純屬興趣開發，只為幫助朋友、我自己搶想聽的演唱會門票。

---
## 🔄 更新(2025/2/24)

### 更新-新增功能
1. **網頁多開** - 可同時開啟多個購票頁面，提高成功率。(要開幾個視窗就搶票滑鼠按幾下！
2. **瀏覽器大小檢測工具** - 在 `tool` 內新增瀏覽器大小檢測工具，確保所需要的大小。
3. **筆記本檔案保存設定** -  回覆初始設定有些小bug，目前不清楚為何，用一個比較陽春的辦法，`tool`有一個txt檔案，可複製到 settings.json檔，即可回復初始設定，避免存檔錯誤。
4.  **KKTIX選地區** -可以在區域選擇位置，例如台中、台北等... 

###  已知問題
1. **不會自動登入帳號** - 需手動點擊登入按鈕（但會自動輸入帳號密碼）。
2. **不會自動選擇購票頁面** - 在某種情況下（拓元尤其明顯），他不會自己選擇購票的網頁，你要自己點擊，就會自動進行了。
3. **拓元的驗證** -  若使用fb登入拓元，可能會出現驗證碼驗證，這是需要手動輸入驗證的，這個沒有做。
4. **搶票過程速度較慢** - 由於 Python 執行速度仍不及 C++，開啟搶票功能後可能稍慢，會持續優化。
5. **登入完帳號不會進入購票網站** - 目前不知道是什麼何種原因導致，有時候可以有時候又不行，就自己手動進入一下搶票的首頁吧。
6. **KKITX** -只是個Beta，有時候會偵測不到。 
---
## 聯絡作者
**Instagram**：[junyan_0826](https://www.instagram.com/junyan_0826)
:說真的我不想工作，我每天累得像條狗，我想中樂透
