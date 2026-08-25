# Graduate Student–Faculty Research Matching System

A Python-based recommendation prototype that matches prospective graduate students with faculty members based on research interests, academic background, program goals, and faculty publications.

## Project Overview

Graduate programs need effective ways to identify faculty members whose research aligns with prospective students’ interests and academic goals. This project creates an explainable student–faculty matching system that generates ranked faculty recommendations using text-based similarity analysis.

The system is designed as a decision-support prototype for graduate recruitment, admissions support, and faculty–student research alignment. It does not make admission or advising decisions automatically.

## Features

- Creates structured student and faculty profile datasets.
- Validates data for missing values, duplicate rows, duplicate IDs, and empty required fields.
- Cleans and standardizes text fields for consistent analysis.
- Matches students and faculty using:
  - Research interests
  - Academic background and faculty department
  - Graduate program goals and faculty focus areas
  - Faculty publication and scholarly-work text
- Uses TF-IDF vectorization with n-gram phrase matching.
- Calculates cosine similarity between student and faculty profiles.
- Combines multiple similarity scores into one weighted final match score.
- Produces top-three faculty recommendations for each student.
- Provides explainable component scores for every recommendation.
- Creates a final student–faculty match-score heatmap.
- Exports recommendations to a CSV file.

## Technologies Used

- Python
- pandas
- NumPy
- scikit-learn
- Matplotlib
- Jupyter Notebook

## Dataset

The current project uses a small synthetic dataset for demonstration purposes.

### Student profile fields

| Field | Description |
|---|---|
| `student_id` | Unique identifier for each prospective student |
| `name` | Student name |
| `academic_background` | Academic discipline or degree background |
| `research_interests` | Research topics of interest |
| `program_goals` | Graduate study, research, or career goals |

### Faculty profile fields

| Field | Description |
|---|---|
| `faculty_id` | Unique identifier for each faculty member |
| `name` | Faculty member name |
| `department` | Academic department |
| `research_interests` | Faculty research topics |
| `faculty_focus` | Faculty research focus area |
| `publications` | Sample scholarly publication or research-summary text |

## Matching Methodology

The system compares student and faculty text fields using **TF-IDF vectorization** and **cosine similarity**.

TF-IDF converts text into numerical feature vectors while emphasizing terms that are meaningful within the available profiles. The model uses n-gram matching to help recognize research phrases such as:

- Machine Learning
- Natural Language Processing
- Computer Vision
- Data Science
- Cloud Computing

Cosine similarity then measures how closely each student profile aligns with each faculty profile. A higher score indicates stronger text-based alignment.

### Final weighted score

The final student–faculty matching score combines four components:

| Matching Component | Weight |
|---|---:|
| Research-interest similarity | 55% |
| Academic-background similarity | 15% |
| Program-goal similarity | 15% |
| Faculty-publication similarity | 15% |

Research interests receive the highest weight because direct research alignment is the primary purpose of faculty matching. Academic background, program goals, and faculty publications provide additional context.

## Workflow

1. Create or load student and faculty datasets.
2. Validate missing values, duplicate rows, duplicate identifiers, and empty fields.
3. Clean text by removing unnecessary spaces and standardizing text format.
4. Standardize research-related terminology where appropriate.
5. Calculate research-interest similarity.
6. Calculate academic-background and department similarity.
7. Calculate student-goal and faculty-focus similarity.
8. Calculate student-interest and faculty-publication similarity.
9. Combine component scores using the weighted matching formula.
10. Rank the top three faculty recommendations for each student.
11. Generate explainable recommendations and visualizations.
12. Export results to CSV.

## Example Output

The system produces a ranked recommendation table with:

| Student | Rank | Recommended Faculty | Research Score | Academic Score | Goal Score | Publication Score | Final Score |
|---|---:|---|---:|---:|---:|---:|---:|
| Alice Johnson | 1 | Dr. Sarah Miller | 0.XXX | 1.000 | 0.XXX | 0.XXX | 0.XXX |
| Alice Johnson | 2 | Dr. Robert Taylor | 0.XXX | 0.000 | 0.XXX | 0.XXX | 0.XXX |
| Alice Johnson | 3 | Dr. James Wilson | 0.XXX | 0.000 | 0.XXX | 0.XXX | 0.XXX |

