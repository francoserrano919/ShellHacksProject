# Stepwise

**A guided Python learning workspace that makes the learner do the work.**

The learner predicts a result, investigates why it happens, revises a small piece of code, and applies the idea to a fresh example. Gemini selects among two reviewed hints per level when a key and learner thinking are available. It cannot send free-form solution text to the learner. If the API is unavailable, built-in hints keep the lesson usable.

## Features

- Fixed radio choices for lesson and multiple-choice answer selection.
- Three selectable lessons: loop boundaries, conditions, and running totals.
- Four-stage practice flow with two progressively clearer hints per guided stage.
- Correct-answer transition with a five-second progress bar and **Continue now** option.
- Independent follow-up with no hints, progress and attempt counts, and a downloadable report of thinking, correct answers, and incorrect attempts.
- Offline demo mode for network outages or exhausted API quota.

## Run locally on a Mac

In VS Code, open the project folder, then open Terminal > New Terminal:

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
python -m streamlit run stepwise_app_v1.1.py
```

Open the Local URL that Streamlit prints, usually http://localhost:8501. The app works without a key using built-in hints.

### Enable Gemini hint selection

Create a Gemini API key in Google AI Studio. Stop Streamlit with Control+C. In the same terminal, enter:

```zsh
read -s "GEMINI_API_KEY?Paste your Gemini API key, then press Enter: "
```

Copy your key, paste it into the invisible prompt, press Enter, then run:

```bash
export GEMINI_API_KEY
python -m streamlit run stepwise_app_v1.1.py
```

The key stays in your terminal process. Do not paste it into source code or commit it. If you open a new terminal, activate `.venv` and set the key again. The configured model is `gemini-3.5-flash-lite`; you can set `GEMINI_MODEL` in the environment if model availability changes.

For a repeatable demonstration, turn on **Offline demo mode** in the sidebar. For a live AI demonstration, turn it off, enter something in **What are you thinking?**, and request a hint. The sidebar's **AI-selected hints** number should increase after an accepted Gemini response. A visible fallback status means the built-in path was used.

## How the guardrail works

1. The learner chooses a lesson and provides thinking.
2. The app sends the lesson context, last attempt, and exactly two approved hint choices to Gemini.
3. Gemini returns a hint ID; the app accepts only one of the two known IDs and displays its own approved text.
4. If the key is absent, the request fails, or the ID is unexpected, a built-in hint is displayed.
5. For revision steps, the app parses Python syntax without executing learner code. It compares the edited syntax tree with reviewed variants. Other stages use constrained responses.

This prototype checks the three included exercises. It does not grade arbitrary Python programs, uploaded screenshots, or math problems. Learning reports record thinking entered when an answer is submitted or a hint requested, all submitted answers, their correctness, and accepted answers after lesson completion. They record practice on the included examples rather than proving mastery. Session progress lasts while the browser session is active.

## Project structure

- `stepwise_app_v1.1.py`: single-file Streamlit application, lesson data, validation, progress transition, learning report, and Gemini hint selection.
- `requirements.txt`: pinned dependency versions.
- `DEMO.md`: a short judging walkthrough and fallback plan.
- `.gitignore`: excludes local environment files and secrets.
