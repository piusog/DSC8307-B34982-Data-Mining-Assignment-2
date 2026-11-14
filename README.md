# DSC8307 Advent 2026 Assignment 2 — B34982

Two reproducible Jupyter projects for the Uganda Christian University MSc Data Science and Analytics assignment.

## Contents
- `project_1_wholesale_customers.ipynb`: exploratory analysis, cluster tendency, K-Means/Ward/DBSCAN comparison, segment profiling and recommendations.
- `project_2_credit_card_fraud.ipynb`: temporal anomaly-ranking evaluation, robust outlier baseline, MiniBatchKMeans, One-Class SVM, Isolation Forest, AP/ROC/Precision@K/Recall@K/lift and bootstrap uncertainty.
- `requirements.txt`: Python dependencies.
- `wholesale-customers.csv` and `creditcard.csv`: supplied original datasets; see source README files.

## Run (Python 3.11+ recommended)
```bash
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate
python -m pip install -r requirements.txt
jupyter lab
```
Run both notebooks in filename order using **Run All**, or validate from the repository root:
```bash
jupyter nbconvert --to notebook --execute project_1_wholesale_customers.ipynb --output project_1_executed.ipynb --ExecutePreprocessor.timeout=1800
jupyter nbconvert --to notebook --execute project_2_credit_card_fraud.ipynb --output project_2_executed.ipynb --ExecutePreprocessor.timeout=1800
```
Execution time varies with CPU and memory. The fraud file is ~144 MB; allow sufficient RAM and several minutes for one-class SVM and bootstrap evaluation. Run from the repository root so relative CSV paths resolve. Outputs may differ slightly across compatible dependency versions.

## Source and methodology notes
The assignment PDF and accompanying dataset README files were supplied with this project. The credit-card data contain sensitive *transaction patterns* but no direct personal identifiers in the supplied features. Fraud labels are withheld from anomaly-model training; reported test metrics are for evaluation only. Model choice after inspecting test outcomes would require a new prospective test.

## GitHub and Moodle
1. Create a public GitHub repository, e.g. `DSC8307_B34982_Assignment2`.
2. Upload the two notebooks, requirements, README and dataset documentation. The 144 MB `creditcard.csv` exceeds GitHub's standard 100 MB file limit: use **Git LFS** (`git lfs track 'creditcard.csv'`) if supported, or omit the CSV and provide a reliable download link and checksum in this README. Avoid uploading the CSV via normal Git.
3. Verify a fresh clone and install executes both notebooks, and that any LFS files download correctly.
4. Submit the public repository URL on Moodle, per assignment instructions. No repository has been created or submitted automatically.

### Git LFS example
```bash
git lfs install
git lfs track 'creditcard.csv'
git add .gitattributes *.ipynb *.csv *.txt requirements.txt README.md
git commit -m 'Add reproducible DSC8307 assignment projects'
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/DSC8307_B34982_Assignment2.git
git push -u origin main
```
GitHub LFS storage and bandwidth quotas apply. Review UCU academic integrity and data-sharing rules before publication.

## Final execution and review record (14 November 2026)
- Both notebooks were executed sequentially with `nbclient` in the available Python environment, without cell errors.
- The saved notebooks include **9 embedded PNG figures** (Project 1) and **7 embedded PNG figures** (Project 2), plus numerical outputs.
- Added an eligible-method comparison and 80% subsample stability description for customer clustering; corrected the earlier erroneous feature-perturbation wording.
- Added label-free calibration-period score-ranking sensitivity for MiniBatchKMeans and One-Class SVM, and a review-capacity error-count table for fraud detection.
- The two-cluster raw-versus-log K-Means adjusted Rand index was 0.081, indicating important preprocessing sensitivity; the reported customer groups are exploratory.
- Execution in a newly provisioned virtual environment was **not** independently verified. A successful run in the current environment is not a guarantee of identical behavior on other systems.
- Saved results are observational and do not guarantee any grade or fraud detection performance in deployment.

## Enhanced methodological audit (14 November 2026)
- Re-executed both notebooks after adding log+robust, log+standard and raw+standard preprocessing comparisons, plus 30 repeated 80% customer subsamples and relative median segment profiles.
- Added capacity curves at 50, 100, 250, 500, 1,000 and 2,000 reviews, and chronological test-quartile AP alongside prevalence and fraud counts.
- Added limitations and literature references, emphasizing label-free calibration, historical data limitations, temporal dependence and operational decision costs.
- Execution verified in the available environment with nbclient (zero errors); **a newly created isolated environment has not been independently tested**.
- Academic assessment has a maximum of 100%, and no score is guaranteed.

## Final expanded audit and validation (14 November 2026)
- **Project 1:** 30-seed observed Hopkins versus 30 bounding-box uniform null replicates; preprocessing ARI matrix; 40 repeated 80% refits with label matching and customer-level assignment agreement; quantified segment-median category ratios and conditional controlled-pilot actions. The uniform null is a reference diagnostic, not a formal hypothesis test.
- **Project 2:** earlier expanding-window chronological stress tests for the robust-z, MiniBatchKMeans and Isolation Forest methods; explicit hypothetical cost sensitivity (arbitrary units); moving-block bootstrap sensitivity for AP and Recall@500. The historical final holdout was already inspected, so these analyses are exploratory rather than independent confirmation. One-Class SVM remains evaluated in the primary held-out comparison but is not included in the additional rolling-window refits due to computational cost.
- Both notebooks were **re-executed from top to bottom in the available environment** with zero errors and all outputs saved. `VALIDATION.json` records executable-cell counts, figure counts, and SHA-256 checksums of original datasets. `requirements-lock.txt` records versions from the successful environment; `requirements.txt` remains the more portable dependency specification.
- **No clean-environment install or independent GitHub clone has been performed.** This is a reproducibility limitation, not a claim of validation.
- The source datasets and the source README files are included. For GitHub, `creditcard.csv` requires Git LFS or a documented external source plus checksum.
