# TOPSIS-Harshit-102303276

A Python package to implement the **Technique for Order of Preference by Similarity to Ideal Solution (TOPSIS)**. This command-line tool takes a dataset of alternatives and criteria, applies weights and impacts, and calculates a ranking score for each alternative.

[Web Demo](topsis-zzre.vercel.app)

[PyPI Package](pypi.org/project/topsis-harshit-102303276)


## Installation

You can install the package using `pip` with the following command:

```bash
pip install topsis-harshit-102303276
```

## How to Use

This tool is designed to be run from the command line. You need to provide an input CSV or Excel file with your dataset, along with a list of weights, a list of impacts, and the name of the output file where results will be stored.

### Command Format

```bash
topsis <InputDataFile> <Weights> <Impacts> <ResultFileName>
```

### Parameters

1. **InputDataFile**: The path to the `.csv` or `.xlsx` file.

   * The file should have **at least 3 columns**.
   * The **first column** should contain the object or model names (e.g., M1, M2, M3). This column is kept in the output but not used for calculations.
   * The **remaining columns** must contain numeric values representing the criteria.

2. **Weights**: A comma-separated list of numbers showing the relative importance of each criterion (for example, `"1,1,1,1"`).

3. **Impacts**: A comma-separated list of symbols (`+` or `-`) specifying whether a higher or lower value is preferred for each criterion.

   * `+` means higher is better (benefit).
   * `-` means lower is better (cost).

4. **ResultFileName**: The name of the CSV file where the output will be saved.

## Example

Suppose we want to rank 5 mobile phone models using 4 criteria: **Price**, **Storage**, **Camera**, and **Looks**.

### 1. Input File (`data.csv`)

| Model | Price | Storage | Camera | Looks |
| ----- | ----- | ------- | ------ | ----- |
| M1    | 250   | 16      | 12     | 5     |
| M2    | 200   | 16      | 8      | 3     |
| M3    | 300   | 32      | 16     | 4     |
| M4    | 275   | 32      | 8      | 4     |
| M5    | 225   | 16      | 16     | 2     |

* **Interpretation of criteria**:
* **Price**: Lower value is preferred (`-`).
* **Storage**: Higher value is preferred (`+`).
* **Camera**: Higher value is preferred (`+`).
* **Looks**: Higher value is preferred (`+`).

### 2. Run the Command

Execute this in your terminal:

```bash
topsis data.csv "1,1,1,1" "-,+,+,+" result.csv
```

* **Weights**: `1,1,1,1` (all criteria have equal importance).
* **Impacts**: `-,+,+,+` (Price is a cost criterion, the rest are benefit criteria).

### 3. Output File (`result.csv`)

The program creates a file named `result.csv` that includes the original data along with two extra columns: **Topsis Score** and **Rank**.

| Model | Price | Storage | Camera | Looks | Topsis Score | Rank |
| ----- | ----- | ------- | ------ | ----- | ------------ | ---- |
| M1    | 250   | 16      | 12     | 5     | 0.534277     | 3    |
| M2    | 200   | 16      | 8      | 3     | 0.308368     | 5    |
| M3    | 300   | 32      | 16     | 4     | 0.691632     | 1    |
| M4    | 275   | 32      | 8      | 4     | 0.534737     | 2    |
| M5    | 225   | 16      | 16     | 2     | 0.492650     | 4    |
