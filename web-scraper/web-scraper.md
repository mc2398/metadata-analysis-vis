# Phase 1- Data Collection 

## Applicability to Your Project
For this project, I chose to analyze metadata about the books which were nominated for Goodreads' Reader's Choice Awards from 2011-2024.  (See more about the project's [research design](/research-design+analysis/research-design.md)).  Depending on your institution, or available resources, collecting your metadata may involve querying an API, or accessing and opening a spreadsheet.  
Many cultural heritage institutions are now making their collection's metadata publicly available. Prior to completing a web scraping project it is essential to check the availability of the data you want to use.  Don't web scrape if you don't have to!

In order to access this data I built a web scraper, based on work from [The Goodreads Classics](https://github.com/maria-antoniak/goodreads-scraper) a digital humanities project. When I completed my project in spring 2025, the code for that project's web scraper was unmaintained and no longer functioning, in large part due to updates Goodreads has made to the structure of its book pages.  The My project also differed from the Goodreads' Classics project, in that I was 1) not interested in pulling data from Goodreads' reviews 2) and did not have an existing list of IDs for books I wanted to scrape (although I had limited the scope of my project to nominees for the Readers Choice Awards in order to ensure I had a manageably sized dataset for this exploratory project).  Thus the program I built first loops over the Goodreads website to pull a list of urls of all of the books which were nominated for the awards, so that I could pull metadata about each book.

## Web Scraping Process and Suggestions
Should you determine that web scraping is essential for your process, you will need the following:
1) Ability to read and understand html (essential for determining the structure of the website you are navigating)
2) Ability to read and write in python (the code I wrote for this project is by no means elegant but it works)  
3) Either an IDE or workbook in which you can run python (I used google Colab)
2) Plenty of time

This Project uses a number of python libraries including:
1) [Beautiful Soup](https://beautiful-soup-4.readthedocs.io/en/latest/)  
2) Regex (which allowed me to identify specific links and information I wanted to target)  
3) [Pandas](https://pandas.pydata.org/docs/) Which is also helpful with working with large datasets  

The code created for this project will likely no longer function in the near future, and cannot be used for a website other than Goodreads.  As the structure, and identifying tags used on the website are modified, the scripts in this project will break.  In particular, the html tags which are used to identify specific pieces will likely be updated over time.
    For example- this scraper identifies the title of each book using the h1 tag and an attribute: 
        for title in soup.find('h1', {'data-testid': 'bookTitle'}):  
    If modifying the code from this project to meet your needs, you may need to adjust this specific component of the code- the beautiful soup documentation is helpful for navigating this part of the process.

Like all programming, it is helpful to approach your project in manageable stages. Prior to testing the functions I wrote on the full collection, I tested each function, by passing each the page for one book as a list.  

When pulling data using web scraping, it is essential to use the sleep function, which builds in a small amount of time between each data request, to avoid overloading the servers of the site you are querying.  