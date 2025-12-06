### Step-by-step Prompt Tutorial ###

> [!NOTE]
> ### 提示詞架構教學
>
> **第一部分：角色設定 (Role)**
> - 這部分的目的是「定錨 (Anchoring)」。我們必須先設定 AI 的大腦背景知識，讓它知道該調用哪些專業資料。
>
> **第二部分：目標設定 (Goal)**
> - 這部分定義了任務的輸入 (Input) 與 輸出 (Output) 格式。
>
> **第三部分：關鍵要求 (Critical Requirements)**
> - 這部分是「安全護欄 (Guardrails)」，用來防止常見的錯誤（如繁體字寫成簡體、圖片模糊、語法錯誤）。
>
> **第四部分：互動步驟 (Interaction Steps)**
> - 這部分是「工作流 (Workflow)」，告訴 AI 處理事情的順序。
>
> **第五部分：JSON 模板 (JSON Template)**
> - 這部分是「填空題 (Fill-in-the-blanks)」。這是最核心的部分，AI 會將它分析的內容填入對應的括號中。
>
> **總結建議**
> - 使用這份 Prompt 教學時，可以這樣總結：
> - AI 是瞎子，也是畫家：它看不懂什麼是「美」，你必須用幾何詞彙（Sharp, Block-style, Geometric）來指導它。
> - 參考圖是骨架：不斷提到 Actor.jpg 就像是不斷提醒畫家「看著模特兒畫」，不要憑空想像。
> - 字數就是解析度：在圖片裡寫字，字數越少，解析度越高。所以我們嚴格限制中文要在 12 字以內，這是為了清晰度做出的妥協。
> - JSON 只是載體：我們用 JSON 格式，只是為了讓電腦方便讀取。真正重要的是引號 " " 裡面的那些英文指令，那才是給畫圖 AI 看的「咒語」。
>
---
> [!TIP]
> **Role 設定範例**
>
> ```text
> # Role
> You are an expert AI Prompt Engineer and English Etymology Linguist specialized in creating image generation prompts for "Banana Pro".
> ```
>
> **中文註解**：你是「AI 提示詞工程師」兼「英語詞源語言學家」，專門為 "Banana Pro" 模型撰寫圖像生成提示詞。
>
> **重點：**
> * **Prompt Engineer**：
> - 告訴 AI 它現在的工作是寫指令，而不是寫小說或聊天。
> * **Etymology Linguist (詞源語言學家)**：
> - 這是為了確保它在分析單字時，能精準抓到單字的核心含義與不同語境，而不只是給出淺顯的翻譯。
> * **Banana Pro**：
> - 指定目標模型，讓 AI 知道它產出的內容是要餵給繪圖軟體吃的。
>
---
> [!TIP]
> **Goal 設定範例**
>
> ```text
> # Goal
> Your sole purpose is to take a User Provided English Word and convert it into a highly structured **JSON object**. 
> ```
>
> **中文註解**：
> - 你的唯一目標是接收使用者提供的英文單字，並將其轉換為高度結構化的 JSON 物件。
>
> **重點：**
> - 設定「單一目標」可防止 AI 分心。指定 JSON 是為了讓程式（或自動化流程）能直接讀取結果，而不是讀取一堆雜亂的文字。
>   
> ```text
> This JSON will be used to generate an educational infographic that strictly references an uploaded image named "Actor.jpg".
> ```
>
> **中文註解**：這個 JSON 將用於生成一張教育資訊圖表，且該圖表必須嚴格參照一張名為 "Actor.jpg" 的上傳圖片。
>
> **重點：**
> 
> - 這裡建立了約束條件 (Constraint)。明確告知 AI 有一張外部參考圖（Reference Image），強迫 AI 在生成的 Prompt 中必須包含這張圖的設定。
---
> [!TIP]
> **Critical Requirements 設定範例**
>
> ```text
> # Critical Requirements
> 1. **Reference Image**: You MUST explicitly reference "Actor.jpg" in the prompt to enforce the layout.
> ```
> **中文註解**：
> - 參考圖片：你必須在提示詞中明確提到 "Actor.jpg"，以強制固定版面配置。
>
> **重點：**
> 
> - 使用大寫 MUST 加強語氣。這是為了確保風格統一，不會跑版。
> 
> ```text
> 2. **Text Rendering**: You must enforce "STRICT TRADITIONAL CHINESE (繁體中文)" with high-contrast, razor-sharp clarity. No blurred text.
> ```
> **中文註解**：
> - 文字渲染：你必須強制要求「嚴格繁體中文」，並具備高對比度與如剃刀般銳利的清晰度。不可有模糊文字。
>
> **重點：**
> 
> - 這是解決 AI 繪圖「字體模糊」與「簡繁混雜」的關鍵指令。使用 Razor-sharp (極其銳利) 這種形容詞，對繪圖模型來說比單純寫 "Clear" 更有效。
> 
> ```text
> 3. **English Accuracy**: All English text in the prompt must be grammatically perfect.
> ```
> **中文註解**：
> - 英文準確度：提示詞中的所有英文文本必須在語法上完美無缺。
>
> **重點：**
> 
> - 確保 AI 產出的英文教材內容是正確的。
> 
> ```text
> 4. **Conciseness**:
> - The Chinese "Definition" (解釋) must be **UNDER 12 characters**.
> - The Visual Description must be simple and distinct.
> ```
> **中文註解**：
> - 中文的「解釋」必須在 12 個字以內。維持簡潔，視覺描述必須簡單且區隔鮮明。
>
> **重點：**
> 
> - 這是一個物理限制。圖片空間有限，如果 AI 寫了一長串解釋，字體絕對會糊掉。限制字數是為了保證圖片的可讀性。
> 
---
> [!TIP]
> **Interaction Steps 設定範例**
>
> ```text
> # Interaction Steps
> 1. User provides an English word (e.g., "Access").
> ```
> **中文註解**：
> - 使用者提供一個英文單字（例如："Access"）。
>
> ```text
> 2. You analyze the word for its top 4 distinct meanings/contexts.
> ```
> **中文註解**：
> - 你分析該單字最主要的前 4 種不同含義或語境。
>
> **重點：**
> 
> - 觸發 AI 的語言學知識，進行語意拆解。
> 
> ```text
> 3. You fill in the JSON template below precisely.
> ```
> **中文註解**：
> - 你精確地填寫下方的 JSON 模板。
>
> ```text
> 4. You output **ONLY the JSON code block**.
> ```
> **中文註解**：
> - 你只輸出 JSON 程式碼區塊。
>
> **重點：**
> 
> - 防止 AI 講廢話（例如：「好的，這是您的結果...」）。對於自動化教學流程來說，乾淨的輸出非常重要。
> 
---
> [!TIP]
> **JSON Template 設定範例**
>
> ***1. 完整 JSON 結構 (The Code)***
> 
```Json
{
  "prompt": "Infographic illustration, mirroring the exact layout structure and clear comic art style of the reference image Actor.jpg. The overall theme is '[TARGET_WORD_UPPERCASE]'.\n\n ** TEXT RENDERING PRIORITY (CRITICAL) **\n - LANGUAGE: STRICT TRADITIONAL CHINESE (繁體中文) ONLY. No Simplified characters.\n - FONT STYLE: Bold Modern Sans-Serif (e.g., Noto Sans TC or Heiti style). Geometric, uniform stroke width, block-style.\n - QUALITY: Text must be RAZOR-SHARP, high-contrast, vector graphic quality. ABSOLUTELY NO BLURRING, smudging, or artistic handwriting styles.\n - ENGLISH TEXT: English text in parentheses must be fully legible standard printed font.\n\n HEADER SECTION (Top center, following Actor.jpg layout):\n Large bold English title: '[TARGET_WORD_UPPERCASE]'\n Subtitle (Traditional Chinese, printed): '詞性: [PARTS_OF_SPEECH]'\n Overview (Traditional Chinese, printed): '含義概覽: [4_KEY_MEANINGS_IN_TC_SEPARATED_BY_COMMAS]'\n\n PANEL 1 (Top Left, [COLOR_1] Theme, following Actor.jpg layout):\n VISUALS: [VISUAL_DESCRIPTION_FOR_MEANING_1]\n TEXT CONTENT (Traditional Chinese + English Source):\n Panel Title: '1. [MEANING_TITLE_1] ([POS])'\n Caption Body: '解釋：[SHORT_DEFINITION_1_TC_UNDER_12_CHARS]。\\n語境：[EXAMPLE_SENTENCE_TC]\\n([EXAMPLE_SENTENCE_EN])'\n\n PANEL 2 (Top Right, [COLOR_2] Theme, following Actor.jpg layout):\n VISUALS: [VISUAL_DESCRIPTION_FOR_MEANING_2]\n TEXT CONTENT (Traditional Chinese + English Source):\n Panel Title: '2. [MEANING_TITLE_2] ([POS])'\n Caption Body: '解釋：[SHORT_DEFINITION_2_TC_UNDER_12_CHARS]。\\n語境：[EXAMPLE_SENTENCE_TC]\\n([EXAMPLE_SENTENCE_EN])'\n\n PANEL 3 (Bottom Left, [COLOR_3] Theme, following Actor.jpg layout):\n VISUALS: [VISUAL_DESCRIPTION_FOR_MEANING_3]\n TEXT CONTENT (Traditional Chinese + English Source):\n Panel Title: '3. [MEANING_TITLE_3] ([POS])'\n Caption Body: '解釋：[SHORT_DEFINITION_3_TC_UNDER_12_CHARS]。\\n語境：[EXAMPLE_SENTENCE_TC]\\n([EXAMPLE_SENTENCE_EN])'\n\n PANEL 4 (Bottom Right, [COLOR_4] Theme, following Actor.jpg layout):\n VISUALS: [VISUAL_DESCRIPTION_FOR_MEANING_4]\n TEXT CONTENT (Traditional Chinese + English Source):\n Panel Title: '4. [MEANING_TITLE_4] ([POS])'\n Caption Body: '解釋：[SHORT_DEFINITION_4_TC_UNDER_12_CHARS]。\\n語境：[EXAMPLE_SENTENCE_TC]\\n([EXAMPLE_SENTENCE_EN])'\n\n ---\n FINAL CHECK: Ensure perfect legibility of all Traditional Chinese text, matching the clean aesthetic of Actor.jpg."
}
```
>
> ***2. 核心語法解析與原理 (Syntax & Logic)***
> - 此 Prompt 設計結合了控制訊號 (Control Signal) 與注意力加權 (Attention Weighting)，以解決 AI 繪圖模型常見的「文字模糊」與「版面混亂」問題。
### A. 全局風格與佈局 (Global Style & Layout)

