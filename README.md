# Faculty_Student_Research_Matching_System

A Python-based recommendation prototype that ranks faculty matches for prospective students using research interests, academic background, program goals, and faculty publication text.

The project demonstrates an explainable matching workflow for graduate recruitment and faculty–student research alignment. It is a decision-support prototype, not an automated admissions or advisor-assignment system.

## Features

- Validates student and faculty data for missing values, duplicate rows, duplicate IDs, and empty required fields.
- Cleans and standardizes text fields for analysis.
- Uses TF-IDF vectorization, phrase matching, and cosine similarity.
- Matches students and faculty using research interests, academic background, program goals, and publication information.
- Generates top-three faculty recommendations for each student.
- Provides research, academic, goal, publication, and final weighted match scores.
- Creates a student–faculty similarity heatmap.
- Exports recommendations to CSV.

## Technologies

Python, pandas, NumPy, scikit-learn, Matplotlib, and Jupyter Notebook.

## Matching Method

The system calculates four similarity components and combines them into a final weighted score:

| Component | Weight |
|---|---:|
| Research interests | 55% |
| Academic background | 15% |
| Program goals | 15% |
| Faculty publications | 15% |

Research interests receive the highest weight because direct research alignment is the primary matching criterion.

## Example Output

The system produces ranked and explainable recommendations:

| Student | Rank | Recommended Faculty | Final Score |
|---|---:|---|---:|
| Alice Johnson | 1 | Dr. Sarah Miller | 0.68 |
| Alice Johnson | 2 | Dr. Robert Taylor | 0.17 |
| Alice Johnson | 3 | Dr. James Wilson | 0.08 |

It also produces a final weighted student–faculty match-score heatmap.

![Final Student-Faculty Matching Heatmap](images/final_match_heatmap.png)

## Installation

```bash
git clone https://github.com/srisaichetanareddyj/Faculty-Student-Research-Matching-System.git
cd Faculty-Student-Research-Matching-System
pip install pandas numpy matplotlib scikit-learn jupyter
```

## Run the Project

```bash
jupyter notebook
```

Open `"Faculty_Student_Research_Matching_System.ipynb"` and run all cells from top to bottom.

## Output

The notebook generates:

- Top-three explainable faculty recommendations for each student.
- A final student–faculty match-score heatmap.
- `student_faculty_recommendations.csv`.

## Limitations and Future Work

The current project uses a small synthetic dataset and manually selected matching weights. It should support—not replace—human decisions by faculty and graduate-program staff.

Future work includes using approved real-world data, incorporating faculty availability and program constraints, collecting expert feedback, and evaluating recommendation quality with metrics such as Precision@K, Recall@K, and NDCG@K.

## Author

**Sri Sai Chetana Reddy**  
MS in Computer Science, Arizona State University  
[GitHub](https://github.com/srisaichetanareddyj) · [LinkedIn](https://www.linkedin.com/in/sri-sai-chetana-j)

## License

This project is intended for educational and portfolio purposes.
