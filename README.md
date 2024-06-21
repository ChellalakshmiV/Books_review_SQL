# Books_review_SQL

```sql
use bookreview;
```

1. [users and genders]
- a. Write a query to display the first_name, last_name, email, birthdate, and gender for all users
- b. Restrict your query to display only users who were born on 2002
- c. Write a query to display the number of users who were born each year. Sort the output by year (ascending)
- d. Repeat your last query, only this time display only years with more than 54 users (who were born on that year)

```sql
select *from users;
select * from genders;
```
```sql
-- a. Write a query to display the first_name, last_name, email, birthdate, and gender for all users

SELECT U.first_name, U.last_name, U.email, U.birthdate, G.gender
FROM users U INNER JOIN genders G
ON U.gender_id= G.gender_id; 
```

```sql
-- b. Restrict your query to display only users who were born on 2002

SELECT U.first_name, U.last_name, U.email, U.birthdate, G.gender
FROM users U INNER JOIN genders G
ON U.gender_id= G.gender_id
WHERE YEAR(U.birthdate) = '2002';
```
```sql
-- c. Write a query to display the number of users who were born each year. Sort the output by year (ascending)

SELECT YEAR(birthdate) AS 'Year', COUNT(*) AS 'Number_of_users'
FROM users 
GROUP BY YEAR(birthdate)
order by Year;
```
```sql
-- d. Repeat your last query, only this time display only years with more than 54 users (who were born on that year)

SELECT YEAR(birthdate) AS 'Year', COUNT(*) AS 'Number_of_users'
FROM users
GROUP BY YEAR(birthdate)
HAVING Number_of_users > 54
order by Year;
```
-- ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------
2. [users and locations]
- a. Write a query to display the first_name, last_name, email, birthdate, country and city for all users
- b. Restrict your query to display only users living in the UK
- c. Write a query to break down the number of users living in each country and city. Sort the output by the number of users (descending)
- d. Restrict your query to count only users above the age 30 
```sql
select * from users;
select * from locations;
```
```sql
-- a. Write a query to display the first_name, last_name, email, birthdate, country and city for all users

SELECT U.first_name, U.last_name, U.email, U.birthdate, L.country, L.city
FROM users U INNER JOIN locations L
ON U.location_id = L.location_id;
```
```sql
--  b. Restrict your query to display only users living in the UK

SELECT U.first_name, U.last_name, U.email, U.birthdate, L.country, L.city
FROM users U INNER JOIN locations L
ON U.location_id = L.location_id
WHERE L.country = 'United Kingdom';
```
```sql
-- c. Write a query to break down the number of users living in each country and city.Sort the output by the number of users (desc)

SELECT L.country, L.city, COUNT(*) AS 'Number_of_users'
FROM users U INNER JOIN locations L 
ON U.location_id = L.location_id
GROUP BY L.country, L.city
ORDER BY Number_of_users DESC;
```
```sql
-- d. Restrict your query to count only users above the age 30

SELECT L.country, L.city, COUNT(*) AS 'Number_of_users'
FROM users U INNER JOIN locations L 
ON U.location_id = L.location_id
WHERE TIMESTAMPDIFF(YEAR, U.birthdate, CURDATE()) > 30
GROUP BY L.country, L.city
ORDER BY Number_of_users DESC;
```
-- ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
3. [users and occupations]
- a. Write a query to display the first_name, last_name, email, age, and occupation_name for all users
- b. Write a query to display the average age for each occupation
- c. Restrict your query to display only occupations with average age greater than 40
```sql
select * from users;
select * from occupations;
```
```sql
-- a. Write a query to display the first_name, last_name, email, age, and occupation_name for all users

SELECT U.first_name, U.last_name, U.email, TIMESTAMPDIFF(YEAR, U.birthdate, CURDATE()) AS 'age', O.occupation_name
FROM users U INNER JOIN occupations O
ON U.occupation_id = O.occupation_id;
```
```sql
-- b. Write a query to display the average age for each occupation

SELECT O.occupation_name, AVG(TIMESTAMPDIFF(YEAR, U.birthdate, CURDATE())) AS 'Average_age'
FROM users U INNER JOIN occupations O
ON U.occupation_id = O.occupation_id
GROUP BY  O.occupation_name;
```
```sql
-- c. Restrict your query to display only occupations with average age greater than 40

SELECT O.occupation_name, AVG(TIMESTAMPDIFF(YEAR, U.birthdate, CURDATE())) AS 'Average_age'
FROM users U INNER JOIN occupations O
ON U.occupation_id = O.occupation_id
GROUP BY  O.occupation_name
HAVING Average_age > 40;
```
-- -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
4. [books and authors]
- Write a query to display the average num_pages for each author. Sort the output by the average number of pages (descending)
```sql
-- Write a query to display the average num_pages for each author. Sort the output by the average number of pages (descending)

SELECT A.authors,AVG(B.num_pages) AS 'average_num_pages'
FROM books B INNER JOIN authors A
ON  B.author_id = A.author_id 
GROUP BY A.authors
ORDER BY average_num_pages DESC;
```
-- ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
5. [books and languages]
```sql
select*from books;
select * from languages;
```
- Write a query to display the number of books for each language, Sort the output by the number of books (desc)
```sql
-- Write a query to display the number of books for each language, Sort the output by the number of books (desc)

SELECT L.language_name, COUNT(*) AS 'Number_of_books'
FROM books B INNER JOIN languages L
ON B.language_code = L.language_code 
GROUP BY L.language_name
ORDER BY Number_of_books DESC;
```
-- ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
6. [books and languages]
- Write a query to display the number of unique publishers by each language,Sort the output by the number of unique publishers(desc)   
```sql
-- Write a query to display the number of unique publishers by each language,Sort the output by the number of unique publishers(desc)
              
SELECT L.language_name, COUNT(distinct publisher_id) AS 'Unique_publishers'
FROM languages L INNER JOIN books B 
ON L.language_code = B.language_code
GROUP BY L.language_name
order by Unique_publishers DESC;
```
-- ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
7. [users, occupations and locations]
- a. Write a query to display the first_name, last_name, email, birthdate, occupation_name, country and city for all users
- b. Write a query to breakdown the number of users for each country and occupation
```sql
--   a. Write a query to display the first_name, last_name, email, birthdate, occupation_name, country and city for all users

SELECT U.first_name, U.last_name, U.email, U.birthdate, O.occupation_name, L.country, L.city
FROM users U 
INNER JOIN occupations O ON U.occupation_id = O.occupation_id
INNER JOIN locations L ON U.location_id = L.location_id;
```
```sql
--   b. Write a query to breakdown the number of users for each country and occupation

SELECT L.country, O.occupation_name,COUNT(*) AS 'Num_of_users'
FROM users U 
INNER JOIN occupations O ON U.occupation_id = O.occupation_id
INNER JOIN locations L ON U.location_id = L.location_id
GROUP BY L.country,  O.occupation_name;
```
8. [ratings, books and users]
- a. Write a query to display the rating_id, rating_date, rating, book title, and user's full name for each rating
- b. Restrict your query to display ratings related to the 'Harry Potter' book-series
- c. How many unique users have rated titles related to the 'Harry Potter' book-series?
```sql
-- a. Write a query to display the rating_id, rating_date, rating, book title, and user's full name for each rating

SELECT R.rating_id, R.rating_date, R.rating, B.title, CONCAT(U.first_name,' ', U.last_name) AS 'full_name'
FROM ratings R
INNER JOIN books B ON R.book_id = B.book_id
INNER JOIN users U ON R.user_id = U.user_id ;
```
```sql
-- b. Restrict your query to display ratings related to the 'Harry Potter' book-series

SELECT R.rating_id, R.rating_date, R.rating, B.title, CONCAT(U.first_name,' ', U.last_name) AS 'full_name'
FROM ratings R
INNER JOIN books B ON R.book_id = B.book_id
INNER JOIN users U ON R.user_id = U.user_id 
WHERE B.title LIKE '%Harry Potter%';
```
```sql
-- c. How many unique users have rated titles related to the 'Harry Potter' book-series?

select count(distinct U.user_id)
FROM ratings R
INNER JOIN books B ON R.book_id = B.book_id
INNER JOIN users U ON R.user_id = U.user_id 
WHERE B.title LIKE '%Harry Potter%';
```
9. [ratings, books, users and locations]
- How many unique users have rated titles related to the 'Harry Potter' book-series. Break down your result by each country
```sql
-- How many unique users have rated titles related to the 'Harry Potter' book-series. Break down your result by each country

SELECT L.country, COUNT(DISTINCT U.user_id) AS 'Num_of_raters'
FROM ratings R
INNER JOIN books B ON R.book_id = B.book_id
INNER JOIN users U ON R.user_id = U.user_id 
INNER JOIN locations L ON U.location_id =L.location_id
WHERE B.title LIKE '%Harry Potter%'
group by L.country;
```
-- ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
10. [books and publishers]
- a. Write a query to display the book title, num_pages and publisher name for all books, including those with no publisher details
- b. Restrict your query to display only books with no publisher details
```sql
-- a. Write a query to display the book title, num_pages and publisher name for all books, including those with no publisher details

SELECT B.title, B.num_pages, P.publisher_name
FROM books B 
LEFT JOIN publishers P ON B.publisher_id = P.publisher_id;
```
```sql
-- b. Restrict your query to display only books with no publisher details

select * from books;
select *from publishers;
SELECT B.title, B.num_pages, P.publisher_name
FROM books B 
LEFT JOIN publishers P ON B.publisher_id = P.publisher_id
WHERE B.publisher_id is null;    
```
11. [books and authors]
- a. Write a query to display the book title, num_pages, publication_date, and authors for all books, including those with no author details
- b. Restrict your query to display only books with no author details
```sql
-- a. Write a query to display the book title, num_pages, publication_date, and authors for all books, including those with no author details

SELECT B.title, B.num_pages, B.publication_date, A.authors
FROM books B 
LEFT JOIN authors A ON B.author_id = A.author_id;
```
```sql
-- b. Restrict your query to display only books with no author details

SELECT B.title, B.num_pages, B.publication_date, A.authors
FROM books B 
LEFT JOIN authors A ON B.author_id = A.author_id
WHERE A.authors IS NULL;
```
12. [books and ratings]
-  How many books have never been rated
```sql
-- How many books have never been rated

SELECT COUNT(*) AS 'num_of_non_rated_books'
FROM books B
LEFT JOIN ratings R ON B.book_id = R.book_id
where R.rating is null;
```
