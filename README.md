# Tall Emu Freight Cost Automation

Automates updating freight costs in Tall Emu CRM from Team Global Express (iPEC) PDF invoices using Playwright browser automation.

## What it does

1. Parses iPEC PDF invoices and extracts freight charges per Tall Emu invoice number
2. Logs into Tall Emu and searches for each invoice
3. Enters the freight cost into the Connote Number field
4. Updates the Freight TE line item cost
5. Fills in the tracking number if the field is blank
6. Handles Lactalis invoices with a special cost adjustment formula
7. Archives processed PDFs with a summary report

## Setup

**1. Install dependencies**
```bash
pip install -r requirements.txt
playwright install chromium
```

**2. Create a `.env` file** in the project root:
```
TALL_EMU_URL=https://your-instance.tallemu.com
TALL_EMU_EMAIL=your@email.com
TALL_EMU_PASSWORD=yourpassword
```

**3. Drop PDF invoices** into the `invoices/` folder.

## Usage

```bash
# Process all PDFs in invoices/
python main.py

# Process a specific PDF
python main.py invoices/IPec_0433-80332442_10225416.pdf

# Parse only — don't touch Tall Emu
python main.py --dry-run

# Run without a visible browser window
python main.py --headless

# Debug PDF parsing output
python main.py --debug-pdf
```

## File Structure

```
├── main.py               # Entry point & CLI
├── parse_invoice.py      # PDF parsing logic
├── tall_emu.py           # Playwright browser automation
├── diagnose_pdf.py       # PDF diagnostic utility
├── discover_selectors.py # Tall Emu UI selector discovery tool
├── requirements.txt      # Python dependencies
├── .env                  # Credentials (not committed)
└── invoices/             # Drop PDFs here (not committed)
```

## Requirements

- Python 3.8+
- Chromium (installed via `playwright install chromium`)

## Code

The source code is available on request. Feel free to open an issue or reach out directly.
