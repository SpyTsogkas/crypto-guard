# 🛡️ CryptoGuard — AI Investment Advisor

> A professional desktop application for cryptocurrency analysis powered by Artificial Intelligence (Random Forest), a FinTech UI (PyQt6), and a local SQLite database.

---

## Table of Contents

- [System Requirements](#system-requirements)
- [Folder Structure](#folder-structure)
- [Installation — VS Code (Recommended)](#installation--vs-code-recommended)
- [Installation — Virtual Environment (venv)](#installation--virtual-environment-venv)
- [Installation — Plain Python Interpreter](#installation--plain-python-interpreter)
- [Running the Application](#running-the-application)
- [User Guide](#user-guide)
- [Troubleshooting](#troubleshooting)

---

## System Requirements

| Component | Minimum Requirement |
|---|---|
| Operating System | Windows 10/11 or Linux (Ubuntu 20.04+) |
| Python | 3.10 or newer |
| RAM | 4 GB |
| Internet Connection | Required (for the CoinGecko API) |
| CoinGecko API Key | Demo plan (free) |

---

## Folder Structure

```
CryptoGuard/
│
├── app.py                  # Application entry point
├── requirements.txt        # Python frameworks
│
├── ui/
│   └── dashboard.py        # PyQt6 UI (AuthScreen + DashboardUI)
│
├── core/
│   ├── data_fetcher.py     # Data fetching from the CoinGecko API
│   ├── predictor.py        # AI Engine (Random Forest Multi-Horizon)
│   └── investment_advisor.py # Organization + Logic Engine
│
└── database/
    ├── db_manager.py       # SQLite management
    └── crypto_guard.db     # Local database (created automatically)
```

---

## Installation — VS Code (Recommended)

### Step 1 — Install Python

1. Download Python from [python.org](https://www.python.org/downloads/)
2. During installation, **DO NOT CHECK** the `Add Python to PATH` option
3. Verify in the terminal:
```bash
python --version
# Expected: Python 3.10.x or newer
```

### Step 2 — Install VS Code

1. Download VS Code from [code.visualstudio.com](https://code.visualstudio.com/)
2. Install the **Python** extension (by Microsoft) from within VS Code:
   - `Ctrl+Shift+X` → search "Python" → Install

### Step 3 — Open the Project

1. `File` → `Open Folder` → select the `CryptoGuard` folder
2. Open the integrated terminal: `` Ctrl+` ``

### Step 4 — Create a Virtual Environment

In the VS Code terminal:
```bash
python -m venv venv
```

### Step 5 — Activate the Virtual Environment

**Windows:**
```bash
venv\Scripts\activate
```
**Linux/macOS:**
```bash
source venv/bin/activate
```

> You will see `(venv)` at the beginning of the terminal line.

### Step 6 — Select the Python Interpreter in VS Code

1. `Ctrl+Shift+P` → type `Python: Select Interpreter`
2. Choose the option that has `venv` in its path (e.g. `./venv/Scripts/python.exe`)

### Step 7 — Install Dependencies

```bash
pip install -r requirements.txt
```

### Step 8 — Configure the API Key

Open the file `core/data_fetcher.py` and replace:
```python
self.api_key = "YOUR_OWN_API_KEY"
```
> Get a free API key from: [coingecko.com/en/api](https://www.coingecko.com/en/api) → Demo Plan

### Step 9 — Run

```bash
python app.py
```

---

## Installation — Virtual Environment (venv)

If you are not using VS Code, follow the steps below from any terminal.

```bash
# 1. Navigate to the project folder
cd path/to/CryptoGuard

# 2. Create a virtual environment
python -m venv venv

# 3. Activate (Windows)
venv\Scripts\activate

# 3. Activate (Linux/macOS)
source venv/bin/activate

# 4. Install libraries
pip install -r requirements.txt

# 5. Run
python app.py
```

---

## Installation — Plain Python Interpreter

> This method installs the packages globally. Recommended only for a quick test.

```bash
# 1. Navigate to the folder
cd path/to/CryptoGuard

# 2. Install libraries
pip install PyQt6 pandas numpy scikit-learn requests

# 3. Run
python app.py
```

---

## Running the Application

```bash
python app.py
```

The Login window appears at **450×600px**.

---

## User Guide

### 1. Registration (Register)
- Select the **Register** tab
- Enter a **Username** and **Password**
- Select a **Risk Profile**: `Conservative` / `Moderate` / `Aggressive`
- Click **Submit**

### 2. Sign In (Login)
- Enter your credentials
- Click **Login** — the window automatically expands to **90% of the screen**

### 3. Coin Analysis
- Select a coin using the buttons (Bitcoin, Ethereum, etc.)
- Wait for the analysis — the application **does not freeze** (asynchronous execution)
- View:
  - **Current Price**
  - **Predicted Price** (1 Day up to 1 Month)
  - **MAE** (Margin of Error)
  - **Personalized Advice** based on your Risk Profile

---

## Troubleshooting

| Problem | Cause | Solution |
|---|---|---|
| `401 Unauthorized` | Wrong or expired API Key | Renew the key in `data_fetcher.py` |
| `Not enough data` warning | Too little data for the horizon | Normal — the system skips that horizon |
| `ModuleNotFoundError` | Missing package | Run `pip install -r requirements.txt` |
| Black window | GPU rendering issue | Add `QT_OPENGL=software` as an environment variable |
| `database/` not found | The folder does not exist | Create it manually: `mkdir database` |

---

## requirements.txt

```
PyQt6>=6.4.0
pandas>=1.5.0
numpy>=1.23.0
scikit-learn>=1.1.0
requests>=2.28.0
```

---

## License

Academic Project — For educational use only.

> **Note:** The application's predictions are the result of a Machine Learning algorithm and **do not constitute investment advice**.
