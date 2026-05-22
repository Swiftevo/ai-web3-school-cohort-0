# Week 1: EOA、智能帳戶與多簽帳戶權限比較

## Metadata

- Date: 2026-05-22
- Task: 比較 EOA、智能帳戶和多簽帳戶的權限差異
- Status: Proof-of-Work note
- Related repo: https://github.com/Swiftevo/ai-web3-school-cohort-0

## Goal

理解三類 Web3 帳戶在「誰能發起交易、誰能批准、誰承擔風險」上的差異，為後續測試網交易、合約調用、錢包確認、agent wallet 和鏈上驗證任務建立共同語言。

## Summary

EOA、智能帳戶和多簽帳戶的最大差別，不只是錢包長相不同，而是「控制權在哪裡」不同。

- EOA：控制權集中在一把 private key。
- 智能帳戶：控制權由智能合約邏輯管理。
- 多簽帳戶：控制權由多個簽名者共同管理，達到門檻才執行。

## Comparison Table

| 維度 | EOA | 智能帳戶 | 多簽帳戶 |
|---|---|---|---|
| 控制權由誰持有 | 單一 private key 控制。誰掌握 private key 或 seed phrase，誰就控制帳戶。 | 由智能合約邏輯控制，可設定 owner、session key、guardian、policy 等規則。 | 由多個簽名者共同控制，通常設定 M-of-N 門檻，例如 2-of-3、3-of-5。 |
| 誰可以發起交易 | private key 持有人可直接簽名並送出交易。 | 被合約授權的 owner、session key、relayer 或自動化流程可根據規則發起。 | 任一授權簽名者通常可以提出交易，但需要足夠簽名者批准後才可執行。 |
| 誰可以批准交易 | 同一個 private key 簽名即批准。 | 由智能帳戶內的規則決定，例如 owner 批准、限額內自動批准、超額需額外確認。 | 多個簽名者按門檻批准，例如 2 人同意才執行。 |
| 是否支持多人確認 | 原生不支持。若要多人確認，需要依賴外部流程或合約。 | 可以支持，但取決於智能帳戶設計。 | 原生支持，是多簽帳戶的核心能力。 |
| 是否支持恢復 | 原生不支持。seed phrase 或 private key 丟失通常很難恢復。 | 可支持社交恢復、guardian、backup key、延遲恢復等機制。 | 可透過替換 signer、調整門檻等方式處理成員變動，但仍取決於多簽合約與治理流程。 |
| 是否支持限額 | 原生不支持。 | 可支持每日限額、單筆限額、token allowlist、dApp allowlist 等策略。 | 可透過政策或模組支持，但基礎多簽主要依賴多人批准。 |
| 是否支持自動化策略 | 原生不支持。EOA 自動化通常意味著把 private key 交給程式，風險很高。 | 可支持 session key、定時任務、策略執行、paymaster 或 agent wallet。 | 可支持部分自動化，但高風險操作通常仍需要多簽批准。 |
| 典型使用場景 | 個人錢包、測試網操作、日常 dApp 連接、小額交易。 | 遊戲錢包、agent wallet、社交恢復錢包、限額付款、批量交易、降低使用者操作成本。 | DAO treasury、團隊資產管理、合約 admin 權限、項目金庫、多人成本批准流程。 |
| 主要風險點 | 單點失效。private key 或 seed phrase 洩露即可能失去全部控制權；簽錯交易也難以撤回。 | 合約 bug、錯誤 policy、過度授權 session key、升級權限被濫用、依賴 relayer 或 paymaster。 | 簽名者串通、簽名者遺失 key、門檻設定不合理、操作流程慢、有人批准不理解的交易。 |

## Account Types

### EOA

EOA 是 Externally Owned Account，由 private key 直接控制。一般使用者透過 MetaMask 等 wallet 建立和操作的帳戶，多數都是 EOA。

適用場景：

