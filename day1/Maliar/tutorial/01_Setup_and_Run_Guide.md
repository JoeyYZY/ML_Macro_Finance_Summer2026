# Maliar Hands-on Tutorial Setup and Run Guide

Last updated: 2026-07-05

This guide is for Day 1 Tutorial 1:

```text
Getting Started with TensorFlow / PyTorch / JAX and Hands-on Practice
```

Instructor: Serguei Maliar

Please complete the local environment check in this guide before the tutorial begins. TensorFlow is the main track for the session. PyTorch and JAX are optional comparisons only.

If you are reading the folder for the first time, start with this file and then open `02_TensorFlow_Minimal_Intro.ipynb`.

## 1. Tutorial Overview

The tutorial will use a guided walkthrough format:

- The instructor will run the notebooks on the projector and explain the code.
- Students should run the classroom versions on their own laptops when possible.
- The focus is on the relationship between code structure, model equations, residuals, loss functions, and training loops.
- Full training runs and slower simulation plots are after-class tasks.

Suggested material sequence:

| File | When to use it | Purpose |
| --- | --- | --- |
| `01_Setup_and_Run_Guide.md` | Morning / before class | Prepare a local Python environment and complete the minimal check |
| `02_TensorFlow_Minimal_Intro.ipynb` | Around noon / beginning of class | Prepare or review TensorFlow basics |
| `03_MMW_Growth_Model_Walkthrough.ipynb` | Main tutorial | Follow the instructor through the MMW growth-model code |
| `04_KS_Model_Walkthrough.ipynb` | Main tutorial | Follow the instructor through the Krusell-Smith short-run code |
| `05_KS_Model_Full_Version.ipynb` | After class | Run or inspect the full original Krusell-Smith notebook |

You do not need to run notebooks 03 or 04 fully before class. Before the tutorial, the main goal is to confirm that you can open a notebook and run the TensorFlow check.

## 2. Minimum Pre-Class Preparation

Before the tutorial, please:

1. Install Miniconda or Anaconda.
2. Create an isolated `maliar-handson` environment.
3. Install TensorFlow, NumPy, Matplotlib, Jupyter, and the other core packages.
4. Open `02_TensorFlow_Minimal_Intro.ipynb` and run the first environment-check cell.

Minimum check:

- Open Jupyter Notebook.
- Open `02_TensorFlow_Minimal_Intro.ipynb`.
- Run the first environment-check cell.
- Run the first tensor/shape/dtype cells.
- Do not run full MMW or Krusell-Smith training before class.

If you have environment issues, you may use AI tools to help with installation, interpret the error message, and check whether the command was run in the correct environment. If it still does not work, save the full error message and ask TA Peiyuan Zhang during a break before the tutorial if possible. If an individual environment cannot be fixed during class, follow the instructor's screen first and continue setup after class.

## 3. Windows Quick Setup

### 3.1 Install Miniconda

1. Go to the official Anaconda/Miniconda website.
2. Download the Windows 64-bit Miniconda installer.
3. Run the installer with the default options.
4. After installation, open `Anaconda Prompt` or `Miniconda Prompt` from the Start menu.

### 3.2 Create the Environment

In `Anaconda Prompt` / `Miniconda Prompt`, run:

```bash
conda create -n maliar-handson python=3.10
conda activate maliar-handson
pip install numpy matplotlib jupyter ipykernel tqdm tensorflow==2.13.1
```

If installation is slow, wait for a while. If it fails repeatedly, save the error message, use an AI tool to identify the likely cause if helpful, and ask TA Peiyuan Zhang during a break.

### 3.3 Start Jupyter

In the same prompt, run:

```bash
jupyter notebook
```

The browser should open Jupyter. Navigate to the tutorial folder and open:

```text
02_TensorFlow_Minimal_Intro.ipynb
```

## 4. macOS Quick Setup

### 4.1 Install Miniconda

1. Go to the official Anaconda/Miniconda website.
2. Choose the installer for your machine:
   - Apple Silicon / M-series chip: choose the macOS Apple Silicon version.
   - Intel chip: choose the macOS Intel version.
3. The `.pkg` graphical installer is recommended. Use the default options.
4. After installation, open `Terminal`.

### 4.2 Create the Environment

In `Terminal`, run:

```bash
conda create -n maliar-handson python=3.10
conda activate maliar-handson
pip install numpy matplotlib jupyter ipykernel tqdm tensorflow==2.13.1
```

If the `conda` command is not found, close and reopen `Terminal`. If it still fails, save the error message and ask TA Peiyuan Zhang during a break.

