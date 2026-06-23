# AI Price Comparison Agent

A multi-agent pipeline that searches multiple e-commerce websites for a product, extracts prices, and generates an HTML comparison report.

## What it does

1. **Agent A** generates smart search queries for the target product
2. **Python functions** search product URLs and extract prices using ScrapeGraphAI
3. **Agent B** generates a clean HTML price comparison report

## Output

![Price Comparison Table](example/price_comparison.html)

An HTML report with:
- Summary cards (lowest, average, highest price)
- Sortable comparison table
- Direct links to each listing

## Stack

- [CrewAI](https://crewai.com) — agent orchestration
- [ScrapeGraphAI](https://scrapegraph.ai) — JS-rendered scraping + search
- [Cohere](https://cohere.com) — search query generation
- [Groq](https://groq.com) — HTML report generation
- [AgentOps](https://agentops.ai) — agent monitoring
- [Pydantic](https://docs.pydantic.dev) — structured output validation

## Setup

1. Clone the repo
```bash
git clone https://github.com/your-username/ai-agents.git
cd ai-agents/1_AI\ Agent\ CrewAI
```

2. Install dependencies
```bash
pip install -r requirements.txt
```

3. Add your API keys — copy `.env.example` to `.env` and fill in:
```
GROQ_API_KEY=
COHERE_API_KEY=
AGENTOPS_API_KEY=
SGAI_API_KEY=
```

4. Run the notebook `price_comparison_vscode.ipynb`

## Example Output

See the [`examples/`](examples/) folder for sample results searching for an ASUS ROG Zephyrus G14.

## Key Lesson

Not every step needs to be an LLM agent.

The scraping agent was burning thousands of tokens per retry. Replacing it with a plain Python function made the system faster, cheaper, and more reliable.