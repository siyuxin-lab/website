# Blog Post 2: What Is the Market Talking About?

For this post #2, I used R to scrape financial-news headlines from public RSS feeds (CNBC, Bloomberg, and MarketWatch) and turn them into two things: which themes the market is talking about most right now, and whether the coverage of each theme leans positive or negative. Every trading morning there is a wall of financial news that people read by gut, so I wanted to see whether that "morning scan" could be turned into a single repeatable number instead of a feeling.

All of the code and writing are in `blog/posts/post2/index.qmd`.

I saved a snapshot of the headlines the day I collected them, because news changes by the minute. This lets someone else repeat the analysis using the exact same headlines I used, even after the live feeds have moved on.

## Where to find everything

Open `website2.Rproj` at the top of the repository. The relevant files are:

- `blog/posts/post2/index.qmd` has the code and the blog post.
- `data/raw/headlines.csv` is the saved snapshot of the headlines I used.
- `data/loughran_lexicon.csv` is the saved Loughran-McDonald sentiment dictionary, so no download is needed to reproduce the scores.
- `blog/posts/post2/index.html` is the rendered post.
- The figures are generated at render time into `blog/posts/post2/index_files/`, and the summary table is generated inline in the post.

(The data and the dictionary live in the repo-level `data/` folder because the code uses the `here` package to locate them from the project root.)

## How to run the analysis

Download the whole repository and open `website2.Rproj` in RStudio. You will need R and Quarto installed (Quarto ships with recent versions of RStudio).

If you have not installed the packages yet, run this in the R Console:

```r
install.packages(c("here", "rvest", "tidyverse", "tidytext", "textdata", "knitr"))
```

Then open `blog/posts/post2/index.qmd`, leave `refresh <- FALSE`, and click Render. The code will use the saved snapshot and the saved dictionary to recreate the cleaned data, figures, table, and blog post — no internet connection needed, and the numbers will match those discussed in my post.

To collect a newer set of listings, change `refresh` to `TRUE`. The code will then scrape the live feeds again, and the results may differ from those discussed in my original post because the news will have changed.

## Data sources

Public RSS feeds — the machine-readable feeds these outlets publish specifically for programs to subscribe to. No logins, paywalls, or CAPTCHAs are involved, and the code pauses one second between requests so it never stresses a server:

- CNBC — Top News, Markets, Finance
- Bloomberg — Markets, Business, Technology
- MarketWatch — Top Stories

Sentiment scoring uses the Loughran-McDonald financial dictionary via the `tidytext` package.