The project also generates a heatmap showing final weighted match scores for every student–faculty pair.

> Add a screenshot of your final heatmap here after uploading it to your repository.
>
> Example:
>
> `![Final Student-Faculty Matching Heatmap](images/final_match_heatmap.png)`

## Installation

Clone the repository:

```bash
git clone https://github.com/[your-github-username]/graduate-student-faculty-matching-system.git
cd graduate-student-faculty-matching-system
```

Install required libraries:

```bash
pip install pandas numpy matplotlib scikit-learn jupyter
```

## How to Run

Start Jupyter Notebook:

```bash
jupyter notebook
```

Open the project notebook and run all cells from top to bottom.

The notebook generates:

- Student and faculty data-validation results
- Individual similarity matrices
- Final weighted student–faculty similarity matrix
- Top-three explainable faculty recommendations
- Student–faculty matching heatmap
- `student_faculty_recommendations.csv`

## Output Files

| File | Description |
|---|---|
| `student_faculty_recommendations.csv` | Exported top-three faculty recommendations with component similarity scores |
| `student_faculty_matching.ipynb` | Main Jupyter Notebook containing data preparation, matching logic, visualization, and export workflow |
| `README.md` | Project documentation |

## Limitations

- The current dataset is synthetic and contains only five students and five faculty profiles.
- The recommendation scores represent text-based alignment, not validated admission or advisor-assignment decisions.
- The weighting scheme is manually selected and has not been validated using historical outcomes or stakeholder feedback.
- TF-IDF and cosine similarity may not fully recognize semantic relationships between related research topics.
- The prototype does not account for faculty availability, advising capacity, funding, lab capacity, or program-specific requirements.
- Recommendation quality depends on complete, accurate, and up-to-date student and faculty profile data.

## Ethical Considerations

This project is a decision-support prototype and should not be used as the sole basis for admissions decisions, faculty assignments, or student advising decisions.

- Human review by faculty and graduate-program staff should remain part of the final process.
- Sensitive personal information should not be included unless necessary, authorized, and securely protected.
- The system should be reviewed for possible bias caused by incomplete, unrepresentative, or historically biased data.
- A low match score does not represent a student’s ability, academic potential, or likelihood of success.
- Recommendations are made more transparent by reporting individual research, academic, goal, and publication component scores.

## Evaluation Plan

A future version should be evaluated using appropriately approved real data, faculty-reviewed relevance labels, or historical student–faculty matches.

Possible evaluation methods include:

- **Precision@K:** Measures how many of the top K faculty recommendations are relevant.
- **Recall@K:** Measures how many relevant faculty members appear in the top K recommendations.
- **NDCG@K:** Measures ranking quality, giving higher credit when highly relevant faculty appear near the top of the recommendation list.
- **Faculty feedback:** Faculty members review and rate the quality of recommended matches.
- **Graduate program staff feedback:** Program staff assess whether recommendations support recruitment and admissions workflows.
- **Human comparison:** Compare automated recommendations with manually selected student–faculty matches.
- **Weight sensitivity analysis:** Test how recommendation rankings change when the component weights are adjusted.
- **Fairness review:** Evaluate whether recommendations perform consistently across disciplines, academic backgrounds, and research areas.

## Future Improvements

- Use real faculty publication abstracts and research-lab descriptions.
- Include student statements of purpose, project portfolios, coursework, and research experience.
- Add faculty availability, advising capacity, funding, and program requirements as approved operational constraints.
- Build a Streamlit dashboard for interactive recommendations and filtering.
- Compare TF-IDF with semantic embeddings or transformer-based language models.
- Add expert-labeled evaluation data and calculate Precision@K, Recall@K, and NDCG@K.
- Add fairness and bias-monitoring procedures.
- Connect the project to CSV files, databases, or APIs rather than manually created dictionaries.

## Author

**[Your Name]**  
[Your Program or Major]  
Arizona State University  
GitHub: [https://github.com/your-github-username](https://github.com/your-github-username)  
LinkedIn: [https://www.linkedin.com/in/your-linkedin-profile](https://www.linkedin.com/in/your-linkedin-profile)

## License

This project is intended for educational and portfolio purposes.

You may add an MIT License if you would like others to be able to reuse and modify this project.