### 4.3 Start Jupyter

In the same Terminal, run:

```bash
jupyter notebook
```

The browser should open Jupyter. Navigate to the tutorial folder and open:

```text
02_TensorFlow_Minimal_Intro.ipynb
```

## 5. If Jupyter Cannot See the Environment

If the packages are installed but the notebook still cannot import TensorFlow, the Jupyter kernel may not be using the correct environment.

Run:

```bash
conda activate maliar-handson
pip install ipykernel
python -m ipykernel install --user --name maliar-handson --display-name "Python (maliar-handson)"
```

Then select:

```text
Kernel -> Change Kernel -> Python (maliar-handson)
```

## 6. Basic Environment Check

First run:

```python
import sys
import numpy as np
import matplotlib
import tensorflow as tf

print("Python:", sys.version.split()[0])
print("NumPy:", np.__version__)
print("Matplotlib:", matplotlib.__version__)
print("TensorFlow:", tf.__version__)
```

If you see version numbers, the basic environment is available.

Then run a minimal TensorFlow check:

```python
x = tf.constant([[1.0, 2.0], [3.0, 4.0]])
w = tf.Variable([[0.5], [1.0]])

with tf.GradientTape() as tape:
    y = x @ w
    loss = tf.reduce_mean(y ** 2)

grad = tape.gradient(loss, w)

print("y:", y.numpy())
print("loss:", float(loss.numpy()))
print("gradient:", grad.numpy())
```

If this code runs, you should be able to continue with the basic parts of notebook 02.

## 7. Are PyTorch and JAX Required?

No.

The tutorial title mentions TensorFlow / PyTorch / JAX, but the two main reference codes are TensorFlow-based. PyTorch and JAX are optional comparisons and are not required for the main workflow.

Optional check:

```python
try:
    import torch
    print("PyTorch:", torch.__version__)
except Exception as e:
    print("PyTorch not available:", repr(e))

try:
    import jax
    print("JAX:", jax.__version__)
except Exception as e:
    print("JAX not available:", repr(e))
```

PyTorch and JAX should not be required for the local environment. Install them separately only if needed:

```bash
pip install torch
pip install jax jaxlib
```

## 8. What You Do Not Need Before Class

Before class, you do not need to:

- Run `03_MMW_Growth_Model_Walkthrough.ipynb` fully.
- Run `04_KS_Model_Walkthrough.ipynb` fully.
- Run `05_KS_Model_Full_Version.ipynb` before class.
- Run `train_me(50000)`.
- Solve all GPU/CUDA issues. GPU is not required for this tutorial.

If you can run the first few cells of notebook 02, you have met the minimum pre-class requirement.

## 9. Troubleshooting

| Issue | Typical symptom | Response |
| --- | --- | --- |
| TensorFlow missing | `ModuleNotFoundError: No module named 'tensorflow'` | Activate `maliar-handson`, then run `pip install tensorflow==2.13.1` |
| Python too new | TensorFlow installation fails | Use Python 3.10 |
| Wrong notebook kernel | Conda has packages but notebook cannot import them | Install `ipykernel` and switch kernel |
| GPU/CUDA error | Driver or CUDA message | GPU is not required; disable GPU or restart |
| Graphviz error | `plot_model` fails | Skip it and use `model.summary()` |
| Training too slow | Cell runs for too long | Lower steps, batch size, or agents; use short-run |
| Shape mismatch | `InvalidArgumentError` / dimension mismatch | Print `.shape` and check batch and agent dimensions |
| Installation repeatedly fails | Slow downloads or dependency resolution failure | Save the error message, use AI tools to interpret it if helpful, and ask TA Peiyuan Zhang during a break or after class |

Optional CPU-only line:

```python
import tensorflow as tf
tf.config.set_visible_devices([], "GPU")
```

If this line itself fails, restart the kernel and skip it.

## 10. After-Class Reproduction Path

Recommended order:

1. Re-run `02_TensorFlow_Minimal_Intro.ipynb` and finish the toy residual example.
2. Run the short version of `03_MMW_Growth_Model_Walkthrough.ipynb`.
3. Increase MMW `CLASSROOM_STEPS`, for example to `5000`, `20000`, or `50000`.
4. Run `04_KS_Model_Walkthrough.ipynb` in reduced mode.
5. Open `05_KS_Model_Full_Version.ipynb` for the full original Krusell-Smith run and precomputed outputs.

Change only one parameter at a time:

- `TRAINING_STEPS`
- `BATCH_SIZE`
- `AGENTS`
- hidden layer width
- learning rate
