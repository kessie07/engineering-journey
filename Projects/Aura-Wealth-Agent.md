# Aura: The Predictive Wealth Agent

**Status:** Built / worked on (hackathon prototype)
**When:** March – April 2026
**Code:** Private for now

## What it is

Aura was a hackathon build. The idea: instead of a banking app that only shows you what already happened, have something that predicts where your balance is heading and answers questions like *"can I afford this right now?"* with that forecast in mind.

## How it's put together

```text
Next.js frontend  ──►  FastAPI (/api/chat, /api/chart-data)
                              │
            ┌─────────────────┴──────────────────┐
            ▼                                    ▼
   GRU forecasting model                 "AuraBrain" chat
   (PyTorch, trained on                  LangChain + Gemini 2.5 Flash
    synthetic transactions)              + FAISS over a bank-rules file
                                                  │
                     Streamlit "banker dashboard" reads the same data
```

- **Data**: there was no real banking data, so I wrote a generator (`datagen.py`) that creates a year of transactions for 100 made-up users with different salaries, rent, EMIs, subscriptions and so on.
- **Forecasting**: a small GRU in PyTorch. It looks at the last 14 transactions (amount + balance, min-max scaled) and predicts the next balance.
- **Chat**: Gemini 2.5 Flash via LangChain. A short `banking_rules.txt` (overdraft fees, loan eligibility, card rewards) is embedded with MiniLM into FAISS, so answers follow "bank policy". The forecast and chat history go into the prompt as well.
- **Frontend**: Next.js + Framer Motion + Recharts. Components for the vault/entry screen, payments, a forecast chart and the chat. Next API routes log chats and transactions to CSV.
- **Dashboard**: a Streamlit control panel for the "banker" side that reflects what happens on the frontend.

## Honest limitations

- All data is synthetic, and the bank rules are invented for the demo.
- The model trains on the full dataset with no validation split or proper evaluation. It was a hackathon, and it shows.
- No tests. CSV files act as the database.

## What's next

If I come back to this, I'd start with the forecasting: a proper train/test split, a baseline to compare against, and an honest number for how good the predictions are.

## Evidence

- Code structure: `aura-ai-engine/` (api, engine, training, data generator, Streamlit dashboard) and `frontend/` (Next.js).
- Screenshots: none saved yet. I'll add them if I run it again.
