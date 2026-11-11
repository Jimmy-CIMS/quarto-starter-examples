# Quarto Starter Examples

Beginner-friendly Quarto examples covering documents, executable reports,
presentations, diagrams, scholarly writing, interactive charts, dashboards,
websites, and books.

Eleven independent examples, starting with basic formatting and progressing to
complete projects. All data is fictional or bundled with R; no API keys or data
downloads are needed.

| File | Demonstrates | Requirements |
|:-----|:-------------|:-------------|
| [01-basics.qmd](01-basics.qmd) | Headings, tables, equations, callouts, and displayed code | Quarto |
| [02-python-report.qmd](02-python-report.qmd) | Python calculations, a generated table, and a chart | Quarto, Python, Jupyter, matplotlib |
| [03-slides.qmd](03-slides.qmd) | Reveal.js slides, incremental lists, columns, and speaker notes | Quarto |
| [04-r-analysis.qmd](04-r-analysis.qmd) | R summaries and a plot using the built-in iris dataset | Quarto, R, knitr, rmarkdown |
| [05-diagrams.qmd](05-diagrams.qmd) | Mermaid flowchart, sequence diagram, and figure references | Quarto (HTML) |
| [06-academic-writing.qmd](06-academic-writing.qmd) | BibTeX citations, bibliography, footnotes, equations, and cross-references | Quarto, included `references.bib` |
| [07-interactive-charts.qmd](07-interactive-charts.qmd) | Plotly hover, zoom, region dropdown, and legend filtering | Quarto, Python, Jupyter, plotly |
| [08-parameterized-report.qmd](08-parameterized-report.qmd) | R report variants selected by department and month | Quarto, R, knitr, rmarkdown |
| [09-dashboard.qmd](09-dashboard.qmd) | Computed KPI cards, a chart, a table, and row layouts | Quarto 1.4+, Python, Jupyter, matplotlib |
| [10-website/](10-website/) | Multi-page site with navigation, search, article listings, categories, and CSS | Quarto |
| [11-book/](11-book/) | Chapters, cross-references, and HTML/PDF/EPUB editions | Quarto; LaTeX for PDF only |

Use a current stable Quarto release for all examples. Examples 01–09 are
standalone documents; 10 and 11 have their own `_quarto.yml` project files.
Commands below assume your terminal is in the repository root.

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

The dashboard uses the same dependencies:

```sh
quarto render 09-dashboard.qmd
```

For the interactive chart, add Plotly:

```sh
python3 -m pip install jupyter plotly
quarto render 07-interactive-charts.qmd
```

The interactive HTML embeds the Plotly library, so it can be used without a
Python server or a CDN connection. These interactions target HTML output.

For the R example, install the rendering packages in R:

```r
install.packages(c("knitr", "rmarkdown"))
```

Then render from your terminal:

```sh
quarto render 04-r-analysis.qmd
```

## Diagrams and academic writing

These examples need no Python or R:

```sh
quarto render 05-diagrams.qmd
quarto render 06-academic-writing.qmd
```

The Mermaid example targets HTML. Keep [references.bib](references.bib) beside
the academic document when copying it. Edit the bibliography and use `@key`
to add citations; Quarto generates the reference list.

## Parameterized reports

Render the default Sales/January report, override the parameters on the command
line, or load the included [parameter file](08-report-params.yml):

```sh
quarto render 08-parameterized-report.qmd
quarto render 08-parameterized-report.qmd -P department:Support -P month:Feb --output support-feb.html
quarto render 08-parameterized-report.qmd --execute-params 08-report-params.yml --output support-feb-from-file.html
```

Supported departments are `Sales` and `Support`; months are `Jan`, `Feb`, and
`Mar`. Each render creates a fixed report. Use distinct output filenames to
keep multiple variants. The R dependencies are the same as example 04.

## Website and blog

```sh
quarto preview 10-website
quarto render 10-website
```

The site includes a home page, an About page, and two articles. Add a `.qmd`
file under `10-website/posts/` with a title, description, date, and categories
to extend the listing. Navigation, search, and the theme are configured in
[10-website/_quarto.yml](10-website/_quarto.yml).

The generated site is in `10-website/_site/`. Share the entire folder through
a static website host, including its search index and assets.

## Book editions

```sh
quarto preview 11-book --to html
quarto render 11-book --to html
quarto render 11-book --to epub
```

The book has a preface and two chapters. Set their order in
[11-book/_quarto.yml](11-book/_quarto.yml). Outputs are written to
`11-book/_book/`; EPUB is a single file, while the HTML edition needs its
complete output folder. EPUB does not require LaTeX.

For the PDF edition, install LaTeX as described below, then run:

```sh
quarto render 11-book --to pdf
```

Always choose `--to html`, `--to epub`, or `--to pdf` for the book so that
Quarto only builds the edition you need. Building without `--to` renders all
configured formats and therefore requires LaTeX.

Project renders clean their output folder by default. To keep a previously
rendered edition while building another, add `--no-clean`, for example
`quarto render 11-book --to epub --no-clean`.

## Try another document format

```sh
quarto render 01-basics.qmd --to docx
quarto render 01-basics.qmd --to pdf
```

PDF output requires a LaTeX installation. Quarto can install TinyTeX with
`quarto install tinytex`.

See the official guides to [Python execution](https://quarto.org/docs/computations/python.html),
[Reveal.js](https://quarto.org/docs/presentations/revealjs/),
[diagrams](https://quarto.org/docs/authoring/diagrams.html),
[citations](https://quarto.org/docs/authoring/citations.html),
[parameters](https://quarto.org/docs/computations/parameters.html),
[dashboards](https://quarto.org/docs/dashboards/),
[websites](https://quarto.org/docs/websites/), and
[books](https://quarto.org/docs/books/) for more options.
