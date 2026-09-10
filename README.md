# context-audit

給 Claude Code 與 Codex Astra 使用的 context 稽核 skill。依使用者的任務、呼叫習慣與依賴關係，提出保留、改手動、停用或移除的建議。

重點是可重複使用的分析方法：找出 context 來源、檢查成本與使用證據，再評估節省量和功能取捨。沒有預設裁減名單，也不以固定使用頻率判定去留。

Token 精簡比例會依照個人需求與設定而有所差異。

## 版本

| 版本 | 入口 | 寫法 |
|---|---|---|
| Claude Code | [SKILL.md](claude/context-audit/SKILL.md) | 七步流程與完成條件，附 Claude 設定參考 |
| Codex Astra | [SKILL.md](codex/context-audit/SKILL.md) | 證據要求、判斷條件與交付標準，使用 Codex 的控制方式 |

兩版都是純文字 skill，不含執行腳本。Agent 使用當下可用的工具蒐集證據；缺少 token 測量或歷史紀錄時，標明限制並提供有條件的建議。

## 評估是否適合你

將以下文字貼給你平常使用的 LLM：

```text
請閱讀 https://github.com/coseto6125/context-audit 的 README 與適用於你目前平台的 skill 內容，根據你已知的我的工作習慣、常見任務與現有設定，評估是否適合採用。

請說明它能解決哪些實際問題、與現有做法有哪些重疊，以及採用後的取捨。給出適合採用、調整後採用或暫不採用的建議與理由；若缺少會影響判斷的資訊，再向我提問。先做評估，不要安裝或修改設定。
```

## 使用

Claude Code 用 `/context-audit`；Codex 用 `$context-audit`。例如：

> 檢查我的 context 負擔。我希望常用的 skill 自動啟用，偶爾使用的工具則願意手動呼叫。先給建議，不修改設定。

提供已有的 context 資訊、常見任務與偏好，有助於提出更合適的建議。Claude 版可使用 `/context all` 的輸出；Codex 版使用當下 runtime 提供的資訊。

輸出包含每個候選項目的來源、成本與測量狀態、使用及依賴證據、建議與取捨。只有在使用者要求執行且已有授權時才修改設定。

## 驗證狀態

- 兩版通過文件結構與引用檢查；Codex 版另通過 skill 格式驗證，並確認可被本機 Codex 辨識。

## 授權

[MIT](LICENSE)
