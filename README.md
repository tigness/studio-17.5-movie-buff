# studio-17.5-movie-buff

/* 1) List all movie titles */
SELECT *
FROM movies;

/* 2) List the title and year of each movie in the database in DESCENDING order of the year released. */
SELECT title, year_released
FROM movies
ORDER BY year_released DESC;

/* 3) List all columns for all records of the directors table in ascending alphabetical order based on the director’s country of origin. */
SELECT *
FROM directors
ORDER BY country ASC;

/* 4) List all columns for all records of the directors table in ascending alphabetical order first by the director’s country of origin and then by the director’s last name. */
SELECT * 
FROM directors
ORDER BY country, last_name ASC;

/* 5) Insert a new record into the directors table for Rob Reiner, an American film director. */
INSERT INTO directors (first_name,last_name,country)
VALUES("Rob","Reiner","USA");

/* 6) List the last name and director_id for Rob Reiner. */
SELECT last_name, director_id
FROM directors
WHERE (last_name="Reiner");

/* 7) Insert a new record into the movies table for The Princess Bride, which was released in 1987 and directed by Rob Reiner. */
INSERT INTO movies (title,year_released,director_id)
VALUES("The Princess Bride",1987,11);

/* 8) Use an inner join in your SQL command to display a list of movie titles, years released, and director last names. */
SELECT movies.title, movies.year_released, directors.last_name
FROM movies
INNER JOIN directors ON movies.director_id = directors.director_id;

/* 9) List all the movies in the database along with the first and last name of the director. Order the list alphabetically by the director’s last name. */
SELECT movies.title, directors.first_name, directors.last_name
FROM movies
INNER JOIN directors ON movies.director_id = directors.director_id
ORDER BY directors.last_name;

/* 10) Using WHERE, list the first and last name for the director of The Incredibles. */
SELECT directors.first_name, directors.last_name
FROM directors, movies
WHERE (directors.director_id=movies.director_id) AND (movies.title="The Incredibles");

/* 11) Using a join, list the last name and country of origin for the director of Roma. */
SELECT directors.last_name, directors.country
FROM directors
INNER JOIN movies ON directors.director_id=movies.director_id AND movies.title = "Roma";

/* 12) Delete a row from the movies table, then list the contents of both tables. */
DELETE FROM movies WHERE movie_id=6;
SELECT * FROM movies;
SELECT * FROM directors;

/* 13) Try to delete one person from the directors table. */
DELETE FROM directors WHERE director_id = 3;

/* Bonus Mission 1 */
SELECT movies.title AS Title, movies.year_released AS "Release Year", CONCAT(directors.first_name,' ',directors.last_name) AS Director
FROM movies
inner join directors on movies.director_id=directors.director_id
ORDER BY movies.title;

/* Bonus Mission 2 */

SELECT movies.title AS Title, movies.year_released AS "Release Year", CONCAT(directors.first_name,' ',directors.last_name) AS Director
FROM movies, directors
WHERE (directors.director_id=movies.director_id) AND (directors.first_name="Peter" AND directors.last_name="Jackson"); 

/* Bonus Mission 3 */
/* Part A */
ALTER TABLE movies
ADD boxOffice_inMillions double;

/* Part B */
UPDATE movies SET boxOffice_inMillions=1073 WHERE movie_id=1;
UPDATE movies SET boxOffice_inMillions=633 WHERE movie_id=2;
UPDATE movies SET boxOffice_inMillions=93.3 WHERE movie_id=3;
UPDATE movies SET boxOffice_inMillions=363.3 WHERE movie_id=4;
UPDATE movies SET boxOffice_inMillions=213.5 WHERE movie_id=5;
UPDATE movies SET boxOffice_inMillions=25 WHERE movie_id=7;
UPDATE movies SET boxOffice_inMillions=5.1 WHERE movie_id=8;
UPDATE movies SET boxOffice_inMillions=1.1 WHERE movie_id=9;
UPDATE movies SET boxOffice_inMillions=195.3 WHERE movie_id=10;
UPDATE movies SET boxOffice_inMillions=1142 WHERE movie_id=11;
UPDATE movies SET boxOffice_inMillions=133.4 WHERE movie_id=12;
UPDATE movies SET boxOffice_inMillions=821.8 WHERE movie_id=13;
UPDATE movies SET boxOffice_inMillions=620.7 WHERE movie_id=14;
UPDATE movies SET boxOffice_inMillions=1.9 WHERE movie_id=15;
UPDATE movies SET boxOffice_inMillions=66.8 WHERE movie_id=16;

/* Part C */
SELECT * FROM Movies ORDER BY boxOffice_inMillions DESC;

/* Part D */
SELECT * FROM MOVIES WHERE boxOffice_inMillions >= 200 ORDER BY boxOffice_inMillions DESC;
