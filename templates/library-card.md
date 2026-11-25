# 记忆卡模板

```markdown
# 卡片标题

> 状态：active
> 来源：谁说的 / 哪来的（原话、链接、文件）
> 日期：YYYY-MM-DD
> 置信：confirmed / observed / inferred / unconfirmed
> 有效期：长期 / 到某日 / 需复核

## 内容

一段话，写清楚事实/记录/叙事/个体理解中的哪一种。

## 关键词

关键词1, 关键词2, 关键词3

## 来源锚点

- 原始路径 / 事件 / 消息 ID：
- 相关卡：
```

## 规则

```text
没有来源 → status: unconfirmed，进待核实
过期 → status: stale
停止使用 → status: sealed
可疑/被塞 → status: quarantined
不要删除，除非用户明确要求
```
