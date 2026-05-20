# Week 1: AI 基礎概念筆記

## Metadata

- Date: 2026-05-20
- Task: 用自己的話整理至少 6 個 AI 基礎概念
- Status: draft for Proof-of-Work
- Related repo: https://github.com/Swiftevo/ai-web3-school-cohort-0

## Goal

用自己的語言建立後續學習 Agent、workflow、AI coding 和 tool use 的共同語言，並保留「原理解 -> AI 指正 -> 修正版」的學習痕跡。

## 我的原理解

### LLM

大語言模式，由 OpenAI、Google、Claude Code 等 AI 公司發展的語言模型。在多組不同的數據輸入訓練後，它用於去猜測每一個輸入資訊背後，應該接著出現哪些內容及語言。

### Prompt

AI 在一間沒有任何窗口的黑房之中。prompt 是下達指令，讓 AI 知道更多的訊息，例如它的角色、目前的背景資料、要做的事、要確定的風格、口吻，處理的手法等等都是 prompt。讓 AI 知道要做甚麼。

### Context Window

窗口訊息。每一次 AI 也是全新的。context window 提供了一個窗口讓它知道在工作前需要知道的資料和背景。窗口越大，AI 在工作開始前就懂得越多，越能理解工作背景，更好地理解你的命令。這也是其中一個 AI 公司競爭的地方。

### Workflow

AI 工作的流程，由抓取資料、分析、選取調動的工具、產出結果、審核的一整套流程。

### Agent

由大語言模式、資料庫、對任務的記憶、在 workflow 流程下，選取可調動的工具或 API，拿到數據，自主進行分析、理解任務、完成任務，甚至能自我檢查，最後交出結果。這樣一個整個具備獨立完成任務的 AI，才可以稱為 agent。

### Tool Use

AI 可調用，以理解任務所需的外界資訊，幫助它完成任務的工具，例如調用 GitHub 內容的 API，查看某錢包有否包含某些代幣或 NFT 的 API 等。

### AI Coding

由 AI 去編寫智能合約。

### Guardrail

這個不懂。

### Tracing

這個不懂。

### Human-in-the-loop

Agent 自主進行任務時，需要在關鍵節點引入人類決定，而不能全程由 agent 全權掌握。包括授權接觸新的資料夾、重大的代碼行為例如刪除全部資料、代為發出電郵等。

## AI 指正

### LLM

應稱為「大語言模型」，不是「大語言模式」。OpenAI、Google、Anthropic 是公司；Claude 是 Anthropic 的模型系列，Claude Code 是 coding agent / 工具，不是 AI 公司。LLM 的核心是根據訓練和當前 context 預測下一個 token，進而生成文字、程式碼或結構化輸出。

### Prompt

拼法是 `prompt`。黑房比喻能幫助理解：prompt 不只是指令，也包括角色、目標、限制、背景資料、輸出格式、例子、評分標準和禁止事項。

### Context Window

Context window 不是「窗口訊息」，而是模型一次能讀入並處理的上下文容量。模型本身不會自動記得所有過去，除非那些內容被放進當前 context，或被系統用 memory、資料庫、RAG 等方式重新取回。

### Workflow

Workflow 是把任務拆成步驟，定義每一步的輸入、處理、工具、輸出和檢查點。Agent 通常是在 workflow 裡運行。

### Agent

Agent 不一定要完全獨立完成任務。更準確地說，agent 是由模型驅動，能根據目標規劃步驟、使用工具、讀寫資料、觀察結果並調整行動的系統。重點是它不只是回答，而是能在限制內行動。

### Tool Use

Tool use 不只是取得資訊，也包括執行動作，例如讀 GitHub repo、查鏈上資料、發 API request、跑測試、建立 issue、寫檔案。在 Web3 場景中，tool use 特別需要注意權限與風險。

### AI Coding

AI coding 不只是由 AI 編寫智能合約。更廣義是用 AI 協助寫程式、讀程式、改 bug、生成測試、解釋 repo、重構和審查安全風險。智能合約只是 Web3 場景中的其中一種應用。

### Guardrail

Guardrail 是安全護欄。它限制 AI / agent 可以做什麼、不可以做什麼，以及什麼情況下必須停止或要求人類確認。例如不能洩露 API key、不能自動轉帳、不能刪除整個資料夾、不能把未確認內容提交到平台。

### Tracing

Tracing 是追蹤 agent 工作過程的紀錄。它會記錄模型收到什麼輸入、做了什麼判斷、調用了什麼工具、工具回傳什麼、最後如何產生答案。用途是 debug、審計、安全檢查和改善 workflow。

### Human-in-the-loop

原理解方向正確。Human-in-the-loop 是在關鍵決策點加入人類確認，例如付款、發 email、push code、提交作業、刪除資料、修改權限、使用私密資料等。

## 修正版概念整理

### LLM

LLM 是大語言模型，根據訓練資料和當前 context 預測下一個 token，生成文字、程式碼或結構化輸出。

### Prompt

Prompt 是給 AI 的任務設計，包含角色、背景、目標、限制、輸出格式、語氣、例子和禁止事項。

### Context Window

Context window 是模型一次能讀取和處理的上下文容量。模型不會自然記得所有過去，除非資料被放入當前 context，或被系統重新取回。

### Workflow

Workflow 是完成任務的流程設計，定義每一步如何取得資料、分析、使用工具、產出結果和檢查。

### Agent

Agent 是由模型驅動、能根據目標規劃步驟、使用工具、觀察結果並調整行動的系統。它不只是回答問題，而是能在限制內執行任務。

### Tool Use

Tool use 是 AI 調用外部工具或 API 的能力，例如讀 GitHub、查鏈上資料、跑測試、寫檔案或取得錢包資料。

### AI Coding

AI coding 是用 AI 協助寫程式、改 bug、生成測試、理解 repo、審查風險；在 Web3 裡也包括智能合約開發。

### Guardrail

Guardrail 是安全護欄，用來限制 AI / agent 的行為，避免洩露秘密、錯誤操作、越權或自動執行高風險行為。

### Tracing

Tracing 是記錄 agent 工作過程的方法，用來追蹤模型判斷、工具調用、輸入輸出和錯誤，方便 debug 和審計。

### Human-in-the-loop

Human-in-the-loop 是在關鍵決策點加入人類確認，例如付款、刪除資料、提交作業、發送訊息或修改重要程式碼。

## Reflection

- 我原本較容易把 AI agent 想成「完全自主完成任務的 AI」，但更準確的理解是：agent 的自主性可以被 workflow、tool permissions、guardrails 和 human-in-the-loop 限制。
- 對 AI x Web3 來說，agent 的核心風險不只是回答錯誤，而是錯誤使用工具、越權調用 API、操作錢包或提交未確認內容。
- 後續學習 Agent、workflow 和 AI coding 時，需要同時看模型能力、工具邊界、審核流程與可追蹤紀錄。

