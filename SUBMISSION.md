# Submission Manifest — Project 2

Fill this in before submitting. The grading agent reads it first.

## Student
- Zachary Shrader (zjs5329)

## Course level
- [ ] 520 (undergraduate)
- [X] 620 (graduate)

## Dataset
- Name / source / version / URL:
- How to obtain it (command or steps):
- Label column (used for EVALUATION ONLY):
- Subsample size and how you chose it:

## How to reproduce
```bash
make setup
# Download the course Drive archive and extract data/UNSW_NB15_training-set.csv
# See data/README.md; make data is an optional mirror fallback / checksum check.
make reproduce
```
Anything non-default the grader must know (data download, runtime):

## Your implementation
- Confirm `config.yaml` has `kmeans.implementation: scratch`: [X]
- Initialization used (`random` / `kmeans++`): kmeans++
- Empty clusters are handled by keeping the centroid where it is. This is a simplicity tradeoff for removing it from being in the system.
- Convergence criterion and tolerance: The convergence criterion is if the label vectors are the same, declared on line 194 of kmeans.py
- Agreement with the reference (each run’s `reference_check` in metrics.json; same geometry):
  - Euclidean `inertia_ratio` / `ari_vs_reference`:
  - Mahalanobis `inertia_ratio` / `ari_vs_reference`:

## Choosing k
- k you report, and the evidence (elbow / silhouette): 24, Silhouette
- If the best silhouette k differs from the number of true classes, explain: 
  There are only ten classes, so we exceed even double the number of classes. This was done as I scaled up the possible values for K to find a better result. This does make some sense as it is seperating similar traffic into different classes, which helps with seperating similar attacks.

## Claimed results (must match `results/metrics.json`)
| Metric | Euclidean | Mahalanobis |
|---|---|---|
| Silhouette (common Euclidean) |0.4396829390685107,|0.4396829390685107|
| Silhouette (configured geometry) |0.4396829390685107|0.4396829390685107|
| V-measure |0.3659883038177016|0.3659883038177016|
| Accuracy |0.4134048257372654|0.4134048257372654|
| Macro F1 |0.3879852206222294|0.3879852206222294|

- Primary comparison criterion declared before weight experiments: The REsults are exactly the same
- The diagonal C you chose, its feature order, and why: I kept a base C, as I have no information to create a better diagonal C
- Same sample, k, seed and restart budget across the primary runs: [ ]
- Tradeoffs and whether any independent validation was used: No independed validation ws used, I traded a bit of time for a lower K value. 

## AI-use acknowledgment
As I am unfamilliar with Numpy, Cluade opus 5.5 was used as a programming assitance tool for dcumentation reserch and learning the system. All code snippets given were reviewed, fact checked, and self-written on the assignment.
