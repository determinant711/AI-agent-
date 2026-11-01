---
day: 0
date: "2026-11-01"
week: 0
phase: "诊断"
status: planned
score: ""
minutes: 0
synced: false
answer_key: ".coach/answer-keys/2026-11-01-diagnostic.md"
tags: ["diagnostic"]
---

# Day 000 · 2026-11-01 · 诊断日

## 今日目标

用 5 道题判断起点：Python 语义、调试边界、类型/测试、LLM 应用、Agent 设计。
**诊断不计入正式周计划**，只决定从第几周开始。

**预计：** 30 分钟（Q1 3' / Q2 6' / Q3 8' / Q4 6' / Q5 7'）

## 题目

### Q1 · [基础][易错] 默认参数

```python
def add_tag(tag, tags=[]):
    tags.append(tag)
    return tags

print(add_tag("python"))
print(add_tag("agent"))
```

写出两次 `print` 的输出，并解释为什么。若要保持“每次调用默认得到空列表”的语义，怎么改？

**要求：** 先不要运行代码；写出输出和理由。
**验收：** 能说清默认参数在什么时候求值，并给出修复。

### Q2 · [基础] 空输入与边界

```python
def average(nums):
    total = 0
    for i in range(len(nums)):
        total += nums[i]
    return total / len(nums)
```

指出至少两个会让这个函数失败的输入，修复它，并写一个 pytest 用例覆盖其中一个失败场景。

**要求：** 说明每个输入为什么失败。
**验收：** 修复后对空列表有明确行为；测试可运行。

### Q3 · [重点] 工具参数的数据结构

定义一个 `ToolCall` 数据结构，包含：

- `name: str`
- `arguments: dict[str, Any]`
- `call_id: str`

实现：

```python
def parse_tool_call(payload: dict) -> ToolCall:
    ...
```

要求：字段缺失或类型不对时抛出 `ValueError`，错误信息要能指出是哪个字段。再写两个 pytest 用例：一个合法输入，一个字段缺失。

**要求：** 可以用 `dataclass`，不要用 Pydantic。
**验收：** 合法输入返回 `ToolCall`；缺字段时异常信息可读。

### Q4 · [重点][岗位相关] 解析模型返回的 JSON

模型可能返回下面三种文本：

```text
{"name": "张三", "age": 28}
```

````text
```json
{"name": "张三", "age": 28}
```
````

```text
这是结果：{"name": "张三", "age": 28} 希望有帮助。
```

实现 `parse_model_json(text: str) -> dict`：能从这三种文本中取出 JSON 对象；
解析失败或结果不是对象时抛出 `ValueError`。不要调用真实模型。

**要求：** 说明你的提取策略和至少一个失败场景。
**验收：** 三种输入都能处理；坏 JSON 不会被静默吞掉。

### Q5 · [重点][岗位相关] Agent 工具选择

场景：Agent 有两个工具：

- `get_order(order_id)`：查询订单，订单不存在时返回 `404`
- `search_docs(query)`：检索退款政策文档

用户问：**“订单 A123 的退款政策是什么？”**

写出 5–10 行伪代码，说明：

1. 先调用哪个工具、为什么；
2. `get_order` 返回 404 时怎么处理；
3. 如何避免无限循环；
4. 最终答案如何带上政策来源；
5. 你会用哪些指标判断这个 Agent 是否变好。

**要求：** 伪代码即可，不要求可运行；重点写失败处理和评测。
**验收：** 有明确终止条件；404 不会被当成“订单存在但无政策”。

## 我的作答

（把 Q1–Q5 的答案贴到这里，或直接在对话里提交）

## 详细解析

（用户提交后填写）

## 踩坑记录

（批改后填写）

## 今日总结

- 起点判断：
- 最该补的短板：
- 前两周策略：
- 用时：
