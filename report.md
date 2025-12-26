# Portfolio Transformation Report

## PHASE 0 — Initial Setup

### 0.1 Created Required Deliverable Files
- Created `report.md` (this file)
- Created `suggestion.txt` (empty placeholder)
- Created `suggestions_done.txt` (empty placeholder)
- Created `project_identity.md` (empty placeholder)

### 0.2 Updated Copilot Guidance
- Updated `.github/copilot-instructions.md` to reflect single-project repository structure
- Noted: This is a single-project repo (neural-network-training-techniques), not multi-project
- Added rules for history snapshot generation to exclude history/ folder itself

---

## PHASE 1 — Project Understanding & Professional Identity

### 1.1 Project Analysis

**Domain/Problem:**
- Addresses internal covariate shift in deep neural network training
- Demonstrates batch normalization as a solution to stabilize learning and accelerate convergence

**Method/Approach:**
- Comparative study: baseline network vs. batch-normalized network
- Both networks: 3 hidden layers, ReLU activations, trained on FashionMNIST
- Architecture: Input(784) → 64 → 32 → 10 classes
- Training: SGD optimizer, learning rate 0.001, 5 epochs, batch size 64

**Stack:**
- Python 3.x with Jupyter Notebook
- PyTorch for model implementation and training
- NumPy for numerical operations
- Matplotlib for visualization
- FashionMNIST dataset (auto-downloaded)

**Current Structure:**
```
.
├── Assignment_6.ipynb    # Main notebook (academic naming)
├── README.md             # Academic-framed README
├── requirements.txt      # Dependencies (adequate)
└── .github/
    └── copilot-instructions.md
```

### 1.2 Professional Identity Decision

Created `project_identity.md` with:
- **Display Title:** Neural Network Training Techniques
- **Repo Slug:** `neural-network-training-techniques` ✓ (already professional)
- **Tagline:** Exploring batch normalization and optimization techniques
- **Description:** Practical exploration using PyTorch on FashionMNIST
- **Stack Tags:** neural-networks, deep-learning, batch-normalization, pytorch, machine-learning, optimization
- **Topics:** 10 relevant keywords identified

### 1.3 Naming Alignment Plan

**Files requiring rename:**
1. `Assignment_6.ipynb` → `batch_normalization_study.ipynb`
   - Rationale: Remove academic naming, reflect content focus
   - Safe: No code imports this file, only documentation references

**Content requiring reframing:**
1. Notebook Cell 0: Remove "NNTI Assignment 6" header and student ID fields
2. Notebook section headers: Remove task numbering (1., 2., 3.) and point values
3. README.md: Complete rewrite to portfolio-grade (aligned with project_identity.md)

**Structure assessment:**
- Current flat structure is appropriate for a single-notebook project
- No folder reorganization needed
- Paths: Need to verify no absolute paths exist (preliminary scan looks clean)

**What stays unchanged:**
- requirements.txt (already professional)
- .gitignore (will create if missing)
- Code logic and results (behavior-preserving)
- FashionMNIST dataset download mechanism (standard PyTorch)

---

## PHASE 2 — Pre-Change Audit

### 2.1 Audit Methodology
- Scanned all files excluding .git and history/ (not yet created)
- Used Python script to analyze notebook cells systematically
- Checked README for folder name references and academic language
- Searched for absolute path patterns (Windows, macOS, Linux)

### 2.2 Findings Summary

**Assignment/Academic Traces Detected:**
- ✗ Notebook cell 0: "NNTI Assignment 6" title, student ID fields, submission instructions
- ✗ Notebook cell 1: "In this exercise" language
- ✗ Notebook cell 2: "Your task is to..." assignment language, "(1 point)" notation
- ✗ Notebook cell 8: "(0.5 points)" notation
- ✗ Notebook cell 11: "(0.25 points)" notation, "discuss what you observe" prompt
- ✗ Notebook cell 13: "Your Answer:" response format
- ✗ README.md line 1: "NNTI Assignment 6" title
- ✗ README.md line 3: "Project Type: University Assignment/Task"
- ✗ README.md line 8: "This is Assignment 6 for the NNTI course..."
- ✗ README.md lines 21-47: References to "Submission_7_-_7072982_Syed_Rumman_Ali" folder

**Path Issues:**
- ✓ No absolute Windows paths detected
- ✓ No absolute Unix/macOS paths detected
- ✓ No brittle path references found
- All paths are relative or use standard PyTorch dataset loading

**Misaligned Names:**
- ✗ Filename: "Assignment_6.ipynb" (should be descriptive of content)
- ✗ README references to old submission folder name

**Missing Files:**
- ✗ No .gitignore present (should have Python/Jupyter patterns)

### 2.3 Ledger Created
All findings documented in `suggestion.txt` with:
- 17 entries total
- TYPE classifications: RENAME(1), TRACE(14), DOC(1), STRUCTURE(1)
- Specific locators (cell indices, line numbers)
- Before/after snippets
- Clear rationale for each change
- All marked STATUS=PENDING

---
