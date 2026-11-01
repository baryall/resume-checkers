# 📄 AI Resume Analyzer

Upload a resume (PDF, DOCX or TXT) and get an **ATS score**, a score breakdown,
strengths/weaknesses, missing keywords and concrete improvement suggestions.
Optionally paste a job description for a more accurate, job-specific score.

Built with **Streamlit** (UI) and **Google Gemini Flash** (AI).

## Features
- PDF / DOCX / TXT upload
- Overall ATS score + breakdown (keywords, formatting, content, structure)
- Strengths, weaknesses, prioritized improvements
- Missing keywords vs. a job description
- Before/after example rewrites
- Download the report as JSON

## Run locally

1. Get a free API key from [Google AI Studio](https://aistudio.google.com/apikey).
2. Install and run:

```bash
python -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate
pip install -r requirements.txt
```

3. Add your key (pick one):

```bash
# Option A: environment variable
export GEMINI_API_KEY="your-key"            # Windows PowerShell: $env:GEMINI_API_KEY="your-key"

# Option B: Streamlit secrets file
mkdir .streamlit
echo 'GEMINI_API_KEY = "your-key"' > .streamlit/secrets.toml
```

4. Start the app:

```bash
streamlit run app.py
```

Optional: use a different model with `GEMINI_MODEL` (default `gemini-2.5-flash`).

## Push to GitHub

```bash
git init
printf "venv/\n__pycache__/\n.streamlit/secrets.toml\n.env\n" > .gitignore
git add .
git commit -m "Initial commit: AI resume analyzer"
git branch -M main
# create an empty repo on github.com first, then:
git remote add origin https://github.com/<your-username>/<your-repo>.git
git push -u origin main
```

> Never commit your API key. The `.gitignore` above keeps `secrets.toml` out of the repo.

## Deploy on Streamlit Community Cloud (free)

1. Go to [share.streamlit.io](https://share.streamlit.io) and sign in with GitHub.
2. Click **Create app** → choose your repo, branch `main`, main file `app.py`.
3. Open **Advanced settings → Secrets** and paste:
   ```toml
   GEMINI_API_KEY = "your-key"
   ```
4. Click **Deploy**. You'll get a public `*.streamlit.app` URL in a minute or two.

## Notes
- Scanned (image-only) PDFs can't be read; neither can real ATS systems, so export a text-based PDF.
- The ATS score is an AI estimate, not the output of any specific ATS product.
- Uploaded resume text is sent to the Gemini API for analysis.# resume-checkers
