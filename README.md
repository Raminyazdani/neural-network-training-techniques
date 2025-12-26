# Neural Network Training Techniques

> Exploring batch normalization and optimization techniques for training deep neural networks

## Overview

This project demonstrates the impact of **batch normalization** on neural network training. It implements and compares two feed-forward networks on the FashionMNIST dataset: a baseline network and an identical architecture enhanced with batch normalization layers. The comparative study reveals how batch normalization stabilizes learning, accelerates convergence, and improves final model performance.

### The Problem

Training deep neural networks faces a challenge called **internal covariate shift** - the distribution of inputs to each layer changes during training as the weights of previous layers are updated. This "moving target" phenomenon slows down learning and can make training unstable, requiring careful tuning of learning rates and initialization.

### The Approach

Batch normalization addresses this by normalizing layer inputs during training, which:
- Stabilizes the distribution of inputs to each layer
- Enables higher learning rates
- Reduces sensitivity to initialization
- Acts as a regularizer, sometimes reducing the need for dropout

This project implements both approaches to empirically demonstrate these benefits.

## Tech Stack

- **Python 3.x** - Primary language
- **PyTorch 2.0+** - Deep learning framework
- **Jupyter Notebook** - Interactive development environment
- **NumPy** - Numerical computations
- **Matplotlib** - Visualization
- **FashionMNIST** - Dataset (28×28 grayscale images, 10 clothing categories)

## Repository Structure

```
neural-network-training-techniques/
├── batch_normalization_study.ipynb  # Main analysis notebook
├── requirements.txt                 # Python dependencies
├── README.md                        # This file
├── .gitignore                       # Git ignore patterns
└── project_identity.md              # Project metadata
```

## Setup

### Prerequisites

- Python 3.8 or higher
- pip (Python package manager)

### Installation

1. Clone the repository:
```bash
git clone https://github.com/Raminyazdani/neural-network-training-techniques.git
cd neural-network-training-techniques
```

2. Install dependencies:
```bash
pip install -r requirements.txt
```

Or install individually:
```bash
pip install torch>=2.0.0 numpy>=1.21.0 matplotlib>=3.3.0 jupyter>=1.0.0
```

## Usage

### Running the Notebook

1. Start Jupyter Notebook:
```bash
jupyter notebook batch_normalization_study.ipynb
```

2. In the browser, execute cells sequentially (Shift+Enter or use "Run All" from the Cell menu)

### What the Notebook Does

1. **Data Loading**: Automatically downloads FashionMNIST dataset via PyTorch
2. **Baseline Network**: Trains a 3-layer feed-forward network (784→64→32→10)
3. **Batch-Normalized Network**: Trains the same architecture with BatchNorm layers
4. **Comparison**: Visualizes accuracy curves and analyzes performance differences

## Data

**FashionMNIST Dataset:**
- **Source**: Automatically downloaded by PyTorch on first run
- **Size**: 60,000 training images, 10,000 test images
- **Format**: 28×28 grayscale images
- **Classes**: 10 clothing categories (T-shirt, Trouser, Pullover, Dress, Coat, Sandal, Shirt, Sneaker, Bag, Ankle boot)
- **Storage**: Downloads to `~/.pytorch/datasets/FashionMNIST/` by default

No manual data setup required - PyTorch handles downloading and caching automatically.

## Outputs

The notebook produces:

1. **Training Metrics**:
   - Per-epoch accuracy for both networks
   - Test set evaluation results

2. **Visualizations**:
   - Comparative accuracy plots across epochs
   - Performance trend analysis

3. **Analysis**:
   - Observation of convergence speed differences
   - Discussion of stability improvements
   - Quantitative comparison of final accuracies

### Expected Results

Typical observations from running the notebook:
- **Baseline network**: Slower initial learning, gradual accuracy improvement (~20% → ~56% over 5 epochs)
- **Batch-normalized network**: Rapid early learning, higher final accuracy (~72% → ~81% over 5 epochs)
- **Convergence**: BatchNorm network reaches baseline's final accuracy by epoch 1-2

## Reproducibility

### Determinism

The notebook uses default PyTorch behavior without explicit random seeds. For fully reproducible results:

```python
import torch
import random
import numpy as np

# Add to notebook
torch.manual_seed(42)
random.seed(42)
np.random.seed(42)
```

### Environment

Tested on:
- Python 3.12.1
- PyTorch 2.0+
- CPU and CUDA-enabled GPUs

Results may vary slightly across different hardware and PyTorch versions due to numerical precision differences.

## Troubleshooting

### Import Errors

```
ModuleNotFoundError: No module named 'torch'
```
**Solution**: Install dependencies with `pip install -r requirements.txt`

### CUDA/GPU Issues

If you encounter GPU memory errors or CUDA unavailability:
- The notebook runs on CPU by default (no CUDA required)
- To force CPU usage: `device = torch.device('cpu')`
- For GPU: Ensure CUDA-compatible PyTorch is installed

### Memory Issues

```
RuntimeError: out of memory
```
**Solution**: If running on limited hardware, reduce batch size in the dataloader (currently 64)

### Download Failures

If FashionMNIST download fails:
- Check internet connection
- Verify access to `http://fashion-mnist.s3-website.eu-central-1.amazonaws.com/`
- Manual download: https://github.com/zalandoresearch/fashion-mnist

### Notebook Kernel Crashes

- Restart kernel and clear outputs: Kernel → Restart & Clear Output
- Check system resources (RAM, disk space)
- Try running cells individually instead of "Run All"

## Key Findings

From the comparative analysis:

1. **Faster Convergence**: Batch normalization achieves high accuracy much earlier in training
2. **Higher Final Performance**: ~25 percentage point improvement in test accuracy
3. **Training Stability**: Reduced variance in accuracy between epochs
4. **Learning Dynamics**: BatchNorm enables stable learning with fixed hyperparameters

These results validate batch normalization as an essential technique for training modern deep networks.

## Further Exploration

Potential extensions of this work:
- Experiment with different network depths
- Compare with other normalization techniques (Layer Norm, Group Norm)
- Analyze impact on different datasets (CIFAR-10, MNIST)
- Study interaction with dropout and other regularization
- Investigate BatchNorm's effect on gradient flow

## License

This project is available for educational and portfolio purposes.

## Acknowledgments

- **Dataset**: FashionMNIST by Zalando Research
- **Framework**: PyTorch team for the excellent deep learning library
- **Inspiration**: Ioffe & Szegedy (2015) - "Batch Normalization: Accelerating Deep Network Training by Reducing Internal Covariate Shift"

