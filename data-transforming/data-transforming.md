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
Draft versions of the datasets I used for the analysis of the project are available.  Details of the intended use and modifications made at each stage are below:

1) [Initial Data](data-transforming/datasets/initial_data_output.csv).  Data as pulled from Goodreads using the webscraper. The year in which each book was nominated for the awards was added manually after the fact.
2) [Data with Subject Terms Analysis](data-transforming/datasets/deduped_subject_terms_wide - first_20_subjects.csv).  Goodreads Ids are added for each book (pulled from the list of links generated by the webscraper).  Regular Expressions are used to count the frequency of specific subject terms for each book, which enables working with a list of comma separated subject terms without breaking them into separate columns.  This dataset has been deduplicated, to include each book once (accounting for books which were nominated for multiple categories).
3) [Subject Counts](data-transforming/datasets/deduped_subject_terms_wide_binary - first_20_subjects.csv). Converts data about the presence of subject terms in each book's metadata to a binary and adds the number of books/year with each subject term to a total for use in further analysis.
4) [Subject Percents](data-transforming/datasets/deduped_subjects_longlist - _percents.csv).  Converts subject term counts to rounded percents, to facilitate visualization of the data as a line graph.
5) [Changes in Percents](data-transforming/datasets/deduped_subjects_longlist - _change_in_percents.csv) Calculations of the change in the percent of books that were tagged with each of the top 200 genres, between 2024 and 2011.
6) [Top Genre Tags](data-transforming/datasets/deduped_subject_terms-list_plus_counts - Sheet2.csv) Data including the total count of each genre in the dataset, and RegEx statements uniquely identifying each genre tag for use in the Subject Counts calculations for each year
7) [Topic Modeling Dataset](data-transforming/datasets/goodreads_dataset_for_topic-modeling.csv). Simplified version of the dataset for use in topic modeling (using python)- stores only the book ID and description field.

### To come- Data Transformation Tutorial walking through each stage of the analysis!
