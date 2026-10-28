# Predicting Barbell Lift Quality

Practical Machine Learning course project using accelerometer data to predict exercise quality (`classe`, A–E).

The compiled report is available as [HTML](index.html). The R Markdown source, model script, and quiz predictions are included in this repository.

## Reproduce the analysis

Install R and the required packages:

```r
install.packages(c("randomForest", "knitr"))
```

Download the course data into a `data` directory:

```r
dir.create("data", showWarnings = FALSE)
download.file("https://d396qusza40orc.cloudfront.net/predmachlearn/pml-training.csv",
              "data/pml-training.csv", mode = "wb")
download.file("https://d396qusza40orc.cloudfront.net/predmachlearn/pml-testing.csv",
              "data/pml-testing.csv", mode = "wb")
```

From the repository root, run:

```sh
Rscript analysis.R
Rscript -e 'knitr::knit("model_report.Rmd", output="model_report.html")'
```

The script performs stratified five-fold cross-validation, fits the final random forest, and writes quiz predictions for the 20 test cases. The compiled report records the validation results and expected out-of-sample error. The predictions are provided in `quiz_predictions.txt` (one answer per line) and `quiz_predictions.csv`.

To publish the report with GitHub Pages, select **Deploy from a branch**, choose `main` and `/(root)` in the repository's Pages settings. The `index.html` file is the report homepage.

## Data source

Groupware at PUC-Rio, Weight Lifting Exercise Dataset: [project dataset page](http://web.archive.org/web/20161224072740/http:/groupware.les.inf.puc-rio.br/harsvg). The dataset was generously made available for this course assignment.
