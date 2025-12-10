# mis583-group10
# 專案簡介
本專案旨在評估 Grounded-SAM (結合 GroundingDINO 與 SAM) 以及 CLIP-guided SAM 兩模型在自建的 COCO 2017 驗證集子集 (Mini-subset) 上的表現。

我們特別聚焦於 多粒度提示詞工程 (Multi-Granularity Prompt Engineering) 的影響，測試不同層級的文字描述（粗粒度、屬性描述、細緻描述）如何影響模型的語意分割 (Segmentation) 準確度。

## 檔案結構

### 1. 原始程式碼 (.ipynb)
- groundingdino-sam.ipynb:
  Grounded-SAM 的實作程式碼。
  整合 GroundingDINO 進行物件偵測 (Box Detection) 與 SAM 進行分割 (Segmentation)。
- CLIP-guided SAM.ipynb:
  CLIP-guided SAM 的實作程式碼。
  利用 CLIP 模型根據文字提示引導分割流程。

### 2. 資料集與標註檔
- val2017_50/:
  包含本實驗選用的 50 張 COCO 2017 驗證集圖片。
  ground_truth.json：位於此資料夾內。包含標準化的 Ground Truth (BBox 與 Masks)，用於計算 IoU 與評估模型效能。
- val2017_prompt.json:
  定義了每張圖片在三種不同粒度 (Coarse, Attribute, Fine-grained) 下的文字提示詞。

### 3. 實驗結果 (outputs)
實驗結果依照模型與提示詞層級分類，每個資料夾內包含生成的遮罩圖像與預測數據。

- Grounded-SAM 實驗結果：
  ground-SAM_coarse_results/ (粗粒度)
  ground-SAM_attribute_results/ (屬性描述)
  ground-SAM_fine_grained_results/ (細緻描述)

- CLIP-guided SAM 實驗結果：
  CLIP-guided SAM_coarse_results/
  CLIP-guided SAM_attribute_results/
  CLIP-guided SAM_fine_grained_results/

## 🚀 執行方式
1. Clone 此專案至本地端或 Colab。
2. 安裝必要的依賴套件 (請參考 Notebook 中的第一個 Cell)：
   - segment_anything (SAM)
   - groundingdino (用於 Grounded-SAM)
   - clip (用於 CLIP-guided SAM)
   - 其他通用套件：transformers, torch, opencv-python 等。
3. 依序執行 Jupyter Notebook (.ipynb) 即可重現實驗結果與分割影像。
