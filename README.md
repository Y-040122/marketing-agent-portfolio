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

## 本地真实 AI（Node.js 22+）

在启动服务的终端环境中配置 `OPENAI_API_KEY`，可选 `OPENAI_MODEL`，然后运行：

```sh
node server.mjs
```

打开 http://127.0.0.1:8089 。密钥仅从服务端环境读取，不写入网页。GitHub Pages 上的 `/api` 不存在，公开页明确使用固定演练模式，不伪装实时AI。

点击真实生成会把当前输入发往 OpenAI。请使用虚构或已获授权且脱敏的内容。服务只绑定本地回环地址、限制同源JSON请求、6000字输入、单次60秒超时、最多2200输出token、串行调用及每次启动30次限额。输出和修订不自动存储，可主动导出。

这不是完整自主Agent：提供需求诊断、采访生成和草稿审阅，决策、内容审核及对外发送由人完成。真实模型是否可用取决于服务端账号、权限、额度与网络。

### OpenAI 配置

将 `.env.example` 复制为同目录 `.env`，仅在 `.env` 内填写 OPENAI_API_KEY。服务启动时读取该文件；`.env` 已被 gitignore 排除且不在静态文件白名单内。

默认模型 `gpt-4.1-mini`，可通过 `OPENAI_MODEL` 修改为账号有权限调用的模型。使用官方 Responses API，`store:false`。ChatGPT 登录不会自动提供本项目API密钥。配置后重新运行 `node server.mjs`，打开 http://127.0.0.1:8089/#ai-lab 。

官方接口文档：https://developers.openai.com/api/reference/resources/responses/methods/create