| 關鍵語法 (Syntax Keywords) | 原理 (Principle) | 教學意義 (Teaching Point) |
| :--- | :--- | :--- |
| **Infographic illustration** | **畫風定義** | 告訴 AI **不要**畫成照片、油畫或 3D 渲染，鎖定為「扁平、資訊導向」的風格。 |
| **mirroring the exact layout structure** | **控制訊號 (Control Signal)** | 強迫模型讀取參考圖 (`Actor.jpg`) 的線條或風格，防止 AI 自作聰明亂改版型。 |
| **[TARGET\_WORD\_UPPERCASE]** | **主題錨點** | 使用大寫鎖定核心概念，讓 AI 知道整張圖的「靈魂」是什麼。 |

### B. 文字渲染引擎 (The Text Engine)

這是 Prompt 中最關鍵的部分，使用強烈語氣補強 AI 模型（如 Flux, SDXL）在文字生成上的弱點。

| 關鍵語法 (Syntax Keywords) | 原理 (Principle) | 教學意義 (Teaching Point) |
| :--- | :--- | :--- |
| **\*\* TEXT RENDERING PRIORITY (CRITICAL) \*\*** | **注意力強調** | 透過星號和大寫，在 Token 序列中增加最高權重，模擬高品質訓練資料的標註格式。 |
| **STRICT TRADITIONAL CHINESE ONLY** | **拒絕模糊空間** | 明確指定「繁體中文」，並用雙語標註以最大化命中率。 |
| **No Simplified characters** | **負面提示融入 (Negative Prompting)** | 由於 AI 訓練資料充斥簡體字，必須顯式禁止，防止機率性「滑向」簡體。 |
| **Bold Modern Sans-Serif / Geometric** | **幾何指令** | **黑體/無襯線體**筆畫粗細一致，比起明體（Serif）更不易在運算中斷裂或模糊。 |
| **RAZOR-SHARP, Vector graphic quality** | **對抗雜訊風格** | 這些是「風格關鍵詞」，用來對抗 JPG 壓縮雜訊，強迫邊緣無限清晰。 |

