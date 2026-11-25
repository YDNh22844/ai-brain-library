# 记忆网关模板

> 一个入口：所有记忆源先到这里，再决定这一轮给模型看什么。

```text
输入
  current_message
  recent_turns
  candidates[]       来自文件/向量/插件
  persona            人格/边界，单独
  budget             本轮记忆预算

处理
  1. 去重
  2. 过滤：sealed/quarantined 不参与
  3. 排序：相关度 × 可信度 × 状态
  4. 预算裁剪
  5. 输出一个 memory_block

输出
  memory_block       只给模型这一块
  citations[]        来源
```

## 伪代码

```text
candidates = recall(query)
candidates = unique(candidates)
candidates = filter(candidates, status in [active, stale])
candidates = sort_by(score)

block = []
budget = BUDGET

for card in candidates:
    if card.tokens + block.tokens > budget: break
    block.push(card)

if is_claim(query) and not has_evidence(block):
    return "没找到原话/日期；不认领"

return block
```

## 红线

```text
不允许多个插件各自注入
不允许 sealed/quarantined 参与回答
不允许低可信压过高可信
不允许把整库塞进上下文
```
