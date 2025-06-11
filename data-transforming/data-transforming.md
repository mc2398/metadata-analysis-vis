# Phase 2- Transforming your Data

## Data Requirements
The metadata included in my project's analysis included:
    - Book Titles
    - A unique id for each book
    - Subject Terms (called Genres on Goodreads)
    - A description field for each book
    - The year in which each book was nominated for the Goodreads Choice Awards

For a similar project, the following fields are suggested for inclusion at the minimum:
    - Book titles
    - Unique Book ids (can be generated during data collection if not preexisting in metadata)
    - Subject Terms
    - Book summary or abstract
    - Circulation Counts (ideally broken down by year to enable analysis of a book's popularity over time)

Additional metadata, identifying genres, series, languages, or formats, may also prove useful depending on the needs of your institution or project.

## Tools
For my project, I used a combination of Google Sheets and [OpenRefine](https://openrefine.org/) to tranform and modify the data used for the project.
As of spring 2025, Google Sheets has a file size limit of 100MB and a maximum number of cells (across all sheets in a project) of 10 million cells. OpenRefine can similarly work with a large amount of data, however, with very large collections, it may be helpful to work with subsets of the collection, or to use [Pandas](https://pandas.pydata.org/docs/) to conduct initial analysis.

## Datasets
Draft versions of the datasets I used for the analysis of the project are available as csvs in the datasets folder, and in a public [google sheets folder](https://drive.google.com/drive/folders/1cNs4Pt_WTyY_A0Jl-BtC47Q1LWYoJEoZ?usp=sharing) (individual files hyper-linked in the list below).  Details of the intended use and modifications made at each stage are below:

Note that across all datasets 0 indicates "no", ie., a row does not include a given attribute or subject term, while 1 indicates "yes".

1) [Raw Data- All Fields](https://docs.google.com/spreadsheets/d/1lDUWIl2z2zZfivjH5wti6w8RDAn--GmeoGuamTY6I70/edit?usp=drive_link).  Data as pulled from Goodreads using the webscraper. The year in which each book was nominated for the awards was added manually after the fact.  Authors were also pulled in a later round of web-scraping and added to the dataset.  Original order represents the order in which books are listed on Goodreads' website, and pulled using the web scraper.
2) [Author Data](https://docs.google.com/spreadsheets/d/12mBbl5dLK6z4TkT4HGpotUAVjZEOreRT9fXRH30PHIs/edit?usp=drive_link). Contains a row for each author of the included books.  Books have been already deduplicated.  Multiauthored books and repeat authors are identified.
3) [Duplicate Categories Data](https://docs.google.com/spreadsheets/d/1BuxkDnpcS_0RseQiU4Awm7jtKpzh_2FetuWIfrja-Qs/edit?usp=drive_link) Contains all fields for the books analysed in the dataset- added field noting the categories each book is assigned to, including whether or not a book is a duplicate (ie., nominated for multiple categories).
4) [Genres regex plus counts](https://docs.google.com/spreadsheets/d/1F-utjm_yurJJtLgEDd93VTj5omuxMxuWe4TLP0tFy6c/edit?usp=drive_link) Data including the total count of each genre in the dataset, and regex statements uniquely identifying each genre tag for use in the subject counts calculations for each year.  Top genre tags were calulated using facet analysis in OpenRefine (based on a long version of all genre tags where, following book deduplication, each tag was transposed into a long list of all the tags and faceted by count)(tutorial of this process to come).
5) [Deduplicated books with subject term analysis](https://docs.google.com/spreadsheets/d/1E8NCbeJlDZjw-7grYL67Kk5Y7AruVYHByKDknEd2484/edit?usp=drive_link).  Regular Expressions are used to count the frequency of specific subject terms for each book, which enables working with a list of comma separated subject terms without breaking them into separate columns.  This dataset has been deduplicated, to include each book once (accounting for books which were nominated for multiple categories).  The google sheets version of this sheet includes sheets for all of the top 200 genres/subject terms. The csv version only includes the top 20 subjects.
6) [binary_subject_counts_top_20_subjects](https://docs.google.com/spreadsheets/d/1NUA2aHmCE2EJEz6dEee0LXMVIFnoCT6gBIX8EkqAlR8/edit?usp=drive_link). Converts data about the presence of subject terms in each book's metadata to a binary and adds the number of books per year with each subject term to a total for use in further analysis.  The included sheet is an example, for the top 20 subjects, although sheets for all top 200 subject terms were created for the analysis. The google sheets version includes counts for all years, but the csv version only includes calculations for the counts of the overall top 20 subjects in 2024.
7) [Subject Percent Calculations](https://docs.google.com/spreadsheets/d/1bPJbR8JBtq8fbQWUYZ5timNPOpMZaa1JFYS2OOK0UJg/edit?usp=drive_link).  Converts subject term counts to rounded percents, to facilitate visualization of the data as a line graph.
8) [Changes in Percents](https://docs.google.com/spreadsheets/d/1H7u7ILffXFEW5NjQ12V8NbaMhogEEDfRhWBW0DX1PdM/edit?usp=drive_link). Calculations of the change in the percent of books that were tagged with each of the top 200 genres, between 2024 and 2011.  Dataset includes counts of the number of subjects which changed by a given percent, for use in a visualization.  The google sheets version includes sheets which were used for making calculations of the rate of change of each subject's representation.
9) [Topic Modeling Dataset](https://docs.google.com/spreadsheets/d/1Z2eilAzB5k4ftWuUV3x0Fts8J8JKZw5v5yssQhR4mTw/edit?usp=drive_link). Simplified version of the dataset for use in topic modeling (using python)- stores only the book ID and description field. The description field has been edited to remove new lines.  Books have not been deduplicated to remove books nominated for multiple categories.

### To come- Data Transformation Tutorial walking through each stage of the analysis!
