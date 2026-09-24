![Python](https://img.shields.io/badge/Python-3.14-3776AB?style=flat-square&logo=python&logoColor=white)
![PyTorch](https://img.shields.io/badge/PyTorch-2.13-EE4C2C?style=flat-square&logo=pytorch&logoColor=white)
![CUDA](https://img.shields.io/badge/CUDA-13.2-76B900?style=flat-square&logo=nvidia&logoColor=white)
![uv](https://img.shields.io/badge/uv-0.12.4-DE5FE9?style=flat-square&logo=astral&logoColor=white)

# Machine Learning Lab Practicals for On Going Lab (Fall 2026) (CSP DC305)

## Practicals


<table>
<tr>
<th width="50px">S. No.</th>
<th width="520px">Practical</th>
<th width="260px">Notebook</th>
<th width="260px">Helper notebook / Exercise solutions</th>
</tr>
<tr>
<td>1</td>
<td><strong>Write</strong> <strong>a program to represent a dataset as feature vectors and to implement linear transformations and matrix--vector operations on it.</strong> Load a dataset and construct the feature matrix $X$ of order $n \times d$ and the target vector $y$; identify the feature space and its dimensionality; convert categorical attributes into numeric features. Formulate the same dataset once as a classification problem and once as a regression problem, and state the supervised and the unsupervised formulation of the same data. Implement vector addition, scaling, the inner product, norms and projection. Apply matrix--vector multiplication as a linear transformation to a two-dimensional dataset and plot the effect of rotation, scaling, reflection and shear. Verify that the composition of two transformations is the product of their matrices. Compute the covariance matrix of the dataset, obtain its eigenvalues and eigenvectors, and re-represent the data in the new basis. &amp; Unit 1: Representation (features); linear transformations and matrix--vector operations; problem formulations; paradigms of learning</td>
<td><a href="practical_notebooks/feature_vectors_and_linear_algebra_regression_explained_in_detail.ipynb">feature_vectors_and_linear_algebra_regression_practical.ipynb</a></td>
<td><a href="practical_notebooks/Encoding_Techniques_Complete_Guide.ipynb">Encoding_Techniques_Complete_Guide.ipynb</a> (encoding categorical data in machine learning in detail) <a href="practical_notebooks/Encoding_Techniques_Exercise_Solutions.ipynb">Encoding_Techniques_Exercise_Solutions.ipynb</a> (solutions to the exercises in the guide above)</td>
</tr>
<tr>
<td>2</td>
<td><strong>Write a program to study probability distributions on data and to implement a classifier based on prior probabilities and Bayes rule</strong>. Plot the empirical distribution of each attribute of a dataset and fit Bernoulli, Binomial and Gaussian models to it; compute the mean, variance and covariance matrix and compare the empirical moments with the theoretical ones. Construct the joint, marginal and conditional probability tables of a categorical dataset. Compute the prior probability of each class from the training data. Apply Bayes rule to obtain the posterior probability of each class for a given observation, verify the result numerically against the probability tables, and implement a classifier that assigns the class with the maximum posterior probability.</td>
<td><a href="practical_notebooks/probability_bayes_map_classifier.ipynb">probability_bayes_map_classifier.ipynb</a></td>
<td><a href="practical_notebooks/Probability_Bayes_MAP_Exercise_Solutions.ipynb">Probability_Bayes_MAP_Exercise_Solutions.ipynb</a> (solutions to the exercises in practical 2)</td>
</tr>
<tr>
<td>3</td>
<td><strong>Implement statistical decision theory and demonstrate the bias–variance trade-off:</strong> Generate data from known class-conditional distributions; compute the Bayes optimal decision rule under 0–1 loss, plot the Bayes decision boundary and compute the Bayes error rate, and compare it with the error of trained classifiers. For regression, verify empirically that the predictor minimising the expected squared error is the conditional mean $E[Y|X]$. Fit models of increasing complexity to repeated resamples of the data, estimate the bias, the variance and the irreducible error of each, and plot bias$^2$, variance and total error against model complexity to exhibit the trade-off.</td>
<td><a href="practical_notebooks/statistical_decision_theory_and_bias_variance_tradeoff.ipynb">statistical_decision_theory_and_bias_variance_tradeoff.ipynb</a></td>
<td><a href="practical_notebooks/statistical_decision_theory_and_bias_variance_tradeoff_exercise_solutions.ipynb">statistical_decision_theory_and_bias_variance_tradeoff_exercise_solutions.ipynb</a> (solutions to the exercises in practical 3)</td>
</tr>
</table>


> **Helper notebooks and exercise solutions** are optional supplementary material linked to a practical: helper notebooks give deeper background on a topic, and exercise-solutions notebooks work out the exercises posed in the main practical notebook. Neither is a separate lab practical.



## Environment Setup

This project uses **[uv](https://docs.astral.sh/uv/)**, a fast Python package and project manager to create an isolated, reproducible environment tied to this repository.

### Why use a project-based environment?

A project-based environment keeps all dependencies for this lab work in one place, separate from your system Python and other projects. That means:

- **Reproducibility**: everyone working on these practicals can install the same package versions.
- **Isolation**: packages installed here do not conflict with other courses or projects on your machine.
- **Simplicity**: `uv` handles Python version selection, virtual environments, and dependency locking in a single workflow.
- **Speed**: `uv` resolves and installs dependencies much faster than traditional tools.

After downloading or cloning this repository, follow the instructions for your platform below.

### Windows (Native)



#### 1. Install uv

Install **uv** for your system architecture. On **x86-64 (64-bit)** Windows, use:

```powershell
winget install astral.sh-uv
```

For other installation options, see the [uv installation guide](https://docs.astral.sh/uv/getting-started/installation/).

#### 2. Initialize the project (if starting from scratch)

If you are setting up a new copy of the project rather than cloning this repo:

```powershell
uv init ml_lab_practicals_csp_dc_305 --python 3.14
cd ml_lab_practicals_csp_dc_305
```

If you cloned this repository, `cd` into the project directory instead.

#### 3. Check your NVIDIA driver / CUDA version

```powershell
nvidia-smi
```

Note the **CUDA Version** shown in the output (e.g. `13.3`). Use the matching PyTorch wheel index below.

#### 4. Install PyTorch (GPU)

Choose the command that matches your CUDA version:


| CUDA version (from `nvidia-smi`)   | Command                                                                       |
| ---------------------------------- | ----------------------------------------------------------------------------- |
| 13.x (e.g. 13.3, use cu132 wheels) | `uv add torch torchvision --index-url https://download.pytorch.org/whl/cu132` |
| 13.0                               | `uv add torch torchvision --index-url https://download.pytorch.org/whl/cu130` |
| 12.6                               | `uv add torch torchvision --index-url https://download.pytorch.org/whl/cu126` |


Example (CUDA 13.3 / cu132 wheels):

```powershell
uv add torch torchvision --index-url https://download.pytorch.org/whl/cu132
```



#### 5. Install remaining dependencies

```powershell
uv add matplotlib seaborn pandas scikit-learn jupyterlab
```



#### 6. Run Jupyter Lab

```powershell
uv run jupyter lab
```

Open the notebook from the **Practicals** table above.

### Windows (WSL2)

[WSL2](https://learn.microsoft.com/en-us/windows/wsl/install) lets you run a Linux environment on Windows. If you do not have WSL2 yet, follow Microsoft's guide: [Install WSL](https://learn.microsoft.com/en-us/windows/wsl/install).

Once WSL2 is set up, open your Linux terminal (e.g. Ubuntu) and use the **Linux** instructions below inside your WSL distribution. Clone or copy the project into the WSL filesystem for best performance, then:

```bash
cd ml_lab_practicals_csp_dc_305
uv sync
uv run jupyter lab --ip=0.0.0.0
```

> **Note:** GPU support in WSL2 requires an up-to-date NVIDIA driver on Windows and the [CUDA on WSL guide](https://docs.nvidia.com/cuda/wsl-user-guide/index.html). Check `nvidia-smi` inside WSL before installing PyTorch wheels.



### Linux



#### 1. Install uv

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

Or via your package manager — see the [uv installation guide](https://docs.astral.sh/uv/getting-started/installation/).

#### 2. Clone and enter the project

```bash
git clone <repository-url>
cd ml_lab_practicals_csp_dc_305
```



#### 3. Check CUDA version (optional, for GPU)

```bash
nvidia-smi
```



#### 4. Install PyTorch (GPU)


| CUDA version        | Command                                                                       |
| ------------------- | ----------------------------------------------------------------------------- |
| 13.x (cu132 wheels) | `uv add torch torchvision --index-url https://download.pytorch.org/whl/cu132` |
| 13.0                | `uv add torch torchvision --index-url https://download.pytorch.org/whl/cu130` |
| 12.6                | `uv add torch torchvision --index-url https://download.pytorch.org/whl/cu126` |


If you cloned an existing repo with a `uv.lock` file, sync instead:

```bash
uv sync
```



#### 5. Install remaining dependencies

```bash
uv add matplotlib seaborn pandas scikit-learn jupyterlab
```



#### 6. Run Jupyter Lab

```bash
uv run jupyter lab
```



### macOS



#### 1. Install uv

Using Homebrew:

```bash
brew install uv
```

Or using the install script:

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```



#### 2. Clone and enter the project

```bash
git clone <repository-url>
cd ml_lab_practicals_csp_dc_305
```



#### 3. Install dependencies

On Apple Silicon, PyTorch installs CPU or MPS-enabled wheels from PyPI automatically:

```bash
uv sync
```

Or add packages individually:

```bash
uv add torch torchvision
uv add matplotlib seaborn pandas scikit-learn jupyterlab
```



#### 4. Run Jupyter Lab

```bash
uv run jupyter lab
```



### Quick start (download ZIP)

If you prefer not to use Git, you can set up the project from a ZIP download:

1. **Download** the repository as a ZIP file from GitHub (**Code → Download ZIP**).
2. **Unzip** the archive to a folder on your machine.
3. **Open a terminal** and change into the project folder:
  ```bash
   cd ml_lab_practicals_csp_dc_305
  ```
   On Windows PowerShell, use the path where you extracted the folder, for example:
4. **Check whether** `uv` **is installed:**
  ```bash
   uv --version
  ```
  - If the command prints a version number, proceed to the next step.
  - If the command is not found, install `uv` for your platform using the steps in **Windows (Native)**, **Linux**, or **macOS** above, then return here.
5. **Install all project dependencies** with a single command:
  ```bash
   uv sync
  ```
   This creates the virtual environment, installs Python 3.14 (if needed), and sets up all packages listed in `pyproject.toml` and `uv.lock`.
6. **Start Jupyter Lab:**
  ```bash
   uv run jupyter lab
  ```
   Open a notebook from the **Practicals** table above.

> **GPU users:** If you need a CUDA-specific PyTorch build and `uv sync` does not pick up the right wheels, see the PyTorch install steps under your platform section above.



## License

This project is licensed under the MIT License, see [LICENSE](LICENSE) for details.