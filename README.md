# What drives house prices in Melbourne?

Project 1 for BZAN 6351 (University of Houston, Fall 2026), by Duc (Bill) Le.

A real estate agency sets a price guide for each new listing. This project asks two things: which features and locations drive the sale price, and whether a model built only on facts known at listing time can back up that guide.

The full write-up, with charts and a price guide tool you can try, is on my portfolio:
https://ducle26.github.io/bill-portfolio/projects/melbourne-housing.html

## What I found

- Location and property type do most of the work. Each extra kilometer from the city takes about 4% off the price, and a unit sells for about 39% less than a comparable house.
- Rooms and bathrooms add value. Parking and extra land add little once location is set.
- A random forest was the most accurate of three models. On sales it had never seen, it landed within 20% of the real price for two homes out of three.

| Model | R² | RMSE | MAE | MAPE |
|---|---|---|---|---|
| Linear regression | 0.648 | $358,884 | $236,841 | 23.9% |
| Decision tree | 0.557 | $402,454 | $269,201 | 26.9% |
| Random forest | 0.756 | $298,479 | $184,310 | 17.8% |

Scores are on a 20% test set of 2,977 sales, with prices in Australian dollars.

## Files

| File | What it is |
|---|---|
| `Project1_Melbourne_Housing.Rmd` | The R Markdown file: cleaning, exploration, three models, and recommendations |
| `Melbourne_Data.csv` | The data: 18,396 sales from January 2016 to September 2017 |

## Run it

1. Download this folder and open `Project1_Melbourne_Housing.Rmd` in RStudio. Keep the CSV in the same folder.
2. Install the packages once:

   ```r
   install.packages(c("dplyr", "tidyr", "ggplot2", "scales", "rpart", "rpart.plot",
                      "randomForest", "car", "corrplot", "knitr"))
   ```

3. Press Knit. The random forest takes about half a minute.

The file sets a seed, so the numbers above come out the same each run.

## Data

Becker, D. (2018). *Melbourne Housing Snapshot* [Data set]. Scraped by T. Pino from public listings on Domain.com.au. Kaggle. https://www.kaggle.com/datasets/dansbecker/melbourne-housing-snapshot

The data belongs to its publishers. See the Kaggle page for its license.
