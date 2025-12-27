# Git History Reconstruction: Neural Network Training Techniques

This document describes the expanded and reconstructed development history for the Neural Network Training Techniques project. This version contains **15 steps** (expanded from the previous 10 steps), showing a more granular and realistic progression from initial setup to the final portfolio-ready state.

---

## History Expansion Note

**Previous run:** N_old = 10 steps  
**Current run:** N_new = 15 steps  
**Multiplier achieved:** 1.5×

### Expansion Strategy

This expanded history uses two complementary strategies to increase the step count while maintaining realism:

1. **Step Splitting**: Large commits from the previous history were split into smaller, more atomic changes:
   - **Old Step 03** (Notebook creation) → **New Steps 03-04**: Separated title/intro from section structure
   - **Old Step 05** (Baseline network) → **New Steps 06-07**: Split network definition from instantiation
   - **Old Step 06** (Training) → **New Steps 08-09**: Separated training loop from evaluation
   - **Old Step 07** (BatchNorm network) → **New Steps 10-11**: Created oops/hotfix sequence (see below)
   - **Old Step 08** (Visualization) → **New Steps 12-13**: Split training runs from visualization

2. **Oops → Hotfix Sequence**: Inserted a realistic mistake and immediate fix:
   - **Step 10 (oops)**: Added BatchNorm network with incorrect layer order
     - **Mistake**: BatchNorm layers placed BEFORE Linear layers instead of AFTER
     - **Why this is wrong**: BatchNorm should normalize the output of linear transformations, not the input
     - **Result**: This would lead to suboptimal performance and incorrect normalization statistics
   - **Step 11 (hotfix)**: Fixed BatchNorm layer positioning
     - **Fix**: Moved BatchNorm layers to correct position (after Linear, before ReLU)
     - **How noticed**: During code review before running training
     - **Resolution**: Corrected the forward pass to: Linear → BatchNorm → ReLU

### Mapping: Old Steps → New Steps

| Old Step | Description | New Steps | Expansion Details |
|----------|-------------|-----------|-------------------|
| 01 | Initial commit | 01 | Unchanged |
| 02 | Add requirements | 02 | Unchanged |
| 03 | Create notebook structure | 03-04 | Split: title/intro (03), section headers (04) |
| 04 | Data loading | 05 | Renumbered |
| 05 | Baseline network | 06-07 | Split: definition (06), instantiation (07) |
| 06 | Training loop | 08-09 | Split: training (08), evaluation (09) |
| 07 | BatchNorm network | 10-11 | **Oops/hotfix**: wrong order (10), fixed (11) |
| 08 | Visualization | 12-13 | Split: training runs (12), plots/analysis (13) |
| 09 | README enhancement | 14 | Renumbered |
| 10 | Final polish | 15 | Renumbered |

---

## Development Narrative

This project evolved through 15 logical development stages, each building upon the previous work. The progression demonstrates realistic development practices including incremental feature addition, mistake correction, and iterative refinement.

---

## Step-by-Step Progression

### Step 01: Initial Repository Setup
**Commit Message:** `Initial commit: Set up neural network training project`

**Changes:**
- Created README.md with project overview and basic structure
- Added .gitignore with Python/Jupyter patterns
- Established project foundation

**Rationale:** Every project starts with initialization. This represents the moment a developer creates a new repository and sets up the basic file structure.

**Files:** 2 (README.md, .gitignore)

---

### Step 02: Dependencies Configuration
**Commit Message:** `Add requirements.txt with PyTorch dependencies`

**Changes:**
- Added requirements.txt with PyTorch, NumPy, Matplotlib, Jupyter
- Specified version constraints for reproducibility

**Rationale:** After initializing, the next logical step is defining dependencies so the development environment can be set up. This allows other developers to replicate the environment.

**Files:** 3 (+requirements.txt)

---

### Step 03: Notebook Creation with Title and Introduction
**Commit Message:** `Create notebook with project title and introduction`

**Changes:**
- Created batch_normalization_study.ipynb
- Added title cell: "Neural Network Training Techniques"
- Added introduction explaining the batch normalization study
- Described the comparison approach (baseline vs. BatchNorm)

**Rationale:** With dependencies defined, the developer creates the main notebook file and writes the introduction. Starting with documentation helps clarify the project goals.

**Files:** 4 (+batch_normalization_study.ipynb)

---

### Step 04: Add Section Structure
**Commit Message:** `Add section headers and notebook structure`

**Changes:**
- Added section headers for:
  - Setup and Data Loading
  - Baseline Network
  - Network with Batch Normalization
  - Performance Comparison
- Created skeleton for the notebook flow

**Rationale:** Before writing code, establishing the structure helps organize thoughts and provides a roadmap for implementation.

**Files:** 4 (notebook updated with structure)

---

### Step 05: Data Loading Implementation
**Commit Message:** `Implement FashionMNIST data loading with PyTorch`

