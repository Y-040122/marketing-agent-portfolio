# 营销协作台 · Product Portfolio

一个内部营销工作台的中文产品作品集，以黑白响应式界面展示从达人筛选到需求、策略、选人、方案、执行和转化复盘的产品演进。

## 内容与边界

- 本地应用已实现：项目任务、策略表单、候选矩阵、模板方案、合作记录、转化计算及本地知识库。
- 此仓库为独立静态作品集，包含交互流程演示与转化计算器，不是完整内部应用。
- 所有人选、资质、报价、预算与效果指标均为模拟设定。
- 尚未接入真实AI、自动归因、团队共享、CRM或生产环境数据。
- 不包含账号、Token、`.env`、内部接口、客户身份、浏览器数据或内部项目截图。

## 本地预览

```sh
python3 -m http.server 8080
```

访问 http://localhost:8080 。不需要安装依赖或构建。

## GitHub Pages

在仓库 Settings → Pages 中选择 Deploy from a branch，分支 main，目录 / (root)。

## 文件

- index.html：案例叙事和展示界面
- style.css：黑白响应式样式
- script.js：六步流程演示、键盘切换和转化计算

## 设计参考

- https://www.ama.org/toolkits/creative-brief-template/
- https://help.asana.com/s/article/campaign-management?language=en-US
- https://support.google.com/google-ads/answer/1722022?hl=en-en

参考用于Brief结构与衡量思路，不代表平台背书。

## 本地真实 AI：火山方舟（Node.js 22+）

在同目录 `.env` 配置 `ARK_API_KEY` 和 `ARK_MODEL`，然后运行 `node server.mjs`。
打开 http://127.0.0.1:8089/#ai-lab 。

- 密钥入口：https://ark.volcengine.com/region:cn-beijing/apikey
- ARK_MODEL 使用账户已开通的 Model ID 或推理接入点ID；不自动猜测。
- 标准接口：https://ark.cn-beijing.volces.com/api/v3/chat/completions
- 本适配用于方舟标准数据面，不是 Coding Plan 专属接口。
- 密钥不进入浏览器、仓库或日志；`.env` 不在静态服务白名单内。
- 真实生成只发送当前输入到火山方舟；请使用虚构或已授权脱敏资料。
- GitHub Pages仅演练，真实AI运行于本地服务。
- 输入6000字、输出2200token、请求60秒超时，每次服务启动最多30次调用。
- 保留OpenAI本地配置不会调用它；当前服务只读取ARK_API_KEY与ARK_MODEL。

官方文档：https://docs.volcengine.com/docs/ark/chat-api?lang=zh
