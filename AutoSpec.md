# 🛠️ AgilePoint NX10 - OpenAI 整合操作教學自動化生成指引

本文件定義了如何將「圖片目錄（如 `OpenAI/`）」與「步驟說明」自動轉譯並組裝為符合規範的 `OpenAI.html` 網頁。不論是透過 AI 轉換或是自動化腳本（Python），都應嚴格遵循此結構。

---

## 📂 1. 輸入源資料結構 (Source Data Structure)

當使用者提供 `OpenAI/` 目錄時，應自動識別並對齊以下 11 個步驟的圖片與內文：

| 步驟編號 | 圖片檔名 (位於 OpenAI/ 目錄下) | 標題 (`.step-title`) | 描述文字 (`.desc-text`) 規範 |
| :--- | :--- | :--- | :--- |
| **01** | `01_Global Access Token_01.png` | 01 Global Access Token 01 | 進入 AgilePoint NX 管理介面，點選Add Token新增設定。123 |
| **02** | `01_Global Access Token_02.png` | 01 Global Access Token 02 | 點擊新增 OpenAI。 |
| **03** | `01_Global Access Token_03.png` | 01 Global Access Token 03 | 輸入自定義名稱並填入從 OpenAI 官網取得的 API 金鑰(須付費)，完成全域存取設定。 |
| **04** | `02_eForm_01.png` | 02 eForm 01 | 在 eForm 表單設計器中，進行配置(如圖:AutoLoopUp\*1、Text Area\*2、Button\*1)。 |
| **05** | `02_eForm_02.png` | 02 eForm 02 | 編輯AutoLoopUp，選擇/新增 LoopUp，並且設定Access Token(Open AI)。 |
| **06** | `02_eForm_03.png` | 02 eForm 03 | 配置 OpenAI 活動的輸入參數與模型屬性。<br><br>**Model Properties 頁籤：調整 AI 的「性格與精準度」**（此步驟內需嵌入參數定義表格，詳見 HTML 範本）。 |
| **07** | `02_eForm_04.png` | 02 eForm 04 | 設定輸出對應，將 AI 產生的回應寫回至表單的指定欄位中。下圖表示紅色的一定要設定（此步驟內需嵌入 Prompt 核心要素表格，詳見 HTML 範本）。 |
| **08** | `02_eForm_05.png` | 02 eForm 05 | 請設定Form裡面的請求欄位。 |
| **09** | `02_eForm_06.png` | 02 eForm 06 | 請選擇Map OpenAI Response To App Schema，並點右側的放大鏡。 |
| **10** | `02_eForm_07.png` | 02 eForm 07 | 設定content至你的輸出欄位。 |
| **11** | `03_Result_01.png` | 03 預覽 | 預覽畫面，執行結果如圖。 |

---

## 📄 2. 預期輸出的 HTML 完整範本

自動化工具應將上述結構填入 `` 中，並輸出如下的完整 HTML 程式碼：

```html
<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AgilePoint NX10 - OpenAI 使用教學 (更新版)</title>
    <style>
        body { font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; background-color: #f4f7f6; color: #333; margin: 0; padding: 20px; }
        .container { max-width: 80%; margin: 0 auto; background: white; padding: 30px; box-shadow: 0 4px 15px rgba(0,0,0,0.1); border-radius: 8px; }
        .header { text-align: center; border-bottom: 2px solid #3498db; padding-bottom: 10px; margin-bottom: 20px; }
        .ref-link { text-align: right; margin-bottom: 20px; font-size: 0.9em; }
        .ref-link a { color: #3498db; text-decoration: none; font-weight: bold; }
        .step-container { display: flex; align-items: flex-start; margin-bottom: 40px; border-bottom: 1px solid #eee; padding-bottom: 20px; }
        .image-box { flex: 0 0 480px; margin-right: 25px; cursor: zoom-in; }
        .image-box img { width: 100%; height: auto; border: 1px solid #ddd; border-radius: 4px; }
        .description-box { flex: 1; min-width: 400px; }
        .step-title { font-weight: bold; font-size: 1.2em; color: #2980b9; margin-bottom: 10px; }
        .desc-text { line-height: 1.6; background: #fafafa; padding: 15px; border-left: 4px solid #3498db; }
        #modal { display: none; position: fixed; z-index: 1000; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.8); justify-content: center; align-items: center; }
        #modal img { max-width: 90%; max-height: 90%; border: 5px solid white; }
    </style>
</head>
<body>

<div class="container">
    <div class="ref-link">
        官方參考網址：<a href="[https://blog.agilepoint.com/agilepoint-v10-now-supports-form-lookups-for-openai/](https://blog.agilepoint.com/agilepoint-v10-now-supports-form-lookups-for-openai/)" target="_blank">AgilePoint Blog - OpenAI Form Lookups</a>
    </div>
    <div class="header">
        <h1>AgilePoint NX10 - OpenAI 整合操作教學</h1>
    </div>
    
    <div id="content">

        <div class="step-container">
            <div class="image-box" onclick="openModal('OpenAI/01_Global Access Token_01.png')">
                <img src="OpenAI/01_Global Access Token_01.png" alt="01 Global Access Token 01">
            </div>
            <div class="description-box">
                <div class="step-title">01 Global Access Token 01</div>
                <div class="desc-text">進入 AgilePoint NX 管理介面，點選Add Token新增設定。123</div>
            </div>
        </div>
    
        <div class="step-container">
            <div class="image-box" onclick="openModal('OpenAI/01_Global Access Token_02.png')">
                <img src="OpenAI/01_Global Access Token_02.png" alt="01 Global Access