**Changes:**
- Added imports (torch, torchvision, torch.nn, torch.nn.functional, matplotlib, numpy)
- Implemented data transformers (ToTensor, Normalize)
- Set up training and test dataloaders with batch size 64
- Configured FashionMNIST dataset for automatic download

**Rationale:** Before building models, data pipelines must be established. This is a fundamental step in any ML project. The data loading must be completed before any model training can occur.

**Files:** 4 (notebook updated with imports and data loading)

---

### Step 06: Define Baseline Network Class
**Commit Message:** `Implement baseline feed-forward neural network architecture`

**Changes:**
- Defined NeuralNetwork class inheriting from nn.Module
- Added architecture: 784 → 64 → 32 → 10
- Implemented three linear layers (fc1, fc2, fc3)
- Defined forward pass with flatten, ReLU activations

**Rationale:** The core model architecture is implemented first. Starting with the baseline provides a reference point for comparison. The class definition is separated from instantiation for clarity.

**Files:** 4 (notebook updated with network class)

---

### Step 07: Instantiate and Verify Network
**Commit Message:** `Create baseline network instance and verify architecture`

**Changes:**
- Instantiated baseline network: `model_baseline = NeuralNetwork()`
- Printed model architecture for verification
- Confirmed layer dimensions and parameter counts

**Rationale:** After defining the class, the developer creates an instance to verify the architecture is correct before proceeding to training. This is a natural checkpoint in development.

**Files:** 4 (notebook updated with network instantiation)

---

### Step 08: Implement Training Loop
**Commit Message:** `Add training loop with SGD optimizer and cross-entropy loss`

**Changes:**
- Implemented training function with epoch loop
- Added SGD optimizer with learning rate 0.001
- Configured CrossEntropyLoss
- Added per-epoch loss and accuracy tracking
- Set device configuration (CPU/GPU)

**Rationale:** With the model defined and instantiated, the training infrastructure is needed to actually train the network. The training loop is implemented before evaluation to establish the training process.

**Files:** 4 (notebook updated with training loop)

---

### Step 09: Add Evaluation Function
**Commit Message:** `Implement test set evaluation and baseline training`

**Changes:**
- Added evaluation function for test accuracy
- Implemented test loop with no_grad context
- Trained baseline network for 5 epochs
- Recorded baseline accuracy results

**Rationale:** After implementing training, evaluation is needed to measure performance. Training the baseline first establishes a reference point before implementing the BatchNorm variant.

**Files:** 4 (notebook updated with evaluation and baseline results)

---

### Step 10: Add Batch Normalization Network (OOPS!)
**Commit Message:** `Implement batch normalization enhanced network`

**Changes:**
- Added NeuralNetworkWithBatchNorm class
- **MISTAKE**: Placed BatchNorm1d layers BEFORE Linear layers
  - bn1 applied before fc1
  - bn2 applied after fc1 but before fc2
  - bn3 applied after fc2 but before fc3
- Forward pass: BN → Linear → ReLU (incorrect order!)

**Rationale:** After establishing baseline functionality, the developer implements the experimental enhancement. However, this commit contains a **realistic mistake** - the BatchNorm layers are positioned incorrectly. This would be caught during code review or when comparing against PyTorch best practices.

**Why this is wrong:**
- BatchNorm should normalize the linear transformation outputs, not the inputs
- The current order means bn1 normalizes raw input features (already normalized)
- This defeats the purpose of batch normalization in addressing internal covariate shift

**Files:** 4 (notebook updated with incorrect BatchNorm network)

---

### Step 11: Fix Batch Normalization Layer Order (HOTFIX!)
**Commit Message:** `Fix: Correct BatchNorm layer positioning after linear layers`

**Changes:**
- **FIXED** BatchNorm layer positioning
- Corrected order: Linear → BatchNorm → ReLU
- Updated forward pass:
  - flatten → fc1 → bn1 → ReLU
  - → fc2 → bn2 → ReLU  
  - → fc3 → output
- Added network instantiation

**Rationale:** During code review, the developer noticed the BatchNorm placement was incorrect. This hotfix corrects the architecture to follow best practices: apply batch normalization to the output of linear transformations, before the activation function.

**How noticed:** Code review and reference to PyTorch documentation on proper BatchNorm usage.

**Resolution:** Restructured the forward pass to apply BatchNorm after each linear layer but before the activation.

**Files:** 4 (notebook fixed with correct BatchNorm network)

---

### Step 12: Add Training Runs for Both Networks
**Commit Message:** `Train both baseline and BatchNorm networks`

**Changes:**
- Trained baseline network (if not already trained)
- Trained BatchNorm network using same training loop
- Recorded training accuracies for both networks
- Prepared data for comparative analysis

**Rationale:** With both network architectures correctly implemented, the developer trains them under identical conditions to enable fair comparison.

**Files:** 4 (notebook updated with training for both networks)

---

