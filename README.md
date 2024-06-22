## SQL Book Review Analysis and Insights
## Overview
This repository contains a series of SQL queries designed to extract and manipulate data from a book review database. The database includes various tables such as **`users`**, **`genders`**, **`locations`**, **`occupations`**, **`books`**, **`authors`**, **`publishers`**, **`languages`**, and **`ratings`**. Each query is written to fulfill specific data retrieval needs, focusing on different aspects of the database like user demographics, book details, ratings, and more.

## Database Schema

**Users and Genders**
- Users Table: Contains user details including first name, last name, email, birthdate, gender ID, location ID, and occupation ID.
- Genders Table: Maps gender IDs to gender descriptions.
  
**Users and Locations**
- Locations Table: Contains location details including country and city.
  
**Users and Occupations**
- Occupations Table: Maps occupation IDs to occupation names.

**Books and Authors**
- Books Table: Contains book details including title, number of pages, publication date, author ID, language code, and publisher ID.
- Authors Table: Maps author IDs to author names.

**Books and Languages**
- Languages Table: Maps language codes to language names.

**Ratings, Books, and Users**
- Ratings Table: Contains rating details including rating ID, rating date, rating, book ID, and user ID.

**Books and Publishers**
- Publishers Table: Maps publisher IDs to publisher names.

**SQL Queries Description**

**Users and Genders**

- **Query 1:** Displays user details (first name, last name, email, birthdate, gender).
- **Query 2:** Restricts the above query to users born in 2002.
- **Query 3:** Displays the number of users born each year, sorted by year.
- **Query 4:** Filters the previous query to show only years with more than 54 users born.

**Users and Locations**

- **Query 5:** Displays user details along with their country and city.
- **Query 6:** Restricts the above query to users living in the UK.
- **Query 7:** Breaks down the number of users living in each country and city, sorted by the number of users.
- **Query 8:** Filters the previous query to count only users above the age of 30.

**Users and Occupations**

- **Query 9:** Displays user details along with their occupation and age.
- **Query 10:** Displays the average age for each occupation.
- **Query 11:** Filters the previous query to show only occupations with an average age greater than 40.

**Books and Authors**
- **Query 12:** Displays the average number of pages for each author, sorted by the average number of pages.

**Books and Languages**
- **Query 13:** Displays the number of books for each language, sorted by the number of books.
- **Query 14:** Displays the number of unique publishers for each language, sorted by the number of unique publishers.

**Users, Occupations, and Locations**
- **Query 15:** Displays user details along with their occupation, country, and city.
- **Query 16:** Breaks down the number of users for each country and occupation.

**Ratings, Books, and Users**
- **Query 17:** Displays rating details along with the book title and user's full name.
- **Query 18:** Restricts the above query to ratings related to the 'Harry Potter' book series.
- **Query 19:** Counts the number of unique users who have rated 'Harry Potter' books.

**Ratings, Books, Users, and Locations**
- **Query 20:** Counts the number of unique users who have rated 'Harry Potter' books, broken down by country.

**Books and Publishers**
- **Query 21:** Displays book details along with the publisher name, including books with no publisher details.
- **Query 22:** Restricts the above query to books with no publisher details.

**Books and Authors**
- **Query 23:** Displays book details along with the author name, including books with no author details.
- **Query 24:** Restricts the above query to books with no author details.

**Books and Ratings**
- **Query 25:** Counts the number of books that have never been rated.

## Files
- **README.md:** This file.
- **queries.sql:** File containing all the SQL queries described.

## Explore SQL Queries: 
Review the SQL queries provided in the `SQL queries_book_review.sql` file to understand how data can be extracted and manipulated from the bookreview database.

