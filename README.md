# 🛡️ CryptoGuard — AI Investment Advisor

> Επαγγελματική Desktop εφαρμογή ανάλυσης κρυπτονομισμάτων με Τεχνητή Νοημοσύνη (Random Forest), FinTech UI (PyQt6) και τοπική βάση δεδομένων SQLite.

---

## Πίνακας Περιεχομένων

- [Απαιτήσεις Συστήματος](#-απαιτήσεις-συστήματος)
- [Δομή Φακέλων](#-δομή-φακέλων)
- [Εγκατάσταση — VS Code](#-εγκατάσταση--vs-code-συνιστάται)
- [Εγκατάσταση — Virtual Environment (venv)](#-εγκατάσταση--virtual-environment-venv)
- [Εγκατάσταση — Απλός Python Interpreter](#-εγκατάσταση--απλός-python-interpreter)
- [Εκτέλεση της Εφαρμογής](#-εκτέλεση-της-εφαρμογής)
- [Οδηγός Χρήσης](#-οδηγός-χρήσης)
- [Αντιμετώπιση Προβλημάτων](#-αντιμετώπιση-προβλημάτων)

---

## Απαιτήσεις Συστήματος

| Στοιχείο | Ελάχιστη Απαίτηση |
|---|---|
| Λειτουργικό Σύστημα | Windows 10/11 ή Linux (Ubuntu 20.04+) |
| Python | 3.10 ή νεότερη |
| RAM | 4 GB |
| Σύνδεση Internet | Απαραίτητη (για CoinGecko API) |
| CoinGecko API Key | Demo plan (δωρεάν) |

---

## Δομή Φακέλων

```
CryptoGuard/
│
├── app.py                  # Σημείο εκκίνησης της εφαρμογής
├── requirements.txt        # Εξαρτήσεις Python
│
├── ui/
│   └── dashboard.py        # PyQt6 UI (AuthScreen + DashboardUI)
│
├── core/
│   ├── data_fetcher.py     # Άντληση δεδομένων από CoinGecko API
│   ├── predictor.py        # AI Engine (Random Forest Multi-Horizon)
│   └── investment_advisor.py # Ορχηστρωτής + Logic Engine
│
└── database/
    ├── db_manager.py       # SQLite διαχείριση
    └── crypto_guard.db     # Τοπική βάση (δημιουργείται αυτόματα)
```

---

## Εγκατάσταση — VS Code (Συνιστάται)

### Βήμα 1 — Εγκατάσταση Python

1. Κατέβασε Python από το [python.org](https://www.python.org/downloads/)
2. Κατά την εγκατάσταση, **τσέκαρε** το `Add Python to PATH`
3. Επαλήθευσε στο terminal:
```bash
python --version
# Αναμενόμενο: Python 3.10.x ή νεότερη
```

### Βήμα 2 — Εγκατάσταση VS Code

1. Κατέβασε VS Code από το [code.visualstudio.com](https://code.visualstudio.com/)
2. Εγκατάστησε το extension **Python** (από Microsoft) μέσα από το VS Code:
   - `Ctrl+Shift+X` → αναζήτηση "Python" → Install

### Βήμα 3 — Άνοιγμα του Project

1. `File` → `Open Folder` → επίλεξε τον φάκελο `CryptoGuard`
2. Άνοιξε το integrated terminal: `` Ctrl+` ``

### Βήμα 4 — Δημιουργία Virtual Environment

Στο terminal του VS Code:
```bash
python -m venv venv
```

### Βήμα 5 — Ενεργοποίηση Virtual Environment

**Windows:**
```bash
venv\Scripts\activate
```
**Linux/macOS:**
```bash
source venv/bin/activate
```

> ✅ Θα δεις `(venv)` στην αρχή της γραμμής του terminal.

### Βήμα 6 — Επιλογή Python Interpreter στο VS Code

1. `Ctrl+Shift+P` → πληκτρολόγησε `Python: Select Interpreter`
2. Επίλεξε την επιλογή που έχει `venv` στο path (π.χ. `./venv/Scripts/python.exe`)

### Βήμα 7 — Εγκατάσταση Εξαρτήσεων

```bash
pip install -r requirements.txt
```

### Βήμα 8 — Ρύθμιση API Key

Άνοιξε το αρχείο `core/data_fetcher.py` και αντικατάστησε:
```python
self.api_key = "ΤΟ_ΔΙΚΟ_ΣΟΥ_API_KEY"
```
> Δωρεάν API key από: [coingecko.com/en/api](https://www.coingecko.com/en/api) → Demo Plan

### Βήμα 9 — Εκτέλεση

```bash
python app.py
```

---

## Εγκατάσταση — Virtual Environment (venv)

Αν δεν χρησιμοποιείς VS Code, ακολούθα τα παρακάτω βήματα από οποιοδήποτε terminal.

```bash
# 1. Μετακίνηση στον φάκελο του project
cd path/to/CryptoGuard

# 2. Δημιουργία virtual environment
python -m venv venv

# 3. Ενεργοποίηση (Windows)
venv\Scripts\activate

# 3. Ενεργοποίηση (Linux/macOS)
source venv/bin/activate

# 4. Εγκατάσταση εξαρτήσεων
pip install -r requirements.txt

# 5. Εκτέλεση
python app.py
```

---

## Εγκατάσταση — Απλός Python Interpreter

> Η μέθοδος αυτή εγκαθιστά τα packages globally. Συνιστάται μόνο για γρήγορη δοκιμή.

```bash
# 1. Μετακίνηση στον φάκελο
cd path/to/CryptoGuard

# 2. Εγκατάσταση εξαρτήσεων
pip install PyQt6 pandas numpy scikit-learn requests

# 3. Εκτέλεση
python app.py
```

---

## Εκτέλεση της Εφαρμογής

```bash
python app.py
```

Το παράθυρο Login εμφανίζεται σε **450×600px**.

---

## Οδηγός Χρήσης

### 1. Εγγραφή (Register)
- Επίλεξε την καρτέλα **Register**
- Εισήγαγε **Username** και **Password**
- Επίλεξε **Risk Profile**: `Conservative` / `Moderate` / `Aggressive`
- Πάτα **Submit**

### 2. Σύνδεση (Login)
- Εισήγαγε τα στοιχεία σου
- Πάτα **Login** — το παράθυρο μεγαλώνει αυτόματα σε **90% της οθόνης**

### 3. Ανάλυση Νομίσματος
- Επίλεξε νόμισμα από τα κουμπιά (Bitcoin, Ethereum, κ.λπ.)
- Περίμενε την ανάλυση — η εφαρμογή **δεν παγώνει** (ασύγχρονη εκτέλεση)
- Δες:
  - **Τρέχουσα Τιμή**
  - **Προβλεπόμενη Τιμή** (1 Ημέρα έως 1 Μήνα)
  - **MAE** (Margin of Error)
  - **Προσωποποιημένη Συμβουλή** βάσει Risk Profile

---

## Αντιμετώπιση Προβλημάτων

| Πρόβλημα | Αιτία | Λύση |
|---|---|---|
| `401 Unauthorized` | Λάθος ή ληγμένο API Key | Ανανέωσε το key στο `data_fetcher.py` |
| `Not enough data` warning | Λίγα δεδομένα για το horizon | Κανονικό — το σύστημα παραλείπει αυτό το horizon |
| `ModuleNotFoundError` | Λείπει πακέτο | Τρέξε `pip install -r requirements.txt` |
| Μαύρο παράθυρο | GPU rendering issue | Πρόσθεσε `QT_OPENGL=software` ως env variable |
| `database/` δεν βρίσκεται | Ο φάκελος δεν υπάρχει | Δημιούργησε χειροκίνητα: `mkdir database` |

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

## Άδεια Χρήσης

Ακαδημαϊκό Project — Χρήση μόνο για εκπαιδευτικούς σκοπούς.

> **Σημείωση:** Οι προβλέψεις της εφαρμογής είναι αποτέλεσμα αλγορίθμου Machine Learning και **δεν αποτελούν επενδυτική συμβουλή**.
