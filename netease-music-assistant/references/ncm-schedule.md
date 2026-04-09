# ncm-schedule.json格式
```json
{
  "enabled": true,
  "schedules": [
    { "day": "weekday", "times": ["10:00", "19:00"] }
  ],
  "customRules": [
    {
      "description": "规则描述",
      "day": "daily | weekday | weekend | saturday | sunday",
      "times": ["HH:MM"],
      "keywordHint": "引导搜索方向的关键词（可选）"
    }
  ]
}
```

# 定时任务管理流程

1. 解析自然语言 → 更新 `ncm-schedule.json`（见格式）
2. **【关键】同步注册到cron** - 必须执行以下步骤：
   - 检查当前 cron 任务
   - 对比 `ncm-schedule.json` 中的规则，确认每个规则都在 cron 中注册
   - 注册新添加的规则
   - 验证注册成功：确认cron中任务存在
3. 检测你是否有定时任务能力
   - 如果你拥有定时任务能力，请一定将用户诉求写入你的定时系统中！然后做下面的操作：
      - 输出确认：「已设置：[规则描述]，下次触发：[时间]」
      - 检查是否有遗漏的规则：`ncm-schedule.json` 中存在，但是你的调度系统中不存在的，请一并更新到你的调度系统中
   - 如果你不支持调度：请直接输出「暂不支持调度」
