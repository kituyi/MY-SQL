# MY-SQL
CREATIND DATABASE
USE record_company;

CREATE TABLE bands (
	id INT NOT NULL AUTO_INCREMENT,
	name VARCHAR(255) NOT NULL,
  id INT NOT NULL AUTO_INCREMENT,
  name VARCHAR(255) NOT NULL,
  PRIMARY KEY (id)
);

CREATE TABLE albums (
	id INT NOT NULL AUTO_INCREMENT,
  id INT NOT NULL AUTO_INCREMENT,
  name VARCHAR(255) NOT NULL,
  release_year INT,
  band_id INT NOT NULL,
 2  solutions/1.sql 
@@ -1,5 +1,5 @@
CREATE TABLE songs (
	id INT NOT NULL AUTO_INCREMENT,
  id INT NOT NULL AUTO_INCREMENT,
  name VARCHAR(255) NOT NULL,
  length FLOAT NOT NULL,
  album_id INT NOT NULL,
 2  solutions/10.sql 
@@ -1,2 +1,2 @@
SELECT AVG(length) as 'Average Song Length'
SELECT AVG(length) as 'Average Song Duration'
FROM songs; 
 2  solutions/11.sql 
@@ -1,5 +1,5 @@
SELECT
	albums.name AS 'Album',
  albums.name AS 'Album',
  albums.release_year AS 'Release Year',
  MAX(songs.length) AS 'Duration'
FROM albums
 2  solutions/12.sql 
@@ -1,5 +1,5 @@
SELECT
	bands.name AS 'Band',
  bands.name AS 'Band',
  COUNT(songs.id) AS 'Number of Songs'
FROM bands
JOIN albums ON bands.id = albums.band_id
 13  solutions/4.sql 
@@ -1,3 +1,14 @@

/* This assummes all bands have a unique name */
SELECT DISTINCT bands.name AS 'Band Name'
FROM bands
JOIN albums ON bands.id = albums.band_id; 
JOIN albums ON bands.id = albums.band_id;

/* If bands do not have a unique name then use this query */
/* 
  SELECT bands.name AS 'Band Name'
  FROM bands
  JOIN albums ON bands.id = albums.band_id
  GROUP BY albums.band_id
  HAVING COUNT(albums.id) > 0;
*/ 
 2  solutions/5.sql 
@@ -1,4 +1,4 @@
SELECT DISTINCT bands.name AS 'Band Name'
SELECT bands.name AS 'Band Name'
FROM bands
LEFT JOIN albums ON bands.id = albums.band_id
GROUP BY albums.band_id
 2  solutions/6.sql 
@@ -1,5 +1,5 @@
SELECT
	albums.name as Name,
  albums.name as Name,
  albums.release_year as 'Release Year',
  SUM(songs.length) as 'Duration'
FROM albums
 4  solutions/7.sql 
@@ -1,5 +1,7 @@
/* This is the query used to get the id */
/* SELECT * FROM albums where release_year IS NULL; */
/*
  SELECT * FROM albums where release_year IS NULL;
*/

UPDATE albums
SET release_year = 1986
  6  solutions/8.sql 
@@ -2,8 +2,10 @@ INSERT INTO bands (name)
VALUES ('Favorite Band Name');

/* This is the query used to get the band id of the band just added */
/* SELECT id FROM bands
ORDER BY id DESC LIMIT 1; */
/*
  SELECT id FROM bands
  ORDER BY id DESC LIMIT 1;
*/

INSERT INTO albums (name, release_year, band_id)
VALUES ('Favorite Album Name', 2000, 8); 
 12  solutions/9.sql 
@@ -1,13 +1,17 @@
/* This is the query used to get the album id of the album added in #8 */
/* SELECT id FROM albums
ORDER BY id DESC LIMIT 1; */
/*
  SELECT id FROM albums
  ORDER BY id DESC LIMIT 1;
*/

DELETE FROM albums
WHERE id = 19;

/* This is the query used to get the band id of the band added in #8 */
/* SELECT id FROM bands
ORDER BY id DESC LIMIT 1; */
/*
  SELECT id FROM bands
  ORDER BY id DESC LIMIT 1;
*/

DELETE FROM bands
WHERE id = 8; 
