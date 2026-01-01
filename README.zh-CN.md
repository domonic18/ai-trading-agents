<p align="center">
  <img src="docs/assets/TauricResearch.png" style="width: 60%; height: auto;">
</p>

<div align="center" style="line-height: 1;">
  <a href="https://arxiv.org/abs/2412.20138" target="_blank"><img alt="arXiv" src="https://img.shields.io/badge/arXiv-2412.20138-B31B1B?logo=arxiv"/></a>
  <a href="https://discord.com/invite/hk9PGKShPK" target="_blank"><img alt="Discord" src="https://img.shields.io/badge/Discord-TradingResearch-7289da?logo=discord&logoColor=white&color=7289da"/></a>
  <a href="./docs/assets/wechat.png" target="_blank"><img alt="WeChat" src="https://img.shields.io/badge/WeChat-TauricResearch-brightgreen?logo=wechat&logoColor=white"/></a>
  <a href="https://x.com/TauricResearch" target="_blank"><img alt="X Follow" src="https://img.shields.io/badge/X-TauricResearch-white?logo=x&logoColor=white"/></a>
  <br>
  <a href="https://github.com/TauricResearch/" target="_blank"><img alt="Community" src="https://img.shields.io/badge/Join_GitHub_Community-TauricResearch-14C290?logo=discourse"/></a>
</div>

<div align="center">
  <a href="README.md">English</a> | <strong>中文</a>
</div>

---

# TradingAgents: 多智能体 LLM 金融交易框架

> 🎉 **TradingAgents** 正式发布！我们收到了大量关于这项工作的咨询，在此感谢社区的热情支持。
>
> 因此我们决定完全开源这个框架。期待与您一起构建有影响力的项目！

<div align="center">

🚀 [框架介绍](#tradingagents-框架) | ⚡ [安装与CLI](#安装与命令行) | 🎬 [演示视频](https://www.youtube.com/watch?v=90gr5lwjIho) | 🤝 [贡献](#贡献) | 📄 [引用](#引用)

</div>

## TradingAgents 框架

TradingAgents 是一个模拟真实交易公司动态的多智能体交易框架。通过部署专业的 LLM 驱动智能体——从基本面分析师、情绪专家和技术分析师，到交易员和风险管理团队，平台协作评估市场状况并指导交易决策。此外，这些智能体通过动态讨论来确定最佳策略。

<p align="center">
  <img src="docs/assets/schema.png" style="width: 100%; height: auto;">
</p>

> TradingAgents 框架专为研究目的设计。交易表现可能因多种因素而异，包括所选的骨干语言模型、模型温度、交易周期、数据质量和其他非确定性因素。[不构成财务、投资或交易建议。](https://tauric.ai/disclaimer/)


## 安装与命令行

### 安装

克隆仓库：
```bash
git clone https://github.com/domonic18/ai-trading-agents.git
cd ai-trading-agents
```

#### 方式一：使用 uv 安装

```bash
# 安装 uv
curl -LsSf https://astral.sh/uv/install.sh | sh

# 切换到后端目录
cd backend

# 创建虚拟环境并安装依赖
uv sync

# 安装可选依赖（中国市场、数据库、可视化）
uv sync --extra all
```

#### 方式二：使用 pip 安装

```bash
# 切换到后端目录
cd backend

# 创建虚拟环境
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate

# 安装依赖
pip install -e .

# 安装可选依赖
pip install -e ".[all]"  # 所有可选功能
pip install -e ".[chinese,database]"  # 特定功能
```

### 配置

```bash
cp .env.example .env
# 编辑 .env 填入您的 API 密钥
```

**仅分析美股时**：
```env
# OpenAI或Google AI (选择一个)
OPENAI_API_KEY=your_openai_api_key_here
# 或者
GOOGLE_API_KEY=your_google_api_key_here

# FinnHub (金融数据必需)
FINNHUB_API_KEY=your_finnhub_api_key_here
```

**分析中国A股或使用百炼LLM时**：
```env
# 百炼 (中国股票或通义千问模型必需)
DASHSCOPE_API_KEY=your_dashscope_api_key_here

# FinnHub (金融数据必需)
FINNHUB_API_KEY=your_finnhub_api_key_here
```

**注意**：
- **百炼API密钥仅在以下情况需要**：
  - 分析中国A股股票 (使用通达信数据 + 百炼embeddings)
  - 选择百炼作为LLM提供商 (通义千问模型)
- **分析美股使用OpenAI/Google模型时**: 不需要百炼

### CLI 使用

从项目根目录运行 CLI：

```bash
# 激活虚拟环境
source backend/.venv/bin/activate

# 切换到后端目录
cd backend

# 启动cli
python -m cli.main
```

您将看到一个交互界面，可以选择股票代码、日期、LLM、研究深度等。

<p align="center">
  <img src="docs/assets/cli/cli_init.png" width="100%" style="display: inline-block; margin: 0 2%;">
</p>

运行时会出现一个界面，实时显示结果加载，让您跟踪智能体的进度。

<p align="center">
  <img src="docs/assets/cli/cli_news.png" width="100%" style="display: inline-block; margin: 0 2%;">
</p>

<p align="center">
  <img src="docs/assets/cli/cli_transaction.png" width="100%" style="display: inline-block; margin: 0 2%;">
</p>

## 感谢

感谢 [Tauric Research](https://github.com/TauricResearch) 团队创造的革命性多智能体交易框架 **TradingAgents**！

本项目基于他们在多智能体 LLM 金融交易系统方面的开创性工作。他们通过专业化 AI 智能体模拟真实交易公司动态的创新方法，为金融研究和分析开辟了新的可能性。

我们也感谢更广泛的开源社区，正是他们的工具和库使这项研究成为可能。本项目仅用于教育和研究目的。

## 免责声明

**重要提示：股市投资有风险，入市需谨慎。**

本框架严格用于研究和教育目的。本系统生成的交易决策、分析和建议：

- **不构成财务、投资或交易建议**
- **不保证未来的表现或利润**
- **基于历史数据和 AI 模型，可能无法准确预测未来市场状况**

股市投资涉及巨大的损失风险，可能并不适合所有投资者。您应该：

1. **永远不要投资您无法承受损失的资金**
2. **在做任何投资决策之前，进行自己的研究和尽职调查**
3. **在做投资选择之前咨询合格的财务顾问**
4. **注意过去的表现并不保证未来的结果**

开发者、贡献者和原始 Tauric Research 团队：

- **对使用本系统造成的任何财务损失不承担任何责任**
- **不建议将此框架用于实际交易决策**
- **强烈建议仅将此工具作为辅助研究工具，而不是作为主要决策系统**

使用本软件，即表示您了解这些风险并接受对您所做的任何投资决策承担全部责任。