### Step 13: Add Performance Comparison and Visualization
**Commit Message:** `Add performance visualization and comparative analysis`

**Changes:**
- Implemented matplotlib visualization comparing accuracies
- Created line plots showing training curves for both networks
- Added analysis section discussing:
  - Convergence speed differences
  - Final accuracy comparison
  - BatchNorm stability benefits
  - Training dynamics observations

**Rationale:** With both models trained, the developer creates visualizations to communicate results effectively. The analysis section interprets the findings and draws conclusions.

**Files:** 4 (notebook completed with all analysis cells)

---

### Step 14: Enhance README Documentation
**Commit Message:** `Enhance README with comprehensive project documentation`

**Changes:**
- Expanded README with detailed sections:
  - Problem statement and approach
  - Comprehensive setup instructions (cross-platform)
  - Usage guide with step-by-step notebook execution
  - Dataset information (FashionMNIST auto-download)
  - Expected outputs and results
  - Reproducibility notes
  - Troubleshooting section
  - Key findings summary
  - Acknowledgments
- Professional framing throughout
- Aligned with project_identity.md

**Rationale:** As the project nears completion, documentation is enhanced for clarity and professional presentation. This makes the project accessible to other developers and potential employers.

**Files:** 4 (README.md significantly expanded)

---

### Step 15: Final Polish and Project Identity
**Commit Message:** `Add project metadata and final portfolio refinements`

**Changes:**
- Created project_identity.md with:
  - Professional display title and tagline
  - GitHub description and topics
  - Tech stack documentation
  - Problem statement and approach overview
  - Inputs and outputs summary
- Added report.md documenting the portfolio transformation
- Added suggestion.txt with portfolio-readiness findings
- Added suggestions_done.txt with applied changes
- Final .gitignore adjustments
- All assignment traces removed
- Portfolio-ready state achieved

**Rationale:** The final step includes metadata, identity files, and ensuring everything is polished for portfolio presentation. This completes the transformation from working project to portfolio piece.

**Files:** 8 (all project files including documentation)

---

## Technical Notes

### Snapshot Format
- Each step directory contains a **complete snapshot** of the project at that point in time
- Snapshots are full copies, not diffs
- Files are copied exactly (byte-for-byte) without reformatting
- Snapshots exclude `.git/` and `history/` directories to avoid recursion

### Realism Constraints
- Progression follows logical development order:
  - Infrastructure (repo setup, dependencies)
  - Data pipeline (loading, preprocessing)
  - Models (baseline first, then enhancements)
  - Training and evaluation
  - Analysis and visualization
  - Documentation
- Each step represents a cohesive unit of work that could be a single commit
- No "time travel" - later features don't appear in earlier steps
- Dependencies are introduced before they're used in code
- Includes realistic mistake and correction (steps 10-11)

### Oops → Hotfix Realism
The mistake in step 10 (incorrect BatchNorm positioning) is:
- **Plausible**: Easy to make when first learning BatchNorm
- **Detectable**: Would be caught during code review or testing
- **Non-breaking**: Code would run but perform suboptimally
- **Quickly fixable**: Simple reordering in the forward pass
- **Educational**: Demonstrates proper BatchNorm usage

### Verification
- Step 15 matches the current repository working tree exactly (excluding history/)
- All files in Step 15 are identical to the portfolio-ready state
- No files from `history/` appear in any snapshot
- No `.git/` directories in any snapshot
- Progressive file additions follow logical order

---

## Usage

To explore the development history:

1. **View a specific step:**
   ```bash
   cd history/steps/step_XX/
   ls -la
   ```

2. **Compare consecutive steps:**
   ```bash
   diff -r history/steps/step_10/ history/steps/step_11/
   ```
   This shows the BatchNorm layer order fix between steps 10 and 11.

3. **Track file evolution:**
   ```bash
   # See when notebook was created
   ls history/steps/step_03/batch_normalization_study.ipynb
   
   # See when README was enhanced  
   diff history/steps/step_13/README.md history/steps/step_14/README.md
   ```

4. **Understand the oops/hotfix:**
   - View `history/steps/step_10/batch_normalization_study.ipynb` to see the incorrect BatchNorm placement
   - View `history/steps/step_11/batch_normalization_study.ipynb` to see the corrected version
   - Compare to understand what changed

Each step is self-contained and represents a working state (except step 10, which contains a known issue fixed in step 11). This reconstructed history demonstrates realistic development practices and helps understand how the project evolved from concept to completion.

---

## Summary Statistics

| Metric | Value |
|--------|-------|
| Total Steps | 15 |
| Previous Steps | 10 |
| Expansion Factor | 1.5× |
| Oops/Hotfix Sequences | 1 (steps 10-11) |
| Split Commits | 4 |
| Files in Final Step | 8 |
| Total Snapshots Size | ~15 complete project states |

This expanded history provides a more granular view of the development process while maintaining realism and demonstrating common development patterns including incremental changes and error correction.
