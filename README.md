# Comparative Analysis of Sorting Algorithms for Olympic Medal Ranking

A Python-based performance study comparing TimSort, QuickSort, and 
BubbleSort for ranking 91 countries from the Paris 2024 Olympic Games 
using a weighted medal scoring system.

This project was submitted as an academic assignment at Birmingham City 
University (Faculty of Computing, Engineering and the Built Environment).

---

## Project Overview

This study evaluates three sorting algorithms by applying them to a 
real-world sports dataset. Each algorithm ranks all 91 medal-winning 
countries in descending order using the following weighted formula:

    Weighted Score = (Gold x 3) + (Silver x 2) + (Bronze x 1)

The project also includes a linear search function for country-by-country 
lookup and comparison, and an interactive menu for viewing top-K countries 
and comparing two countries head-to-head.

---

## Algorithms Implemented

### Sorting Algorithms

| Algorithm  | Best Case  | Average Case | Worst Case  | Space    | Stable |
|------------|------------|--------------|-------------|----------|--------|
| TimSort    | O(n)       | O(n log n)   | O(n log n)  | O(n)     | Yes    |
| QuickSort  | O(n log n) | O(n log n)   | O(n^2)      | O(log n) | No     |
| BubbleSort | O(n)       | O(n^2)       | O(n^2)      | O(1)     | Yes    |

### TimSort (Solution-1)
A custom hybrid implementation combining InsertionSort on small runs 
(< MIN_MERGE = 32 elements) and MergeSort on larger segments. Minimum 
run size is calculated dynamically. Most efficient for this dataset.

### QuickSort (Solution-2)
A custom recursive divide-and-conquer implementation using the last 
element as pivot. Partitions by weighted score (index 4) in descending 
order. In-place sorting with O(log n) average space.

### BubbleSort (Solution-3)
An optimized comparison-based implementation with an early termination 
flag - stops immediately if no swaps occur in a pass, improving 
best-case performance to O(n). Simpler but less scalable.

### Search Algorithm
Linear Search - used for case-insensitive country lookup in the 
compare_countries() and display_top() functions.

---

## Data Structure Used

- Tuple (name, gold, silver, bronze, weighted_score) - immutable, 
  low overhead, fast positional access. Ensures original medal data is 
  never accidentally modified.
- List of Tuples - mutable container holding all 91 country records, 
  allowing in-place reordering by each sorting algorithm.

---

## Results

### Empirical Performance (Actual Timing Output)

| Algorithm  | Time Taken        |
|------------|-------------------|
| TimSort    | 0.000025 seconds  |
| BubbleSort | 0.000103 seconds  |
| QuickSort  | 0.000149 seconds  |

Key finding: TimSort was fastest. Surprisingly, BubbleSort outperformed 
QuickSort on this 91-country dataset because QuickSort's recursive overhead 
and partitioning complexity outweighed its theoretical advantages at this 
small scale.

### Top 5 Countries (All Three Algorithms Agree)

| Rank | Country       | Gold | Silver | Bronze | Weighted Score |
|------|---------------|------|--------|--------|----------------|
| 1    | United States | 40   | 44     | 42     | 250            |
| 2    | China         | 40   | 27     | 24     | 198            |
| 3    | France        | 16   | 26     | 22     | 122            |
| 4    | Great Britain | 14   | 22     | 29     | 115            |
| 5    | Australia     | 18   | 19     | 16     | 108            |

---

## Dataset

- Source: Olympics 2024 Medal Tally by Country - Kaggle
  https://www.kaggle.com/datasets/berkayalan/paris-2024-olympics-medals
- File: olympics2024.csv
- Fields used: Country, Gold, Silver, Bronze
- Fields excluded: Rank, Country Code, Total (not needed for weighted scoring)
- Size: 91 countries (all medal-winning nations at Paris 2024)

---

## Project Structure

    paris-2024-olympics-sorting-analysis/
    ├── olympic_medal_sorting_analysis.ipynb   # Main notebook
    ├── olympics2024.csv                        # Dataset
    ├── report.pdf                              # Academic report
    ├── LICENSE                                 # MIT License
    └── README.md

---

## Interactive Features

The notebook includes a menu-driven interface with three options:

    ==== Olympics 2024 Ranking Based on Weighted Score ====
    1. View Top K Countries
    2. Compare Two Countries
    3. Exit

- Option 1 - Enter any number K (1-91) to display the top K ranked countries
- Option 2 - Enter two country names to compare their weighted scores head-to-head
- Option 3 - Exit the program

---

## How to Run

### Prerequisites
- Python 3.x
- Jupyter Notebook or Google Colab

### Steps

1. Clone the repository:

       git clone https://github.com/Utu8848/paris-2024-olympics-sorting-analysis
       cd paris-2024-olympics-sorting-analysis

2. Make sure olympics2024.csv is in the same directory as the notebook.

3. Open the notebook:

       jupyter notebook olympic_medal_sorting_analysis.ipynb

4. Run all cells in order. The final cells run the interactive menu 
   and the benchmarking comparison.

---

## Author

Utsav Rai
Faculty of Computing, Engineering and the Built Environment
Birmingham City University, Birmingham, United Kingdom
GitHub: https://github.com/Utu8848

---

## License

This project is licensed under the MIT License. See the LICENSE file for details.

---

## Acknowledgements

Dataset sourced from Kaggle:
Olympics 2024 Medals by Berkay Alan
https://www.kaggle.com/datasets/berkayalan/paris-2024-olympics-medals

Full code also available as a GitHub Gist:
https://gist.github.com/Utu8848/f58bfbdf2152ea81cd9dfa0d7b6b9bb2
