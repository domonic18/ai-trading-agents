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
  <a href="README.md"><strong>English</strong></a> | <a href="README.zh-CN.md">中文</a>
</div>

---

# TradingAgents: Multi-Agents LLM Financial Trading Framework 

> 🎉 **TradingAgents** officially released! We have received numerous inquiries about the work, and we would like to express our thanks for the enthusiasm in our community.
>
> So we decided to fully open-source the framework. Looking forward to building impactful projects with you!

<div align="center">

🚀 [Framework](#tradingagents-framework) | ⚡ [Installation & CLI](#installation-and-cli) | 🎬 [Demo](https://www.youtube.com/watch?v=90gr5lwjIho)

</div>

## TradingAgents Framework

TradingAgents is a multi-agent trading framework that mirrors the dynamics of real-world trading firms. By deploying specialized LLM-powered agents: from fundamental analysts, sentiment experts, and technical analysts, to trader, risk management team, the platform collaboratively evaluates market conditions and informs trading decisions. Moreover, these agents engage in dynamic discussions to pinpoint the optimal strategy.

<p align="center">
  <img src="docs/assets/schema.png" style="width: 100%; height: auto;">
</p>

> TradingAgents framework is designed for research purposes. Trading performance may vary based on many factors, including the chosen backbone language models, model temperature, trading periods, the quality of data, and other non-deterministic factors. [It is not intended as financial, investment, or trading advice.](https://tauric.ai/disclaimer/)


## Installation and CLI

### Installation

Clone the repository:
```bash
git clone https://github.com/domonic18/ai-trading-agents.git
cd ai-trading-agents
```

#### Method 1: Using uv

```bash
# Install uv
curl -LsSf https://astral.sh/uv/install.sh | sh

# Change to backend directory
cd backend

# Create virtual environment and install dependencies
uv sync

# Install with optional dependencies (Chinese market, database, visualization)
uv sync --extra all
```

#### Method 2: Using pip

```bash
# Change to backend directory
cd backend

# Create virtual environment
python -m venv .venv
source .venv/bin/activate  # On Windows: .venv\Scripts\activate

# Install dependencies
pip install -e .

# Install with optional dependencies
pip install -e ".[all]"  # All optional features
pip install -e ".[chinese,database]"  # Specific features
```

### Configuration

You need to create a `.env` file in the project root with your API keys (see `.env.example` for reference):

```bash
cp .env.example .env
# Edit .env with your actual API keys
```

**Minimal required configuration**:

**When analyzing US stocks only**:
```env
# OpenAI or Google AI (choose one)
OPENAI_API_KEY=your_openai_api_key_here
# or
GOOGLE_API_KEY=your_google_api_key_here

# FinnHub (required for financial data)
FINNHUB_API_KEY=your_finnhub_api_key_here
```

**When analyzing Chinese A-shares or using DashScope LLM**:
```env
# DashScope (required for Chinese stocks or Qwen models)
DASHSCOPE_API_KEY=your_dashscope_api_key_here

# FinnHub (required for financial data)
FINNHUB_API_KEY=your_finnhub_api_key_here
```

**Note**:
- **DashScope API key is only required when**:
  - Analyzing Chinese A-share stocks (using TongDaXin data + DashScope embeddings)
  - Choosing DashScope as your LLM provider (Qwen models)
- **When analyzing US stocks with OpenAI/Google models**: DashScope is not required

### CLI Usage

Run the CLI from the project root:

```bash
# Activate virtual environment
source backend/.venv/bin/activate

# Change to backend directory
cd backend

# Start CLI
python -m cli.main
```

You will see an interactive interface where you can select your desired tickers, date, LLMs, research depth, etc.

<p align="center">
  <img src="docs/assets/cli/cli_init.png" width="100%" style="display: inline-block; margin: 0 2%;">
</p>

An interface will appear showing results as they load, letting you track the agent's progress as it runs.

<p align="center">
  <img src="docs/assets/cli/cli_news.png" width="100%" style="display: inline-block; margin: 0 2%;">
</p>

<p align="center">
  <img src="docs/assets/cli/cli_transaction.png" width="100%" style="display: inline-block; margin: 0 2%;">
</p>

## Database Setup (Optional)

### Enable High-Performance Caching

**1. Start database services using Docker Compose**:

We recommend using docker-compose to quickly start Redis and MongoDB:

```bash
# Start services (data will be persisted to workspace directory)
docker-compose -f docker-compose-dev.yml up -d

# Check service status
docker-compose -f docker-compose-dev.yml ps

# Stop services
docker-compose -f docker-compose-dev.yml down

# Stop services and remove data (use with caution)
docker-compose -f docker-compose-dev.yml down -v
```

Data will be automatically persisted to the following directories:
- `workspace/db_data/mongodb` - MongoDB data files
- `workspace/db_data/redis` - Redis data files

**2. Enable in .env**:
```env
# Enable database caching
MONGODB_ENABLED=true
REDIS_ENABLED=true

# MongoDB configuration
MONGODB_HOST=localhost
MONGODB_PORT=27017
MONGODB_DATABASE=tradingagents

# Redis configuration
REDIS_HOST=localhost
REDIS_PORT=6379
REDIS_DB=0
```

**3. Restart the application**:
```bash
# Activate virtual environment
source backend/.venv/bin/activate

# Change to backend directory
cd backend

# Start CLI
python -m cli.main
```

The system will now use database caching for improved performance.

## Acknowledgments

We extend our sincere gratitude to the [Tauric Research](https://github.com/TauricResearch) team for creating the revolutionary multi-agent trading framework **TradingAgents**!

This project is based on their groundbreaking work in multi-agent LLM financial trading systems. Their innovative approach to simulating real-world trading firm dynamics through specialized AI agents has opened new possibilities in financial research and analysis.

We also acknowledge the broader open-source community whose tools and libraries make this research possible. This project is intended for educational and research purposes only.

## Disclaimer

**IMPORTANT: STOCK MARKET INVESTMENT CARRIES RISKS. PLEASE INVEST WITH CAUTION.**

This framework is designed strictly for research and educational purposes. The trading decisions, analysis, and recommendations generated by this system:

- **DO NOT constitute financial, investment, or trading advice**
- **DO NOT guarantee future performance or profits**
- **ARE based on historical data and AI models that may not predict future market conditions accurately**

Stock market investments involve substantial risk of loss and may not be suitable for all investors. You should:

1. **Never invest money you cannot afford to lose**
2. **Conduct your own research and due diligence before making any investment decisions**
3. **Consult with qualified financial advisors before making investment choices**
4. **Be aware that past performance does not guarantee future results**

The developers, contributors, and the original Tauric Research team:

- **Assume no liability for any financial losses incurred from using this system**
- **Do not recommend using this framework for actual trading decisions**
- **Strongly advise using this tool only as a supplementary research aid, not as a primary decision-making system**

By using this software, you agree that you understand these risks and accept full responsibility for any investment decisions you make.
