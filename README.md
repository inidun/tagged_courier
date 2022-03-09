# Article segmented courier corpus 

## Introduction

Each document contains the entire OCR:ed text for a single Courier issue. The first line **`# [ID](link)`** is a link to the original source PDF. Each page in the document begins with link **`#[page-number](link)`** to the that page in the original PDF.

Article text segments within the issue are indicated by an *article header* **`### article-title`** line, and the `article-title` is taken from the Courier article index metadata (link). An article segment ends wither at the end of the page, if a new article begins (a new **`### another-title`**) or if a non-article text segment is encountered (**`### non-article-text`**). 

## Annotation workflow


## Important guidelines

 - If a new article header is added or changed (apart from those that already exit in the document, the title **must** be the same as for existing headers for the same article.)


```md
# [{COURIER_ID}](link_to_pdf)
## [Page page_number](link_to_pdf_page) 🆗
### Article title or Non-article
text 
...
```

## TODO
 - Add Github action that checks that all article titles in each document exist in the article metadata index.


## Prerequisites

Use default options when installing

- [Visual Studio Code](https://code.visualstudio.com/download)
- [Git (Standalone)](https://git-scm.com/downloads)

## Setup

1. Open `Git CMD`
2. Navigate to desired folder
3. Clone repo `git clone https://github.com/inidun/tagged_courier.git`
4. Open Visual Studio Code `code .`

Default options
## Keyboard Shortcut tips

| Command        | Keyboard Shortcut            |
| -------------- | ---------------------------- |
| Move line down | `Alt` + `DownArrow`          |
| Move line up   | `Alt` + `UpArrow`            |
| Fold level 2   | `Ctrl` + `K`, `Ctrl` + `2`   |
| Unfold         | `Ctrl` + `K`, `Ctrl` + `J`   |
| Open PDF       | `Ctrl` + `LeftMouseButton` |