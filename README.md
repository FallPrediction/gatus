# 使用Docker啟動Gatus
使用Docker啟動[Gatus](https://github.com/TwiN/gatus)，並搭配簡單的財經網站API測試

## 為什麼選擇Gatus
- 從Client端呼叫API。假設有一個API有問題，即使都沒使用，Gatus也會發現
- 常見的監控系統有Prometheus + Grafana，入門門檻較高，相較之下Gatus更簡單，快速使用

## Gatus的用途
- Health dashboard監控服務健康狀態
    - HTTP
    - ICMP
    - TCP
    - DNS
- 自定義健康狀態條件
- 儲存監控紀錄
    - PostgreSQL
- 告警通知
    - Slack
    - Telegram
    - Email

## 監控設定
僅一個config.yaml檔即可設定所有的待測項目、告警設定等

[文檔](https://github.com/TwiN/gatus) 寫得非常詳細，但還是簡單列出寫法

- 監控endpoints列表
- name
- url
- interval：間隔多久呼叫一次
- conditions：符合這些條件才算通過
    - HTTP status code
    - Response time
    - Body的結構，是否存在key，array長度等等
    - Certificate是否即將過期
    - Domain是否即將過期

## 截圖
### 監控首頁
![監控首頁](blob/home%20page.jpg)
- 群組名稱
- endpoint名稱
- 平均回應時間
- 從舊到新顯示最近的檢查結果
    - 綠色：正常
    - 紅色：檢查不合格

### 監控內頁
![監控內頁](blob/a%20endpoint%20page.jpg)
- 時間軸顯示回應時間
- 最新健康狀態
- 最近事件
  - 監控開始日期
  - 監控有問題的日期
  - 回復正常的日期

### 告警
![告警](blob/telegram%20alert.jpg)
- 告警訊息
- send-on-resolved：是否觸發警報後後續不再告警
- failure-threshold：需要連續幾次檢查不通過才告警
