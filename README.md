# Penguin Species Classification: Flipper Length vs. Body Mass
**Authors:** Yuxue Zhu, Maxine Paredes, Hephzibah Adeniji, Abhishek Sharma

## About

In this project, we ask whether flipper length or body mass more accurately classifies penguin species (Adélie, Chinstrap or Gentoo). Using the Palmer Penguins data set (Horst et al., 2020), we built two logistic regression classifiers, each using a single body measurement. On an unseen test set, the flipper length model outperformed the body mass model on every metric (accuracy 0.837 vs. 0.744; macro F1-score 0.715 vs. 0.561). Both models identified Gentoo penguins well but often confused the similarly sized Adélie and Chinstrap penguins. This suggests that a stable structural trait like flipper length captures species differences better than body mass, which varies with a penguin's condition, but that neither measurement alone is enough to reliably distinguish all three species.

## Report

The final report can be found [here]([GitHub Pages URL]) (HTML), or as a [PDF](analysis/penguin-species-classification.pdf).

## Usage

First time running the project, install [uv](https://docs.astral.sh/uv/getting-started/installation/) and [Quarto](https://quarto.org/docs/get-started/), then clone this repository and move into it:

```bash
git clone https://github.com/UBC-MDS-2026-27/DSCI-522-Palmer-Penguin-Analysis.git
cd DSCI-522-Palmer-Penguin-Analysis
```

Then run the following from the root of this repository to create the virtual environment:

```bash
uv sync
```

To run the analysis and render the report, run the following from the root of this repository:

```bash
uv run quarto render
```

Rendering runs the whole analysis from scratch: it downloads the Palmer Penguins data again from the `palmerpenguins` repository (so you need an internet connection), and overwrites the files in `data/raw/` and `data/processed/`. The rendered report is written to `analysis/penguin-species-classification.html` and `analysis/penguin-species-classification.pdf`, replacing the versions in this repository.

## Dependencies

- [uv](https://docs.astral.sh/uv/) (version 0.12 or higher)
- [Quarto](https://quarto.org/docs/get-started/) (version 1.10 or higher)
- Python and packages listed in [`pyproject.toml`](pyproject.toml) (exact
  versions are locked in [`uv.lock`](uv.lock))

  ## AI use statement

We used Anthropic's [Claude](https://claude.ai) (Opus 5.5) to help edit the wording of report sections, interpret model evaluation metrics, and troubleshoot Git, uv and Quarto errors. All AI-generated suggestions were reviewed, tested and edited by the authors, who take full responsibility for the content of this repository.

Example prompts:

- "Can you give me an outline for how to write an introduction for the Palmer Penguins data set?"
- "What metric should we use for classification evaluation, and why?"
- "I'm running `git fetch --all` but I don't see my partner's branch. Why could this be?"

  ## License

The Penguin Species Classification report contained herein is licensed under the [LICENSE NAME, e.g. Attribution-NonCommercial-ShareAlike 4.0 International (CC BY-NC-SA 4.0) License](LICENSE.md). See [the license file](LICENSE.md) for more information. If re-using/re-mixing please provide attribution and link to this webpage. The software code contained within this repository is licensed under the [MIT] license. See [the license file](LICENSE.md) for more information.

The Palmer Penguins data set used in this project is released under the [CC0 1.0 Universal](https://allisonhorst.github.io/palmerpenguins/LICENSE.html) public domain dedication by its creators, Allison Horst, Alison Hill and Kristen Gorman (Horst, Hill, and Gorman 2020).