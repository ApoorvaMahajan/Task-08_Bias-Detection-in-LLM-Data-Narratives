# **Task 08 Initial Planning Report**
**Project:** Bias Detection in LLM-Generated Sports Data Narratives  
**Researcher:** Apoorva Mahajan  
**Date:** 2025-10-15

## 1. Objective
This initial plan outlines the design and scope for a controlled experiment to detect biases in LLM-generated narratives when processing identical sports datasets from task 5 under varied prompt framings.

## 2. Data
Files to be used (please email amahaj05@syr.edu for actual datasets):
- `2023 SU Womens Lacrosse Cumulative Statistics.xlsx`
- `2024 SU Womens Lacrosse Cumulative Statistics.xlsx`
- `player_improvement.csv`

Ethical step: all player names will be anonymized in `prompts/` (e.g., Player A, Player B) before sending to any LLM.

## 3. Hypotheses
- **H1 (Framing):** LLM recommendations differ when describing a player as "struggling" vs "developing".
- **H2 (Demographic):** Mentioning a player's seniority affects which players are recommended for coaching.
- **H3 (Framing):** "What went wrong" vs "What opportunities exist" produces distinct narratives.
- **H4 (Confirmation):** Priming an LLM with a hypothesis (e.g., "turnovers caused losses") biases its analysis toward that hypothesis.
- **H5 (Selection):** LLM selectively emphasizes different stats (goals, turnovers, assists) based on prompt focus.

## 4. Experimental Design (summary)
- Generate paired prompts per hypothesis using `scripts/experiment_design.py`.
- Run each prompt 3–5 times per model (temperature variability) using `scripts/run_experiment.py`.
- Models: GPT-4 (OpenAI), (optionally) Claude (Anthropic), Gemini (Google) — add adapters as available.
- Log all outputs to `results/llm_outputs.jsonl` with timestamp, model version, temperature.

## 5. Analysis plan (overview)
- Quantify player mentions per condition (who the LLM recommends).
- Sentiment analysis per response (VADER).
- Chi-square tests for mention frequency differences across conditions.
- Validate factual claims against `player_improvement.csv` using `scripts/validate_claims.py`.

## 6. Reproducibility & Ethics
- Random seed 42 for bootstraps.
- Prompt and result archives saved.
- Anonymized prompts and synthetic demographic labels used.
- Pre-registration: hypotheses and prompt templates saved to `prompts/`.

## 7. Deliverables by Oct 21
- `prompts/prompts.json` (generated)
- `results/llm_outputs.jsonl` (raw outputs)
- `analysis/` with summary CSVs and charts