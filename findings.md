# Findings

## 2026-03-30 Report Facts

- The repository exposes two backend endpoints: `GET /health` and `POST /api/query`.
- The implemented ranking model uses four weighted dimensions: `match 40`, `risk 25`, `value 20`, `accessory 15`.
- The local data layer currently contains `100` Switch product samples, `4` query samples, and `4` expected ranking samples.
- The contract test file currently covers three paths: health check, clarification flow, and results flow.
- The repository does not include online production metrics such as CTR, conversion rate, or GMV, so these were excluded from the interview report.

## Source

- 主文档: `MVP_PRD.md`

## Key Observations

- 这是一个面向普通消费者的二手 Switch 导购 MVP，不是泛电商搜索系统。
- 产品核心价值是“帮助用户安心决策”，不是单纯追求低价。
- 模型只负责理解需求、补问、输出结构化过滤器和解析说明。
- 检索、过滤、排序、卡片组装全部归后端控制，模型不直接生成商品结果。
- 前端目标是提供简化卡片展示，不涉及复杂对话体验。
- MVP 必须支持本地 LLM 接入后的端到端运行。

## Mandatory MVP Capabilities

- 自然语言需求输入
- 最多 1 到 3 个必要补问
- 结构化筛选范围输出
- 后端硬过滤
- 后端综合排序
- 推荐理由与风险提示生成
- 简化卡片展示

## Explicit Non-Goals

- 非 Switch 品类扩展
- 长期多轮导购对话
- 图片理解
- 卖家信用体系
- 自动议价、自动下单、全网比价
- 跨会话偏好学习

## Key Domain Objects

- 商品基础信息
- 外观查验结果
- 功能查验结果
- 拆修浸液风险
- 核心配件信息
- 扩展配件信息
- 用户意图与结构化过滤条件
- 推荐理由与风险提示

## Initial Assumptions

- 第一版可以先用本地静态样本数据代替真实商品库。
- 第一版排序可以先采用可解释的规则打分，而不是机器学习排序。
- 第一版补问可以做成单轮追问，不强依赖复杂对话状态机。
- 第一版卡片摘要可由后端模板生成，不要求模型自由生成文案。

## Open Questions

- 商品数据源来自真实平台导出、人工构造样本，还是后续再接数据库。
- 成色等级、功能等级、风险等级是否已有统一业务定义。
- “箱说”是否需要拆分为原盒、说明书两个字段。
- 性价比分数是否需要外部市场价格基线。
- 本地 LLM 计划接入哪种模型与推理框架。

## Recommended Near-Term Deliverables

1. 模型输出 schema 文档
2. 后端过滤与排序规则文档
3. 本地样本数据文件
4. 前后端接口协议文档
5. 联调用例与验证记录模板
