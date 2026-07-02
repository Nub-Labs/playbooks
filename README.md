# Nub Labs — Playbooks

Algorithm playbooks with runnable Jupyter notebooks. Each playbook teaches a technique using a real dataset, then shows how the same approach applies to real engineering and business problems.

Runnable on [Google Colab](https://colab.research.google.com) — no local setup required.

---

## PageRank

**The technique:** Find the most important nodes in any directed graph using power iteration.  
**The dataset:** npm and PHP Composer dependency graphs (public, familiar, verifiable).  
**The real application:** Microservice blast-radius analysis, CVE prioritization, data lineage risk, supply chain auditing.

Interactive walkthrough: [nublabs.com/playbooks/pagerank](https://www.nublabs.com/playbooks/pagerank)  
Questions or findings? [Open an issue](https://github.com/Nub-Labs/playbooks/issues)

| Notebook | Description | Open |
|---|---|---|
| `pagerank/npm_pagerank.ipynb` | PageRank on the npm dependency graph — reproduces the exact website results (js-tokens #1, converged iter 17) | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Nub-Labs/playbooks/blob/main/pagerank/npm_pagerank.ipynb) |
| `pagerank/composer_pagerank.ipynb` | PageRank on the PHP Composer (Packagist) ecosystem — curated dataset + optional live Packagist API fetch | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Nub-Labs/playbooks/blob/main/pagerank/composer_pagerank.ipynb) |

### What the notebooks cover

**npm_pagerank.ipynb**
- Exact same 58 nodes and 59 edges as the website walkthrough
- Pure Python — no dependencies beyond `matplotlib`
- Verified output: `js-tokens` ranks #1 (4.7180%), convergence at iteration 17, sum = 1.000000
- Convergence plot and ranked bar chart

**composer_pagerank.ipynb**
- Curated dataset: 32 top Packagist packages (psr/*, symfony/*, laravel/framework, guzzlehttp/guzzle, phpunit/phpunit)
- Same algorithm, different graph — `psr/log` dominates, not `laravel/framework`
- Optional live-fetch section: pulls real-time data from the Packagist API
- Cross-ecosystem comparison: npm vs PHP findings side by side

---

## Market Basket Analysis

**The technique:** Association rule mining (Apriori algorithm). Discovers which items appear together in transactions more often than chance would predict.  
**The dataset:** A curated 18-item / 267-transaction grocery dataset (Part A), and the [UCI Online Retail Dataset](https://archive.ics.uci.edu/dataset/352/online+retail) — 541,909 rows of real UK retailer transactions (Part B).  
**The real application:** Product recommendations, feature adoption, sales activity patterns, learning path discovery — any domain with transaction-like records.

Interactive walkthrough: [nublabs.com/playbooks/market-basket](https://www.nublabs.com/playbooks/market-basket)  
Questions or findings? [Open an issue](https://github.com/Nub-Labs/playbooks/issues)

| Notebook | Description | Open |
|---|---|---|
| `market-basket/market_basket.ipynb` | Part A: exact curated dataset (reproduces website results). Part B: full UCI Online Retail Dataset. | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Nub-Labs/playbooks/blob/main/market-basket/market_basket.ipynb) |

### What the notebook covers

**market_basket.ipynb — Part A (curated dataset)**
- Exact same 18 items and 267 transactions used on the interactive playbook page
- Reproduces and verifies all three "What Surprised Us" findings:
  - Beer → Soda: 100% confidence, lift 8.3×
  - Wine → Cheese: 100% confidence, lift 5.3×
  - Rice ↔ Chicken: lift 4.4× bidirectional
- Confirms that whole milk (most popular item) has weaker lift than niche pairings

**market_basket.ipynb — Part B (UCI Online Retail)**
- Option A: upload `Online Retail.xlsx` manually via Colab file panel
- Option B: direct download from UCI archive
- Full data cleaning (cancellations, returns, test entries)
- Apriori on ~25,900 real transactions
- Support vs confidence scatter plot coloured by lift
- Verifies the key insight: high-frequency items have weaker associations than niche clusters

---

## Customer Segmentation

**The technique:** RFM analysis (Recency, Frequency, Monetary) combined with K-Means clustering. Finds natural customer groups from transaction history — without manually labelling any customer.  
**The dataset:** A curated 200-customer dataset with 4 known segments (Part A), and the [UCI Online Retail Dataset](https://archive.ics.uci.edu/dataset/352/online+retail) — 541,909 rows of real UK retailer transactions (Part B).  
**The real application:** Targeted marketing campaigns, personalised recommendations, churn detection, win-back campaigns — any domain where treating all users identically wastes budget.

Interactive walkthrough: [nublabs.com/playbooks/customer-segmentation](https://www.nublabs.com/playbooks/customer-segmentation)  
Questions or findings? [Open an issue](https://github.com/Nub-Labs/playbooks/issues)

| Notebook | Description | Open |
|---|---|---|
| `customer-segmentation/customer_segmentation.ipynb` | Part A: curated 200-customer dataset (reproduces website results). Part B: UCI Online Retail Dataset — full RFM segmentation on real retail data. | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Nub-Labs/playbooks/blob/main/customer-segmentation/customer_segmentation.ipynb) |

### What the notebook covers

**customer_segmentation.ipynb — Part A (curated dataset)**
- Exact same 200 customers and 4 segments used on the interactive playbook page
- Reproduces and verifies all three "What Surprised Us" findings:
  - At-Risk AOV $330 vs Loyal AOV $117 — 2.8× ratio
  - Champions: 15% of customers, ~43% of revenue (Pareto)
  - At-Risk: $128K in recoverable revenue
- Elbow method and silhouette score for K selection
- Frequency vs Monetary scatter plot coloured by segment
- Revenue share bar chart per segment

**customer_segmentation.ipynb — Part B (UCI Online Retail)**
- Option A: upload `Online Retail.xlsx` manually via Colab file panel
- Option B: direct download attempt from UCI archive
- Full data cleaning (cancellations, returns, negative quantities)
- RFM feature computation per customer_id
- K-Means with K=4 on normalised features
- Verifies the key insight: highest-AOV customers are not always the highest-frequency ones

---

## Contributing

New playbooks are added here as new algorithm walkthroughs are published on the website.  
Each playbook lives in its own directory: `/<algorithm-name>/`.
