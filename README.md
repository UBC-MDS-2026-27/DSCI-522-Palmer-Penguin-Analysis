# Penguin Species Classification: Flipper Length vs. Body Mass
**Authors:** Yuxue (Jade) Zhu, Maxine Paredes, Hephzibah Adeniji, Abhishek Sharma

## About

In this project, we ask whether flipper length or body mass more accurately classifies penguin species (Adélie, Chinstrap or Gentoo). Using the Palmer Penguins data set (Horst et al., 2020), we built two logistic regression classifiers, each using a single body measurement. On an unseen test set, the flipper length model outperformed the body mass model on every metric (accuracy 0.837 vs. 0.744; macro F1-score 0.715 vs. 0.561). Both models identified Gentoo penguins well but often confused the similarly sized Adélie and Chinstrap penguins. This suggests that a stable structural trait like flipper length captures species differences better than body mass, which varies with a penguin's condition, but that neither measurement alone is enough to reliably distinguish all three species.

## Report

The final rendered report is available online on [GitHub Pages](https://ubc-mds-2026-27.github.io/DSCI-522-Palmer-Penguin-Analysis/), and a static PDF version can also be viewed directly in this repository at [`analysis/penguin-species-classification.pdf`](analysis/penguin-species-classification.pdf).

## Usage

First, make an SSH key if you do not already have one by running `ssh-keygen -t ed25519` and pressing Enter at each question, because without it Docker creates a folder named `~/.ssh/id_ed25519.pub` and SSH into the container fails until you delete that folder and make the key. Next, install [Docker Desktop](https://www.docker.com/products/docker-desktop/), clone this repository, and move into it:


```bash
git clone https://github.com/UBC-MDS-2026-27/DSCI-522-Palmer-Penguin-Analysis.git
cd DSCI-522-Palmer-Penguin-Analysis
```

Download the pre-built container image from Docker Hub:

```bash
docker compose pull
```

Render the report in the container (which runs the full analysis from scratch, downloads the Palmer Penguins dataset over the internet, overwrites `data/raw/` and `data/processed/`, and updates `analysis/penguin-species-classification.html` and `analysis/penguin-species-classification.pdf`):

```bash
docker compose run --rm analysis-env uv run quarto render
```

Because `--rm` is included, the container is removed by itself when the render finishes (if you also use `docker compose up -d`, run `docker compose down` to stop and remove it). Anyone who wants to change the project should follow the instructions in [`CONTRIBUTING.md`](CONTRIBUTING.md).

## Dependencies

All software dependencies are packaged inside the Docker image defined by Dockerfile and docker-compose.yml, which pins exact package versions using pyproject.toml, uv.lock, and renv.lock. To reproduce the analysis locally, you only need Docker Desktop and an active internet connection.

## AI use statement

We used Anthropic's [Claude](https://claude.ai) (Opus 5.5) to help edit the wording of report sections, interpret model evaluation metrics, and troubleshoot Git, uv and Quarto errors. All AI-generated suggestions were reviewed, tested and edited by the authors, who take full responsibility for the content of this repository.

Example prompts:

- "Can you give me an outline for how to write an introduction for the Palmer Penguins data set?"
- "What metric should we use for classification evaluation, and why?"
- "I'm running `git fetch --all` but I don't see my partner's branch. Why could this be?"

## License

The Penguin Species Classification report contained herein is licensed under the [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International (CC BY-NC-SA 4.0) License](LICENSE.md). See [the license file](LICENSE.md) for more information. If re-using/re-mixing please provide attribution and link to this webpage. The software code contained within this repository is licensed under the [MIT](LICENSE.md) license. See [the license file](LICENSE.md) for more information.

The Palmer Penguins data set used in this project is released under the [CC0 1.0 Universal](https://allisonhorst.github.io/palmerpenguins/LICENSE.html) public domain dedication by its creators, Allison Horst, Alison Hill and Kristen Gorman (Horst, Hill, and Gorman 2020).

## References

Bels, V., Le Floch, G., Kirchhoff, F., Rivain, M., Leroy, L., Vallianos, N., Comis, C., Pelle, E., Pfyffer, J., Agnew, P., & Davenport, J. (2026). Terrestrial Locomotion in Extant Marine Tetrapods with Flippers. Biology, 15(20), 1890. https://doi.org/10.3390/biology15201890

Chappell, M. A., Janes, D. N., Shoemaker, V. H., Bucher, T. L., & Maloney, S. K. (1993). Reproductive effort in Adélie penguins. Behavioral Ecology and Sociobiology, 33(3), 173–182.

Emmerson, L., Walsh, S., & Southwell, C. (2019). Nonbreeder birds at colonies display qualitatively similar seasonal mass change patterns as breeders. Ecology and Evolution, 9(8), 4637–4650. https://doi.org/10.1002/ece3.5067

Gorman, K. B., Williams, T. D., & Fraser, W. R. (2014). Ecological Sexual Dimorphism and Environmental Variability within a Community of Antarctic Penguins (Genus Pygoscelis). PLOS ONE, 9(3), e90081. https://doi.org/10.1371/journal.pone.0090081

Horst, A. M., Hill, A. P., & Gorman, K. B. (2022). Palmer Archipelago Penguins Data in the palmerpenguins R Package—An Alternative to Anderson’s Irises. The R Journal, 14(1), 244–254. https://doi.org/10.32614/RJ-2022-020

Hosmer, D. W., Jr., Lemeshow, S., & Sturdivant, R. X. (2013). Introduction to the Logistic Regression Model. In Applied Logistic Regression (3rd ed., pp. 1–33). John Wiley & Sons. https://doi.org/10.1002/9781118548387.ch1

