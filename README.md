### Vocab_Card_Prompts

<div align="Left">
A specialized collection of JSON prompt frameworks designed for AI image generation models to create 4-panel educational vocabulary cards.
</div>


[English](#english) | [中文](#中文)

## <a name="english"></a>English

### Features

3 Distinct Art Styles: Covers American Textbook (Formal/Vector), Japanese Anime (Cel-shaded/Vibrant), and American Comic (Bold Ink/Dramatic).

Stable Infographic Architecture: All prompts utilize an "Infographic Anchor" logic to ensure text legibility and strict layout adherence.

Bilingual Optimization: Enforces strictly formatted Traditional Chinese definitions (< 12 chars) and English context sentences.

Structured JSON Output: Generates valid JSON objects ready for integration with Banana Pro or other stable diffusion pipelines.

Automated Content Analysis: The prompts instruct the LLM to act as a linguist, analyzing the top 4 distinct definitions of any input word.

Style Gallery

[American Textbook](prompts/american-textbook.txt) 

[American Comic](prompts/american-comicV2.txt)  

[Japanese Anime](prompts/japanese-anime.txt) 

### How to Use

Select a Style: Choose a text file from the prompts/ directory (e.g., prompts/japanese-anime.txt).

Input to LLM: Copy the entire content of the file into an LLM (Gemini, ChatGPT, Qwen, etc.).

Provide a Word: Type the English vocabulary word you wish to visualize (e.g., "Access").

Generate JSON: The LLM will output a JSON code block.

Create Image: Paste the JSON content into your Banana Pro or Stable Diffusion interface to generate the vocabulary card.

It is recommended to upload a reference image as a layout template for each generation. 

Please name this file Actor.jpg to match the default prompt settings. 

If you use a different filename, ensure you update the reference name within the prompt accordingly.

---

### Step by Step ###

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

### License

This project is released under the [MIT License](LICENSE).

## <a name="中文"></a>中文

<div align="Left"> AI生圖模型設計的JSON提示詞架構集合，用於生成高品質的「四格單字記憶卡」。 </div>


[View this document in English](#english)

### 功能特色

三種風格: 涵蓋 美式課本 (正式/向量風格)、日系動漫 (賽璐珞/鮮豔) 與 美式漫畫 (粗墨線/戲劇張力)。

穩定的資訊圖表架構: 所有提示詞皆採用「Infographic Anchor (資訊圖表錨點)」邏輯，確保版面工整與文字清晰度。

雙語優化設計: 強制規範繁體中文釋義（12 字以內）與英文語境的分行顯示，提升閱讀體驗。

標準化 JSON 輸出: 產出格式嚴謹的 JSON 物件，可直接應用於 Banana Pro 或 Stable Diffusion 自動化流程。

自動化內容分析: 提示詞內建語言學家角色設定，能自動分析輸入單字的四大核心義項與語境。

風格展示

[美式課本 (Textbook)](prompts/american-textbook.txt) 

[美式漫畫 (Comic)](prompts/american-comicV2.txt)  

[日系動漫 (Anime)](prompts/japanese-anime.txt) 

### 如何使用

選擇風格: 從 prompts/ 資料夾中選擇一個文字檔（例如 prompts/japanese-anime.txt）。

輸入至 LLM: 將檔案內的完整內容複製並貼上至 LLM (Gemini, ChatGPT, Qwen 等)。

提供單字: 輸入您想要視覺化的英文單字（例如："Access"）。

獲取 JSON: LLM 將會自動生成一段 JSON 程式碼。

生成圖片: 將該 JSON 內容貼入 Banana Pro 或 Stable Diffusion 介面中即可生成單字卡。

建議每次生成時，上傳一張參考圖片作為構圖模板（Layout Template）。

請將該圖片命名為 Actor.jpg 以匹配 Prompt 的預設設定；若您使用其他檔名，請務必同步修改 Prompt 內對應的參照名稱。

授權條款

### 本專案採用 [MIT License](LICENSE) 授權。
