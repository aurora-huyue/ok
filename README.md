# ok

graph TD
    subgraph "告警生命周期"
    direction TB

    Start(fa:fa-play 告警产生) --> Active

    Active -- 抑制规则匹配 --> Suppressed
    Suppressed -- 抑制条件解除 --> Active

    Active -- 人工确认 --> Acknowledged
    Suppressed -- 人工确认 --> Acknowledged
    Acknowledged -- 问题复现 --> Active

    Active -- 手动忽略 --> Ignored
    Suppressed -- 手动忽略 --> Ignored
    Acknowledged -- 手动忽略 --> Ignored

    Active -- 问题恢复 --> Resolved
    Suppressed -- 问题恢复 --> Resolved
    Acknowledged -- 问题恢复/工单关闭 --> Resolved

    Resolved -- 自动/手动关闭 --> Closed(fa:fa-stop 已关闭)
    Ignored -- 自动/手动关闭 --> Closed

    end
