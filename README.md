# Quarto Starter Examples

Beginner-friendly Quarto examples covering Markdown documents, Python reports,
Reveal.js slides, and R data analysis.

Four independent examples, ordered from basic formatting to executable reports:

| File | Demonstrates | Requirements |
|:-----|:-------------|:-------------|
| [01-basics.qmd](01-basics.qmd) | Headings, tables, equations, callouts, and displayed code | Quarto |
| [02-python-report.qmd](02-python-report.qmd) | Python calculations, a generated table, and a chart | Quarto, Python, Jupyter, matplotlib |
| [03-slides.qmd](03-slides.qmd) | Reveal.js slides, incremental lists, columns, and speaker notes | Quarto |
| [04-r-analysis.qmd](04-r-analysis.qmd) | R summaries and a plot using the built-in iris dataset | Quarto, R, knitr, rmarkdown |

## Get started

Install the [Quarto CLI](https://quarto.org/docs/get-started/), then preview a sample:

```sh
quarto preview 01-basics.qmd
```

Render a finished HTML document or slide deck:

```sh
quarto render 01-basics.qmd
quarto render 03-slides.qmd
```

Each command writes an HTML file beside its source. Keep any generated companion
`*_files` folder with the HTML when sharing it.

## Execute the reports

For the Python example, install dependencies in your Python environment:

```sh
python3 -m pip install jupyter matplotlib
quarto render 02-python-report.qmd
```

For the R example, install the rendering packages in R:

```r
install.packages(c("knitr", "rmarkdown"))
```

Then render from your terminal:

```sh
quarto render 04-r-analysis.qmd
```

## Try another document format

```sh
quarto render 01-basics.qmd --to docx
quarto render 01-basics.qmd --to pdf
```

PDF output requires a LaTeX installation. Quarto can install TinyTeX with
`quarto install tinytex`.

See the official guides to [Python execution](https://quarto.org/docs/computations/python.html)
and [Reveal.js presentations](https://quarto.org/docs/presentations/revealjs/)
for more options.
