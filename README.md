# bpkb-minimum-repository

## 1) Repo 目的
本 repo 是 Best Practice Knowledge Base（BPKB）的最小可用資料層，用來承載 AI 商業模板研究實驗室的核心知識資料。

## 2) 什麼是 BPKB
BPKB 是一套可持續累積與回寫的知識結構，管理 Source、Pattern、Module、Template、Inquiry、Validation、Research Queue。

## 3) 目錄結構
- `docs/`：規範文件（如來源分級）
- `schemas/`：JSON Schema
- `data/`：主資料檔
- `seed-packs/`：主題型種子資料入口
- `exports/`：匯出資料
- `research-queue/`：研究工作流補充檔案

## 4) 各資料用途
- Source：來源與權威級別
- Pattern：可重用方法模式
- Module：系統模組地圖（Z01-Z12）
- Template：可操作模板
- Inquiry：客戶需求訊號（Demand Signal）
- Validation：實務驗證結果
- Research Queue：待研究任務與產出連結

## 5) evidence_status 定義
- `hypothesis`
- `source_backed_pending`
- `source_backed`
- `cross_validated`
- `field_validated`

> 注意：本 repo 不會把 GPT 推演直接視為正式 Best Practice。

## 6) Source Authority Ladder
詳見 `docs/source-authority-ladder.md`，分為 S/A/B/C/D/E。

## 7) 如何新增 Source
1. 依 `schemas/sources.schema.json` 新增一筆至 `data/sources.json`。
2. 補齊 authority_level、url、summary。

## 8) 如何新增 Pattern
1. 依 `schemas/patterns.schema.json` 新增至 `data/patterns.json`。
2. 必填 `evidence_status`、`source_required=true`、`source_ids`。

## 9) 如何新增 Template
1. 依 `schemas/templates.schema.json` 新增至 `data/templates.json`。
2. 必填 `evidence_status` 與來源欄位。

## 10) 如何記錄 Inquiry / Demand Signal
依 `schemas/inquiries.schema.json` 寫入 `data/inquiries.json`，並設定 `recommended_research_priority`。

## 11) 如何新增 Research Queue 任務
依 `schemas/research_queue.schema.json` 寫入 `data/research_queue.json`，關聯 `trigger_reference`（如 inquiry_id）。

## 12) 如何回寫 Validation
依 `schemas/validations.schema.json` 寫入 `data/validations.json`，並更新相關 pattern/template 的 evidence_status。

## 13) 未來升級方向
本資料層可進一步升級為：
- Web App
- Database
- Agent Retrieval / workflow orchestration

## 14) 現階段限制
目前不負責：
- 自動上網 research
- 自動判斷 Best Practice
- 自動提案生成

## V0.1 暫不做事項
1. Web App
2. 登入系統
3. 多租戶
4. 自動爬網
5. 自動上網 research
6. Vector Search
7. RAG
8. 大型知識圖譜
9. 自動生成 proposal
10. 自動判斷 Best Practice
