# TOPSIS-Python

[![PyPI version](https://badge.fury.io/py/topsis-python.svg)](https://pypi.org/project/topsis-python/)

**TOPSIS-Python** is a Python package for performing the TOPSIS (Technique for Order of Preference by Similarity to Ideal Solution) evaluation method, a popular multi-criteria decision-making (MCDM) technique. This package simplifies the process of ranking alternatives based on multiple criteria by identifying the option closest to the ideal solution and farthest from the nadir solution.

---

## Installation

You can install the package directly from PyPI using pip:

```bash
pip install Topsis-SaiVarsha-102217040==1.0.1
```

---

## Usage

To use the package, you need a dataset containing alternatives (rows) and their criteria (columns), along with the weights and beneficial/non-beneficial indicators for the criteria.

### Command-Line Interface

After installation, the package provides a CLI for quick use:

```bash
topsis --input input_file.csv --weights 1,2,3,4 --impacts +,+,-,+ --output output_file.csv
```

### Python API

You can also use the package programmatically:

```python
from topsis import topsis_evaluate

# Example data
data = [
    [250, 16, 12, 5],
    [200, 16, 8, 3],
    [300, 32, 16, 4],
    [275, 32, 8, 4],
    [225, 16, 16, 2]
]
weights = [0.25, 0.25, 0.25, 0.25]
impacts = ['+', '+', '-', '+']

# Perform TOPSIS
rankings = topsis_evaluate(data, weights, impacts)
print(rankings)
```

---

## Example

### Input File

The input file should be a CSV file containing the following structure:

| Fund Name | P1   | P2   | P3  | P4   | P5   |
|-----------|-------|-------|------|-------|-------|
| M1        | 0.84  | 0.71  | 6.7  | 42.1  | 12.59 |
| M2        | 0.91  | 0.83  | 7    | 31.7  | 10.11 |
| M3        | 0.79  | 0.62  | 4.8  | 46.7  | 13.23 |
| M4        | 0.78  | 0.61  | 6.4  | 42.4  | 12.55 |
| M5        | 0.94  | 0.88  | 3.6  | 62.2  | 16.91 |
| M6        | 0.88  | 0.77  | 6.5  | 51.5  | 14.91 |
| M7        | 0.66  | 0.44  | 5.3  | 48.9  | 13.83 |
| M8        | 0.93  | 0.86  | 3.4  | 37    | 10.55 |

### Python API Example

```python
from topsis import topsis_evaluate

# Example dataset
data = [
    [0.84, 0.71, 6.7, 42.1, 12.59],
    [0.91, 0.83, 7, 31.7, 10.11],
    [0.79, 0.62, 4.8, 46.7, 13.23],
    [0.78, 0.61, 6.4, 42.4, 12.55],
    [0.94, 0.88, 3.6, 62.2, 16.91],
    [0.88, 0.77, 6.5, 51.5, 14.91],
    [0.66, 0.44, 5.3, 48.9, 13.83],
    [0.93, 0.86, 3.4, 37, 10.55]
]
weights = [0.25, 0.25, 0.25, 0.25, 0.25]
impacts = ['+', '+', '-', '+', '+']

# Perform TOPSIS
rankings = topsis_evaluate(data, weights, impacts)
print("Rankings:", rankings)
```

### Output File

The output file will append two columns to the original dataset:
- **Performance Score**
- **Rank**

| Fund Name | P1   | P2   | P3  | P4   | P5   | Performance Score | Rank |
|-----------|-------|-------|------|-------|-------|-------------------|------|
| M1        | 0.84  | 0.71  | 6.7  | 42.1  | 12.59 | 0.5346            | 3    |
| M2        | 0.91  | 0.83  | 7    | 31.7  | 10.11 | 0.3084            | 5    |
| M3        | 0.79  | 0.62  | 4.8  | 46.7  | 13.23 | 0.6912            | 1    |
| M4        | 0.78  | 0.61  | 6.4  | 42.4  | 12.55 | 0.5346            | 2    |
| M5        | 0.94  | 0.88  | 3.6  | 62.2  | 16.91 | 0.4038            | 4    |
| M6        | 0.88  | 0.77  | 6.5  | 51.5  | 14.91 | 0.4912            | 6    |
| M7        | 0.66  | 0.44  | 5.3  | 48.9  | 13.83 | 0.4238            | 7    |
| M8        | 0.93  | 0.86  | 3.4  | 37    | 10.55 | 0.3756            | 8    |

---

## Input Format

- **CSV File**:
  - First row: Criteria names.
  - First column: Alternative names.
  - Remaining cells: Criteria values for each alternative.
- **Weights**:
  - A list of non-negative values representing the importance of each criterion.
- **Impacts**:
  - A list of `+` or `-` for each criterion indicating whether it is beneficial or non-beneficial.

---

## Output Format

The output is a ranked list of alternatives based on their closeness to the ideal solution. The results include:

1. **Performance Score**: Closeness of each alternative to the ideal solution.
2. **Rank**: Rank of each alternative based on the performance score.

---

## License

This project is licensed under the MIT License.

---

