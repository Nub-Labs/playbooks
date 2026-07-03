# Nub Labs - Playbooks

Algorithm playbooks with runnable Jupyter notebooks. Each playbook teaches a technique using a real dataset, then shows how the same approach applies to real engineering and business problems.

Foundations notebooks run on [Google Colab](https://colab.research.google.com) with no local setup. Ecommerce AI series notebooks require a local Python environment (see below).

---

## Local setup

```bash
git clone https://github.com/Nub-Labs/playbooks.git
cd playbooks
python3 -m venv venv
source venv/bin/activate   # Windows: venv\Scripts\activate
pip install -r requirements.txt
cp .env.example .env        # fill in your API keys

# Ecommerce AI series only — start Postgres + pgvector:
docker compose up -d

jupyter notebook
```

The virtualenv and `docker compose up -d` (Postgres + pgvector) are required for the Ecommerce AI series. Foundations notebooks run on Colab without any local setup.

The vector store is reachable at `postgresql://playbooks:playbooks@localhost:5432/playbooks`. Stop it with `docker compose down` (data persists) or `docker compose down -v` to wipe it.

---

## Foundations

Standalone playbooks. Each teaches one algorithm on a public dataset. No platform dependency, no API keys.

### PageRank

**The technique:** Find the most important nodes in any directed graph using power iteration.
**The dataset:** npm and PHP Composer dependency graphs (public, familiar, verifiable).
**The real application:** Microservice blast-radius analysis, CVE prioritization, data lineage risk, supply chain auditing.

Interactive walkthrough: [nublabs.com/playbooks/pagerank](https://nublabs.com/playbooks/pagerank)

| Notebook | Description | Open |
|---|---|---|
| `foundations/pagerank/npm_pagerank.ipynb` | PageRank on the npm dependency graph - reproduces the exact website results (js-tokens #1, converged iter 17) | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Nub-Labs/playbooks/blob/main/foundations/pagerank/npm_pagerank.ipynb) |
| `foundations/pagerank/composer_pagerank.ipynb` | PageRank on the PHP Composer (Packagist) ecosystem - curated dataset + optional live Packagist API fetch | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Nub-Labs/playbooks/blob/main/foundations/pagerank/composer_pagerank.ipynb) |

### Market Basket Analysis

**The technique:** Association rule mining (Apriori algorithm). Discovers which items appear together in transactions more often than chance would predict.
**The dataset:** A curated 18-item / 267-transaction grocery dataset (Part A), and the [UCI Online Retail Dataset](https://archive.ics.uci.edu/dataset/352/online+retail) - 541,909 rows of real UK retailer transactions (Part B).
**The real application:** Product recommendations, feature adoption, sales activity patterns, learning path discovery.

Interactive walkthrough: [nublabs.com/playbooks/market-basket](https://nublabs.com/playbooks/market-basket)

| Notebook | Description | Open |
|---|---|---|
| `foundations/market-basket/market_basket.ipynb` | Part A: exact curated dataset (reproduces website results). Part B: full UCI Online Retail Dataset. | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Nub-Labs/playbooks/blob/main/foundations/market-basket/market_basket.ipynb) |

### Customer Segmentation

**The technique:** RFM analysis (Recency, Frequency, Monetary) combined with K-Means clustering. Finds natural customer groups from transaction history without manually labelling any customer.
**The dataset:** A curated 200-customer dataset with 4 known segments (Part A), and the [UCI Online Retail Dataset](https://archive.ics.uci.edu/dataset/352/online+retail) (Part B).
**The real application:** Targeted marketing campaigns, personalised recommendations, churn detection, win-back campaigns.

Interactive walkthrough: [nublabs.com/playbooks/customer-segmentation](https://nublabs.com/playbooks/customer-segmentation)

| Notebook | Description | Open |
|---|---|---|
| `foundations/customer-segmentation/customer_segmentation.ipynb` | Part A: curated 200-customer dataset (reproduces website results). Part B: UCI Online Retail Dataset. | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Nub-Labs/playbooks/blob/main/foundations/customer-segmentation/customer_segmentation.ipynb) |

---

## Ecommerce AI Series

Connected playbooks built on [TechHeaven](https://github.com/Nub-Labs/techheaven-reference-platform), a fictional but realistic ecommerce business running on Bagisto 2.x. Each playbook adds one AI capability to TechHeaven using real business data.

Series overview: [nublabs.com/playbooks/ecommerce](https://nublabs.com/playbooks/ecommerce)

**Prerequisites:** Local Python environment (see setup above) and an OpenAI API key. Some notebooks also connect to a locally running TechHeaven instance for live data.

| Notebook | Description | Status |
|---|---|---|
| `ecommerce/ai-customer-support/ai_customer_support.ipynb` | RAG-powered customer support assistant. Retrieves answers from TechHeaven's policies, FAQ, and product catalog. | Live |
| `ecommerce/recommendation-engine/` | Collaborative filtering product recommendations from order history | Upcoming |
| `ecommerce/semantic-product-search/` | Embedding-based semantic search over the product catalog | Upcoming |
| `ecommerce/voice-shopping-assistant/` | Voice-first shopping powered by speech-to-text + LLM | Upcoming |

Full roadmap: [nublabs.com/playbooks/ecommerce](https://nublabs.com/playbooks/ecommerce)

### About TechHeaven

TechHeaven is a fictional ecommerce retailer (consumer electronics) with realistic seeded data: 500+ products, 2,000+ customers, 8,000+ orders, 5,000+ reviews, and full policy/FAQ content. It has no AI. Every Ecommerce AI playbook adds one AI capability to it.

Platform docs: [nublabs.com/reference-platforms/techheaven](https://nublabs.com/reference-platforms/techheaven)
Repository: [github.com/Nub-Labs/techheaven-reference-platform](https://github.com/Nub-Labs/techheaven-reference-platform)

---

## Repository structure

```
foundations/
  pagerank/
  market-basket/
  customer-segmentation/
ecommerce/
  ai-customer-support/
  recommendation-engine/         (upcoming)
  ...
shared/                          (utilities shared across series playbooks)
requirements.txt
.env.example
```

---

## Contributing

New playbooks are added here as new algorithm walkthroughs are published on the website.
Questions or findings? [Open an issue](https://github.com/Nub-Labs/playbooks/issues)
