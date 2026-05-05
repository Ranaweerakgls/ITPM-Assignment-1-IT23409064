# Assignment 1 - Singlish to Sinhala Chat Translator Test Automation

Automated testing of the Singlish-to-Sinhala translation feature on [pixelssuite.com/chat-translator](https://www.pixelssuite.com/chat-translator) using Playwright and Python.

---

## Prerequisites

- Python 3.12
- Google Chrome (recommended) — or Playwright will install Chromium automatically

---

## Project Structure

```
test_automation.py                  # Main Playwright automation script
Assignment 1 - Test cases.xlsx      # Excel file for test cases and results
requirements.txt                    # Python dependencies
```

---

## Setup

### 1. Create a virtual environment (Python 3.12)

```bash
python3.12 -m venv .venv
```

Activate it:

```bash
source .venv/bin/activate
```

### 2. Install dependencies

```bash
pip install -U pip
pip install -r requirements.txt
playwright install
```

---

## Running the Tests

### Step 1 — Fill in the Excel test cases

Open `Assignment 1 - Test cases.xlsx` and fill in the following columns:

| Column | Description |
|--------|-------------|
| TC ID | Test case identifier (e.g. `Pos_0001`) |
| Input length type | `S` (≤30 chars), `M` (31–299 chars), or `L` (300–450 chars) |
| Input | Singlish input text |
| Expected output | Expected Sinhala translation |

> Do **not** enter values under `Actual output` or `Status` — these are filled in automatically by the script.

### Step 2 — Run the Playwright script

```bash
python test_automation.py --excel "Assignment 1 - Test cases.xlsx" --url "https://www.pixelssuite.com/chat-translator" --wait-ms 5000 --type-delay-ms 80 --slow-mo-ms 200 --save-every 1 --keep-open
```

| Flag | Description |
|------|-------------|
| `--excel` | Path to the Excel file |
| `--url` | URL of the chat translator page |
| `--wait-ms` | Milliseconds to wait for a translation response |
| `--type-delay-ms` | Delay between keystrokes in milliseconds |
| `--slow-mo-ms` | Slow motion delay for browser actions |
| `--save-every` | Save results to Excel after every N test cases |
| `--keep-open` | Keep the browser open after the script finishes |

### Step 3 — Check results

Reopen `Assignment 1 - Test cases.xlsx` and verify that the `Actual output` and `Status` columns have been filled in automatically.

### Step 4 — Add analysis columns

After reviewing the results, manually add the following two columns next to the `Status` column:

| Column | Description |
|--------|-------------|
| Singlish input types covered | e.g. Question forms, Requests, Romanization / Spelling Variants |
| Evidence or rationale for the input type covered | Brief justification referencing the input text |

Refer to Appendix 2 of the assignment document for guidance and examples.
