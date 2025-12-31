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
<a href="https://www.star-history.com/#TauricResearch/TradingAgents&Date">
 <picture>
   <source media="(prefers-color-scheme: dark)" srcset="https://api.star-history.com/svg?repos=TauricResearch/TradingAgents&type=Date&theme=dark" />
   <source media="(prefers-color-scheme: light)" srcset="https://api.star-history.com/svg?repos=TauricResearch/TradingAgents&type=Date" />
   <img alt="TradingAgents Star History" src="https://api.star-history.com/svg?repos=TauricResearch/TradingAgents&type=Date" style="width: 80%; height: auto;" />
 </picture>
</a>
</div>

<div align="center">

🚀 [框架介绍](#tradingagents-框架) | ⚡ [安装与CLI](#安装与命令行) | 🎬 [演示视频](https://www.youtube.com/watch?v=90gr5lwjIho) | 📦 [包使用](#tradingagents-包) | 🤝 [贡献](#贡献) | 📄 [引用](#引用)

</div>

## TradingAgents 框架

TradingAgents 是一个模拟真实交易公司动态的多智能体交易框架。通过部署专业的 LLM 驱动智能体——从基本面分析师、情绪专家和技术分析师，到交易员和风险管理团队，平台协作评估市场状况并指导交易决策。此外，这些智能体通过动态讨论来确定最佳策略。

<p align="center">
  <img src="docs/assets/schema.png" style="width: 100%; height: auto;">
</p>

> TradingAgents 框架专为研究目的设计。交易表现可能因多种因素而异，包括所选的骨干语言模型、模型温度、交易周期、数据质量和其他非确定性因素。[不构成财务、投资或交易建议。](https://tauric.ai/disclaimer/)

我们的框架将复杂的交易任务分解为专业角色，确保系统实现稳健、可扩展的市场分析和决策方法。

### 分析师团队
- **基本面分析师**：评估公司财务和绩效指标，识别内在价值和潜在风险信号。
- **情绪分析师**：使用情绪评分算法分析社交媒体和公众情绪，评估短期市场情绪。
- **新闻分析师**：监控全球新闻和宏观经济指标，解读事件对市场状况的影响。
- **技术分析师**：利用技术指标（如 MACD 和 RSI）检测交易模式并预测价格走势。

<p align="center">
  <img src="docs/assets/analyst.png" width="100%" style="display: inline-block; margin: 0 2%;">
</p>

### 研究员团队
- 由看涨和看跌研究员组成，他们批判性评估分析师团队提供的洞察。通过结构化辩论，平衡潜在收益与内在风险。

<p align="center">
  <img src="docs/assets/researcher.png" width="70%" style="display: inline-block; margin: 0 2%;">
</p>

### 交易员智能体
- 综合分析师和研究员的报告做出明智的交易决策。根据全面的市场洞察确定交易时机和规模。

<p align="center">
  <img src="docs/assets/trader.png" width="70%" style="display: inline-block; margin: 0 2%;">
</p>

### 风险管理和投资组合经理
- 通过评估市场波动性、流动性和其他风险因素，持续评估投资组合风险。风险管理团队评估和调整交易策略，为投资组合经理的最终决策提供评估报告。
- 投资组合经理批准/拒绝交易提案。如果批准，订单将发送到模拟交易所并执行。

<p align="center">
  <img src="docs/assets/risk.png" width="70%" style="display: inline-block; margin: 0 2%;">
</p>

## 安装与命令行

### 安装

克隆 TradingAgents：
```bash
git clone https://github.com/TauricResearch/TradingAgents.git
cd TradingAgents
```

#### 推荐：使用 uv（快速包管理器）

[uv](https://github.com/astral-sh/uv) 是最快的 Python 包管理器：

```bash
# 安装 uv
curl -LsSf https://astral.sh/uv/install.sh | sh

# 创建虚拟环境并安装依赖
uv sync

# 安装可选依赖（中国市场、数据库、可视化）
uv sync --extra all
```

#### 备选：使用 pip

```bash
# 创建虚拟环境
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate

# 安装依赖
pip install -e .

# 安装可选依赖
pip install -e ".[all]"  # 所有可选功能
pip install -e ".[chinese,database]"  # 特定功能
```

### 必需的 API

您需要 OpenAI API 用于所有智能体，以及 [Alpha Vantage API](https://www.alphavantage.co/support/#api-key) 获取基本面和新闻数据（默认配置）。

```bash
export OPENAI_API_KEY=$YOUR_OPENAI_API_KEY
export ALPHA_VANTAGE_API_KEY=$YOUR_ALPHA_VANTAGE_API_KEY
```

或者，您可以在项目根目录创建 `.env` 文件来存储 API 密钥（参考 `.env.example`）：
```bash
cp .env.example .env
# 编辑 .env 填入您的 API 密钥
```

**注意：** 我们很高兴与 Alpha Vantage 合作，为 TradingAgents 提供强大的 API 支持。您可以[在这里](https://www.alphavantage.co/support/#api-key)免费获取 AlphaVantage API，TradingAgents 的请求速率限制提升至每分钟 60 次且无每日限制。通常这个配额足以执行 TradingAgents 的复杂任务，这得益于 Alpha Vantage 的开源支持计划。如果您更喜欢使用 OpenAI 获取这些数据源，可以修改 `backend/tradingagents/default_config.py` 中的数据供应商设置。

### CLI 使用

您可以直接运行 CLI：

```bash
# 使用 uv
uv run python -m cli.main

# 或使用已安装的命令
tradingagents
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

## TradingAgents 包

### 实现细节

我们使用 LangGraph 构建 TradingAgents 以确保灵活性和模块化。我们的实验使用 `o1-preview` 和 `gpt-4o` 作为深度思考和快速思考 LLM。但是，为了测试目的，我们建议您使用 `o4-mini` 和 `gpt-4.1-mini` 以节省成本，因为我们的框架会进行**大量** API 调用。

### Python 使用

要在代码中使用 TradingAgents，您可以导入 `tradingagents` 模块并初始化 `TradingAgentsGraph()` 对象。`.propagate()` 函数将返回决策。您可以运行 `main.py`，这里有一个快速示例：

```python
from backend.tradingagents.graph.trading_graph import TradingAgentsGraph
from backend.tradingagents.default_config import DEFAULT_CONFIG

ta = TradingAgentsGraph(debug=True, config=DEFAULT_CONFIG.copy())

# 前向传播
_, decision = ta.propagate("NVDA", "2024-05-10")
print(decision)
```

您还可以调整默认配置来设置自己的 LLM 选择、辩论轮数等。

```python
from backend.tradingagents.graph.trading_graph import TradingAgentsGraph
from backend.tradingagents.default_config import DEFAULT_CONFIG

# 创建自定义配置
config = DEFAULT_CONFIG.copy()
config["deep_think_llm"] = "gpt-4.1-nano"  # 使用不同的模型
config["quick_think_llm"] = "gpt-4.1-nano"  # 使用不同的模型
config["max_debate_rounds"] = 1  # 增加辩论轮数

# 配置数据供应商（默认使用 yfinance 和 Alpha Vantage）
config["data_vendors"] = {
    "core_stock_apis": "yfinance",           # 选项: yfinance, alpha_vantage, local
    "technical_indicators": "yfinance",      # 选项: yfinance, alpha_vantage, local
    "fundamental_data": "alpha_vantage",     # 选项: openai, alpha_vantage, local
    "news_data": "alpha_vantage",            # 选项: openai, alpha_vantage, google, local
}

# 使用自定义配置初始化
ta = TradingAgentsGraph(debug=True, config=config)

# 前向传播
_, decision = ta.propagate("NVDA", "2024-05-10")
print(decision)
```

> 默认配置使用 yfinance 获取股价和技术数据，使用 Alpha Vantage 获取基本面和新闻数据。用于生产环境或遇到速率限制时，建议升级到 [Alpha Vantage Premium](https://www.alphavantage.co/premium/) 以获得更稳定可靠的数据访问。对于离线实验，有一个本地数据供应商选项，使用我们的 **Tauric TradingDB**（一个用于回测的精选数据集），但这仍在开发中。我们正在完善这个数据集，计划在即将到来的项目中发布。敬请期待！

您可以在 `backend/tradingagents/default_config.py` 中查看完整的配置列表。

## 🌟 新功能概览

### 🇨🇳 中国 A 股支持

- **支持交易所**：
  - 上交所 (60xxxx): `600036` (招商银行)
  - 深交所 (00xxxx): `000001` (平安银行)
  - 创业板 (30xxxx): `300001`
  - 科创板 (68xxxx): `688001`
- **数据源**: 通达信 API
- **格式**: 6 位数字代码

### 🤖 多 LLM 支持

- **百炼 (DashScope)**: 通义千问模型，中文优化
- **OpenAI**: GPT-4o, GPT-4.1 系列, o1, o3 系列
- **Google AI**: Gemini 2.0/2.5 Flash 系列
- **Anthropic**: Claude 3.5/4 系列

### 🗄️ 数据库集成

- **MongoDB**: 持久化存储
- **Redis**: 高性能缓存

## 贡献

我们欢迎社区贡献！无论是修复错误、改进文档还是建议新功能，您的输入都能让这个项目变得更好。如果您对这条研究路线感兴趣，请考虑加入我们的开源金融 AI 研究社区 [Tauric Research](https://tauric.ai/)。

## 引用

如果 *TradingAgents* 对您有所帮助，请引用我们的工作 :)

```
@misc{xiao2025tradingagentsmultiagentsllmfinancial,
      title={TradingAgents: Multi-Agents LLM Financial Trading Framework},
      author={Yijia Xiao and Edward Sun and Di Luo and Wei Wang},
      year={2025},
      eprint={2412.20138},
      archivePrefix={arXiv},
      primaryClass={q-fin.TR},
      url={https://arxiv.org/abs/2412.20138},
}
```