- 個人測試網操作。
- 小額 dApp 互動。
- 學習交易簽名、gas、nonce 和 transaction lifecycle。

風險點：

- seed phrase 或 private key 一旦洩露，攻擊者可以直接轉走資產。
- EOA 沒有原生多人審批、限額或社交恢復。
- 自動化操作若需要把 private key 放到 script 或 server，風險非常高。

### 智能帳戶

智能帳戶是由智能合約邏輯控制的帳戶。它可以把「誰能操作、可操作多少、何時需要額外確認」寫成規則。

適用場景：

- Agent wallet：讓 AI agent 在限額、限時、限定工具內操作。
- 遊戲或 consumer app：降低使用者每一步都簽名的摩擦。
- 需要恢復機制的個人錢包。
- 批量交易或 gas sponsorship。

風險點：

- 合約邏輯有 bug 可能導致資產或權限失控。
- Session key 權限設得太寬，可能讓 agent 或 dApp 做超出預期的操作。
- 升級權限、guardian 或 relayer 若被控制，可能成為新的攻擊面。

### 多簽帳戶

多簽帳戶通常也是智能合約帳戶，但它的核心是「多人批准」。例如 3 位 signer 中至少 2 位同意，交易才會執行。

適用場景：

- DAO 或團隊 treasury。
- 管理合約 admin 權限。
- 項目方支付、grant、預算批准。
- 高價值資產或高風險操作。

風險點：

- 門檻太低，容易被少數人控制；門檻太高，可能無法及時操作。
- 簽名者若不理解 transaction data，可能批准錯誤或惡意交易。
- 多人串通或多個 key 同時被攻擊，仍可能造成損失。

## Who Can Initiate, Approve, And Bear Risk

| 問題 | EOA | 智能帳戶 | 多簽帳戶 |
|---|---|---|---|
| 誰能發起交易 | private key 持有人 | 被合約 policy 授權的人或流程 | 任一授權 signer 通常可提出 |
| 誰能批准交易 | private key 持有人 | 合約規則指定的 owner、guardian、policy 或 threshold | 達到門檻的多個 signer |
| 誰承擔風險 | private key 持有人 | 設計 policy 的人、owner、使用者和依賴該帳戶的系統 | signer 群體、treasury 成員、DAO 或團隊 |

## Operations That Must Require Human Confirmation

以下操作不應讓 agent 或自動化流程直接執行，應加入 human-in-the-loop：

- 轉出真實資產或高價值 token。
- 授權 token allowance，尤其是 unlimited approval。
- 修改智能帳戶 owner、guardian、session key 或限額。
- 升級智能合約或修改 proxy implementation。
- 執行多簽 treasury 支出。
- 添加或移除 multisig signer。
- 修改 multisig threshold。
- 部署或調用未驗證合約。
- 對不熟悉的 transaction data 簽名。
- 提交會影響公開身份、資產或項目聲譽的鏈上操作。

## Agent Wallet Implication

對 AI agent 來說，EOA 最危險，因為一旦 agent 或 script 取得 private key，就可能直接發起任何交易。智能帳戶比較適合 agent wallet，因為可以限制權限、時間、金額和可調用合約。多簽帳戶適合保護團隊資產與高風險決策，但不適合每一個低風險小操作都走多人審批。

比較合理的設計是：

- 日常低風險操作：智能帳戶 + session key + 限額。
- 高價值資產：多簽帳戶管理。
- 測試與學習：EOA 可用，但不放真實大額資產。
- 所有高風險操作：必須人工確認。

## Reflection

這三類帳戶的差異，可以用一句話總結：

> EOA 把控制權放在一把 key；智能帳戶把控制權放在合約規則；多簽帳戶把控制權分散給多個 signer。

後續做測試網交易、合約調用或 agent wallet 設計時，不能只問「能不能發交易」，還要問「誰批准、誰負責、誰可以停止、出錯後能不能恢復」。

