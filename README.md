# AI_AGENTS

A small collection of Jupyter notebooks for experimenting with autonomous AI agents, data collection, and website data wrangling. This repository is intended as a compact playground for exploring agent designs, statistical/behavioural experiments, and simple web scraping + data preprocessing pipelines.

Repository contents (notebooks)
- [agent-statistical.ipynb](https://github.com/M-zaid-bilal/AI_AGENTS/blob/main/agent-statistical.ipynb) — experiments with statistically-driven agent behaviors and analysis. Kernel: Python 3.12.12 (see notebook metadata).
- [web-crawler.ipynb](https://github.com/M-zaid-bilal/AI_AGENTS/blob/main/web-crawler.ipynb) — a web crawling/scraping notebook for collecting site content. Kernel: Python 3.11.13 (see notebook metadata).
- [websitedatawrangler.ipynb](https://github.com/M-zaid-bilal/AI_AGENTS/blob/main/websitedatawrangler.ipynb) — data cleaning and transformation utilities applied to scraped website content. Kernel: Python 3.11.13 (see notebook metadata).

Note: These notebooks are the primary artifacts in the repo. If you add Python modules, shared utilities, or larger datasets, consider moving them into `src/` and `data/` directories respectively.

Quick start

1. Clone the repo:
   ```bash
   git clone https://github.com/M-zaid-bilal/AI_AGENTS.git
   cd AI_AGENTS
   ```

2. Create a Python environment (recommended: conda for reproducibility). Two notebooks include metadata for Python 3.11 and 3.12; to maximize compatibility use Python 3.11.x unless you intentionally want 3.12 features.

   Using conda:
   ```bash
   conda create -n ai_agents python=3.11
   conda activate ai_agents
   ```

   Using venv:
   ```bash
   python3 -m venv .venv
   source .venv/bin/activate
   ```

3. Install dependencies
   - If you add a `requirements.txt` file to the repo, install it with:
     ```bash
     pip install -r requirements.txt
     ```
   - Example minimal deps (adjust to notebook code):
     ```bash
     pip install jupyterlab ipykernel requests beautifulsoup4 pandas numpy tqdm matplotlib
     ```
   - Optional (for LLM experiments / RAG):
     ```bash
     pip install openai langchain sentence-transformers faiss-cpu transformers torch
     ```

4. Start Jupyter and open the notebooks:
   ```bash
   jupyter lab
   ```
   or
   ```bash
   jupyter notebook
   ```

Running notebooks non-interactively

- Execute a notebook end-to-end with nbconvert:
  ```bash
  jupyter nbconvert --ExecutePreprocessor.timeout=600 --to notebook --execute agent-statistical.ipynb --output executed/agent-statistical.ipynb
  ```

- Run parametrized notebooks with papermill:
  ```bash
  pip install papermill
  papermill web-crawler.ipynb executed/web-crawler.ipynb -p start_url "https://example.com"
  ```

Environment variables and secrets

- Do not commit API keys or credentials. Use environment variables or a secrets manager.
- Recommended variables you might need:
  - OPENAI_API_KEY
  - HF_API_TOKEN
  - PROXY_URL (if crawling behind a proxy)
- Add `.env` to `.gitignore` and read secrets via `os.environ` or python-dotenv when needed.

Web crawling and scraping best practices

- Respect robots.txt and website terms of service.
- Rate-limit your requests, use polite headers and backoff on errors.
- Avoid scraping large sites without permission or ignoring API offerings.

Suggested repo improvements

- Add a `requirements.txt` or `environment.yml` with pinned versions.
- Add a LICENSE (MIT recommended if you want a permissive license).
- Add a short README cell at the top of each notebook describing inputs, kernels, and required environment variables.
- Add `.gitignore` entries for:
  ```
  .venv/
  __pycache__/
  .ipynb_checkpoints/
  .env
  ```
- Add lightweight CI that runs a subset of notebooks headlessly (nbconvert / papermill) to ensure examples remain runnable.

Contributing

- Contributions welcome: fork → branch → PR.
- Keep notebooks focused and move shared code to `src/` for easier testing and reuse.
- Document any new dependencies in `requirements.txt`.

Author / Contact
- Owner: [M-zaid-bilal](https://github.com/M-zaid-bilal)

License
- No license file is present in the repository. If you want this repo to be open source, consider adding a LICENSE (MIT, Apache-2.0, etc.). I can add a LICENSE for you if you tell me which one you'd like.
