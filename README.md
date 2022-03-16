# Curation of article segmented Courier corpus 

## Introduction

Each document contains the entire OCR:ed text, in markdown format, for a single Courier issue. The purpose of the curation is to manually check and correct the article segmentation for each issue in the corpus.

## Description

***Document***

The first line in the *document* `# [DOCUMENT_ID](link)` is a header with a link to the original source PDF. 

***Page***

Each *page* begins with a header `## Page [PAGE-NUMBER](link) [NUM_MISMATCHES]` containing a link to the same page in the original PDF. `NUM_MISMATCHES` is the number of mismatching article titles on the page reported during the automatic text extraction.

***Article segment***

*Article segments* within pages are indicated by an article header `### ARTICLE_ID: article-title` line. The article title is taken from the Courier [article index](https://github.com/inidun/inidun_data/blob/main/courier/articles/article_index.csv).

An *article segment* ends when any of the following is encountered:

| Description           | Example                  |
| --------------------- | ------------------------ |
| A new article segment | `### ARTICLE_ID: another title`        |
| A non-article segment | `### NON-ARTICLE-TEXT`   |
| A new page            | `## [PAGE-NUMBER](link)` |


### Example
```md
# [123456](https://.../courier/123456eng.pdf)
## [Page 1](https://.../courier/123456eng.pdf#page=1) 0
### 78910: Title of article
article text
...
### NON-ARTICLE-TEXT
non-article text
...
```

## Annotation workflow
...

## Important guidelines

 - :exclamation: If a new article header is added or changed (apart from those that already exist in the document, the title **must** be the same as for existing headers for the same article.


## TODO
 - [ ] Add Github action that checks that all article titles in each document exist in the article metadata index.


## Prerequisites

1. Install [Visual Studio Code](https://code.visualstudio.com/download)
2. Install [Git (Standalone)](https://git-scm.com/downloads)

Use default options when installing.
## Setup

1. Open ***Git CMD***
2. Navigate to desired folder
3. Clone repo `git clone https://github.com/inidun/tagged_courier.git`
4. Open Visual Studio Code `code .`

Default options
## Keyboard Shortcut tips

| Command        | Keyboard Shortcut          |
| -------------- | -------------------------- |
| Move line down | `Alt` + `DownArrow`        |
| Move line up   | `Alt` + `UpArrow`          |
| Fold level 2   | `Ctrl` + `K`, `Ctrl` + `2` |
| Unfold         | `Ctrl` + `K`, `Ctrl` + `J` |
| Open PDF       | `Ctrl` + `LeftMouseButton` |