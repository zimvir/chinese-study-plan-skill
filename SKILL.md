---
name: chinese-study-plan
description: 帮助用户制定高效的 中国应试教育 学习计划，科学、详细、可落实
---

# 中国应试教育学习计划

## 触发条件

- `/plan-ch-study`
- "帮我做一下这个学期/这个阶段的学习计划"
- "帮我做个学习计划"

## 工作流程

### Step 1 调查目标信息

收集以下4项基础数据：

1. **各科分数**：你现在的各科分数是多少？（如：语/数/英/物/化/政）
2. **目标院校或目标分数**：你的目标院校是哪个？或者高考想考多少分？
3. **时间情况**：你每天什么时候到家？到家后能学习多长时间？
4. **各科强弱**：你哪科比较擅长、哪科比较吃力？

> 如果用户信息不完整，用提问逐步补全，不要一次性发4个问题。

### Step 2 确定计划大纲

根据用户信息，计算：
- 提高分数 = 目标分数 - 当前分数
- 各科差距 = 各科目标 - 各科当前

输出6部分大纲：
1. **靶子确认**：目标分数、目标院校、差距
2. **差距拆解**：各科分数逆推表（今天→每个节点→高考）
3. **时间分配**：两阶段起止时间（知识学习期 / 总复习提分期）
4. **第一、二阶段里程碑**：知识期的关键节点及其验证方式
5. **风险提示**：计划中的主要风险点
6. **确认后进入Step 3**：告知用户"确认后进入Step 3生成每周详细计划"

> 输出格式：纯Markdown表格，不用emoji装饰

### Step 3 生成每周详细计划

在用户确认Step 2大纲后，根据：
- 大纲中的时间节点
- 用户实际可用时间（每日时长、每周哪天可全天学习）

生成：
1. **每周任务清单**（按阶段列出前几周，后续可迭代）
2. **每日执行模板**（如22:00到家后的时间分配）
3. **周末执行模板**（周六全天 + 周日晚上计划制定）
4. **MIT每日清单模板**（可打印/手写）
5. **里程碑周**（关键节点检查点）

---

## 输出格式规范

- 使用纯Markdown格式
- 表格用Markdown表格语法
- 不用emoji装饰输出内容
- 计划内容要具体可执行（时间、页码、任务量都要有）

---

## 参考文件
### 必要参考文件
- `prompts/plan_outline.md` — Step 2 大纲输出模板
- `prompts/weekly_plan.md` — Step 3 每周计划模板
- `references/core/two_study_stage.md` — 两阶段方法论

### 知识库性文件（RAG模式，用户问到相关话题时再读取）
- `references/core/goal_planning_methodology/outline.yaml` — 目标规划方法论索引
- `references/core/chinese_high_school_subjects_learning_methods/outline.yaml` — 高中各科学习方法索引
- `references/knowledge/goal_planning_methodology/results/` — 具体方法论（按需读取）
- `references/knowledge/chinese_high_school_subjects_learning_methods/results/` — 各科学习方法（按需读取）