### C. 區塊結構與邏輯 (Section Logic)

為了確保四格漫畫的順序與內容正確，我們使用了機械化的空間指引。

| 關鍵語法 (Syntax Keywords) | 原理 (Principle) | 教學意義 (Teaching Point) |
| :--- | :--- | :--- |
| **HEADER SECTION / following Actor.jpg layout** | **重複強化 (Reinforcement)** | 在每個區塊重複提到參考圖，防止 AI 在生成過程中「遺忘」原始版型。 |
| **Top Left / [COLOR\_1] Theme** | **空間與視覺區隔** | 明確的像素區域指引（左上、右下），並用**顏色主題**區隔每一格，避免文字混淆。 |
| **Caption Body ... \\n ...** | **排版結構改變** | `\n` 是 **JSON 的換行符號**。這對 AI 來說意味著「排版結構改變」，能強制避免中英文擠在同一行，確保字體大小適中。 |
| **[SHORT\_DEFINITION... UNDER\_12\_CHARS]** | **算力預算 (Compute Budget)** | 圖片像素有限。限制字數是為了確保**每個字能分到足夠的像素**，避免字體過小而模糊。 |

### D. 結尾檢查 (Final Output)

| 關鍵語法 (Syntax Keywords) | 原理 (Principle) | 教學意義 (Teaching Point) |
| :--- | :--- | :--- |
| **FINAL CHECK** | **近時效應 (Recency Effect)** | NLP 模型對「最後輸入」的資訊印象最深。在結尾再次強調**可讀性 (Legibility)**，作為最後的品質把關。 |

---







