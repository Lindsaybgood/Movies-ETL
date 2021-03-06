# Movies-ETL

An exercise in performing an Extract, Transform, Load (ETL) process to create data pipelines using Python, Pandas and PostgreSQL using very large data files.

![Snap1](https://user-images.githubusercontent.com/96216509/154576139-9ea94285-fc8f-4d77-b300-1a210d5d9992.png)

## Overview

The purpose of this project was to create an automated pipeline that takes in new data, performs the appropriate transformations, and loads the data into existing tables that is connected to a database. The chosen topic is all about Movies from 1990 to 2018 and combining the information from 3 different resources.

## Process

Create an ETL pipeline using Jupyter Notebooks and PostgreSQL from raw data to SQL database.

* **Extract:** read data from multiple sources using Python. Data sourced from:
	* **Wikipedia:** (format: .json, file size: 6.2MB) 7,311 thousand movie titles that include information about the movies, budgets, box office returns, cast/crew, production and distribution.
	* **Kaggle:** - 2 files (format: .csv)
		* a metadata file from [The Movie Database](https://www.themoviedb.org/) containing movie details with 45.5 thousand entries. (File size: 34.4MB)
		* a dataset from [MovieLens](https://movielens.org/) containing over 26 million movie ratings/review. (File size: 709.6MB)

* **Transform:** Clean and structure data using Pandas and regular expressions (RegEx) to achieve desired form. (i.e. using RegEx to parse data and transform text into numbers.
	* Deleting bad data (corrupted or missing), removing duplicate rows, and consolidating columns.
	* Using RegEx to parse data and transform text into numbers.

* **Load:** Export transformed data into a database.

## Results

Ultimately, we were able to clean, merge the datasets and export the two new tables into PostgreSQL by using Python. The final results created a movies table with 6,052 rows. A 17% reduction from the original of 7,311 and a ratings table with 26,024,289 rows.

![movie](https://user-images.githubusercontent.com/96216509/154576584-6693aadb-2a29-493c-aad6-38f6c9d411b6.png)

![ratings](https://user-images.githubusercontent.com/96216509/154576759-6c80c132-ae2f-41e7-89e3-6a9dbc36aca5.png)


## Issues

Working with such large files presented issues along the way. For example in the module practice run, committing the repository to Github resulted in an error because the resource file from MovieLens was too large. Github has a strict 100MB limit. Attempts to resolve this issue using Git LFS and clear the cache were unsuccessful. I attempted to:
* git rm --cached to remove the large ratings.csv file
* git push rewritten, smaller commit

Each attempt resulted in `remote: error: File ratings.csv.zip is 169.99 MB; this exceeds GitHub's file size limit of 100.00 MB` regardless of the `git rm --cached` command.

Attempts to have the file tracked through `git lfs track "*.csv"` and have the file uploaded utilizing LFS also resulted in an error. 

Also, extracting and loading the ratings data (26 million rows) into the database took more than 3 hours to complete in the practice file and 2 hours to complete when executing [Deliverable 4 file](https://github.com/Lindsaybgood/Movies-ETL/blob/main/ETL_create_database.ipynb).

**Practice File Results**

![timestamp](https://user-images.githubusercontent.com/96216509/154577514-1da15342-01bc-42ea-98c7-b8d423e69e69.png)

**Deliverable 4 File Results**

![timestampfinal](https://user-images.githubusercontent.com/96216509/154577632-26551da2-b0e4-4ce9-8467-fd392b981100.png)


## Summary

Overall, this was a very dense topic to learn and complete in one week. The process of reviewing the data and knowing what to "clean" was challenging, including cross comparison between the datasets, as well as, learning how to use RegEx to parse the text. I expect that to become an expert in ETL, especially RegEx outside of class would require extensive practice and application using real-life examples. I am hoping that with time, I can apply this learning to prepare large datasets for analysis.  

## Resources
* **Software:** Python 3.9.7, Anaconda 4.10.3, Jupyter Notebooks 6.4.5, PostgreSQL 4.28 
* **Libraries:** Pandas, SQLAlchemy, NumPy
* **Troubleshooting:** [Deleting Cache](https://docs.github.com/en/github/managing-large-files/removing-files-from-a-repositorys-history), [Using Git LFS](https://git-lfs.github.com/)
* **Files:** [Wikipedia Json](https://github.com/Lindsaybgood/Movies-ETL/blob/main/Resources/wikipedia-movies.json), [Movie Database Metadata](https://github.com/Lindsaybgood/Movies-ETL/blob/main/Resources/movies_metadata.csv), and [MovieLens Ratings](https://www.kaggle.com/rounakbanik/the-movies-dataset?select=ratings.csv) 
* 
