# 🚀 Scrapy Project Setup Guide (Modern Development)

This guide walks you through setting up a modern Scrapy project with best practices including virtual environments, Git, linters, and optional tooling.

---

## 📁 1. Create Project Folder

```bash
mkdir my_scrapy_project
cd my_scrapy_project
```

---

## 🌱 2. Initialize Git & `.gitignore`

```bash
git init
echo "__pycache__/
*.pyc
.env
.venv
.envrc
.idea/
*.sqlite3
*.log
output/
.scrapy/" > .gitignore
```

---

## 🐍 3. Set Up Virtual Environment

```bash
python3 -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate
```

---

## 🕷 4. Install Scrapy

```bash
pip install scrapy
```

---

## ⚙️ 5. Create Scrapy Project

```bash
scrapy startproject myproject .
```

**Project structure:**

```
my_scrapy_project/
├── myproject/
│   ├── spiders/
│   ├── __init__.py
│   ├── items.py
│   ├── middlewares.py
│   ├── pipelines.py
│   ├── settings.py
├── scrapy.cfg
├── .venv/
└── .gitignore
```

---

## 📦 6. Freeze Dependencies

```bash
pip freeze > requirements.txt
```

Or use `pip-tools`:

```bash
pip install pip-tools
pip-compile
```

---

## 🔧 7. Optional Tools

### 📘 Poetry (Alternative Env Manager)

```bash
pip install poetry
poetry init
poetry add scrapy
```

### 🧹 Pre-commit Hooks

```bash
pip install pre-commit
```

`.pre-commit-config.yaml`:
```yaml
repos:
  - repo: https://github.com/pre-commit/pre-commit-hooks
    rev: v4.5.0
    hooks:
      - id: end-of-file-fixer
      - id: trailing-whitespace
      - id: check-added-large-files
```

```bash
pre-commit install
```

### 🎨 Black + Ruff (Formatting + Linting)

```bash
pip install black ruff
```

Add to `pyproject.toml`:
```toml
[tool.black]
line-length = 88

[tool.ruff]
line-length = 88
```

Then run:
```bash
black .
ruff .
```

---

## 📥 8. Git Commit

```bash
git add .
git commit -m "Initial Scrapy project setup"
```

---

## ☁️ 9. (Optional) Push to GitHub

Using GitHub CLI:
```bash
gh repo create my_scrapy_project --public --source=. --push
```

Or manually:
```bash
git remote add origin https://github.com/yourusername/my_scrapy_project.git
git push -u origin main
```

---

## ✅ Ready to Scrape!

Want to go further?
- [ ] Add Docker support
- [ ] Set up CI/CD with GitHub Actions
- [ ] Integrate with MongoDB/PostgreSQL
- [ ] Use Scrapyd or Crawlera for deployment
- [ ] Add logs or alerts for crawl failures

---

Happy crawling! 🕸️
