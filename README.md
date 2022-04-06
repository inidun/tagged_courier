# Courier corpus article segmentation

## Introduction

Each document contains the entire OCR:ed text, in markdown format, for a single Courier issue. The purpose of the curation is to manually check and correct the article segmentation for each issue in the corpus. The end goal is to mark up all text segments that belong to an article in such a way that it can be automatically extracted. To do this we need to insert a heading above each text segment, as well as an indicator where the segment ends. 

### Heading

A heading is a line that starts with a number signs (#). The number of number signs corresponds to the heading level.
### Document

The first line in each *document* `# [DOCUMENT_ID](link) TOTAL_MISMATCHES` is a heading with a link to its original source PDF. `TOTAL_MISMATCHES` is the number of mismatching article titles in the *issue*.

### Page

Each *page* begins with a heading `## Page [PAGE-NUMBER](link) MISMATCHES` containing a link to the same page in the original PDF. `MISMATCHES` is the number of mismatching article titles on the page reported during the automatic text extraction.

### Article

*Articles* within pages are indicated by an article heading `### ARTICLE_ID: article-title` line. The article title is taken from the Courier [article index](https://github.com/inidun/inidun_data/blob/main/courier/articles/article_index.csv).


### Text segment

Sequences of text that are not headings in the formats described above are called *text segments*. 

A *text segment* (article or non-article) **ends** when any of the following is encountered:

| Description           | Example                             |
| --------------------- | ----------------------------------- |
| A new page heading    | `## [PAGE-NUMBER](link) MISMATCHES` |
| A new article heading | `### ARTICLE_ID: another title`     |
| A non-article heading | `### IGNORE`                        |

### Example Document

```md
# [123456](https://.../courier/123456eng.pdf) 12

## [Page 1](https://.../courier/123456eng.pdf#page=1) 0

### 78910: Title of article

article text

### IGNORE

non-article text

```

## Annotation workflow
1. Process one issue at a time.
1. Correct title positions for each pages. Compare with PDF page and move title to the correct position within the page.
3. If article ends before new page or new article, mark ending by adding `### IGNORE`
4. Add `### IGNORE` for text segments which don't contain article text.
5. Add `### EDITORIAL` heading. Mark end of editorial with `### IGNORE`
6. Push changes after completing each issue.

### Important guidelines

 - If a new article heading is added or changed (apart from those that already exist in the document, the title **must** be the same as for existing headings for the same article.
 - Captions are a part of an article and should be included.
 - Note problems with filename and line number.
 - Text should not be changed or corrected.
 - Each heading should be on new line. No other text is allowed on that line.

## Environment

### In browser (Preferred)
1. Navigate to https://github.com/inidun/tagged_courier in browser.
2. Push `.` to open VS Code in browser.
   
### Alternative (Installation)
#### Prerequisites

1. Install [Visual Studio Code](https://code.visualstudio.com/download)
2. Install [Git (Standalone)](https://git-scm.com/downloads)

Use default options when installing.
#### Setup

1. Open ***Git CMD***
2. Navigate to desired folder
3. Clone repo `git clone https://github.com/inidun/tagged_courier.git`
4. Open Visual Studio Code `code .`



### Keyboard Shortcut tips

| Command        | Keyboard Shortcut          |
| -------------- | -------------------------- |
| Move line down | `Alt` + `DownArrow`        |
| Move line up   | `Alt` + `UpArrow`          |
| Fold level 2   | `Ctrl` + `K`, `Ctrl` + `2` |
| Unfold         | `Ctrl` + `K`, `Ctrl` + `J` |
| Open PDF       | `Ctrl` + `LeftMouseButton` |