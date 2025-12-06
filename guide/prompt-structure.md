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






