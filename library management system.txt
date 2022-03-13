/*========== creating the database=================== */
CREATE SCHEMA `library_management_system`;

/* =======================creating the tables*===============/

CREATE TABLE `library_management_system`.`books` (
  `ID` INT NOT NULL AUTO_INCREMENT,
  `Name` VARCHAR(200) NOT NULL,
  `Author` VARCHAR(100) NOT NULL,
  `Year` INT NOT NULL,
  `Genre` VARCHAR(45) NOT NULL,
  `Price` DECIMAL(10,2) NOT NULL,
  `Available` INT NOT NULL,
  PRIMARY KEY (`ID`));

CREATE TABLE `library_management_system`.`borrowed` (
  `ID` INT NOT NULL AUTO_INCREMENT, 
  `Costumer_ID` INT NOT NULL,
  `Book_ID` INT NOT NULL,
  `Date_collected` DATETIME NOT NULL,
  `Due_date` DATETIME NOT NULL,
  `Date_returned` DATETIME,
 PRIMARY KEY (`ID`));

CREATE TABLE `library_management_system`.`costumer` (
  `ID` INT NOT NULL AUTO_INCREMENT,
  `Name` VARCHAR(100) NOT NULL,
  `DOB` DATE NOT NULL,
  `email` VARCHAR(200) NOT NULL,
  `Address` VARCHAR(250),
  `Subscription` VARCHAR(100) NOT NULL, 
 PRIMARY KEY (`ID`));

/*=======INSERTING INTO THE DATABASE==========*/

INSERT INTO `library_management_system`.`books` (`Name`, `Author`, `Year`, `Genre`, `Price`, `Available`)
 VALUES 
 ('Autobiography of Col. Richard Malcolm Johnston', 'Richard Malcolm Johnston', '1900', 'Autobiography', '12.53', '3'),
  ('Autobiography of Col. Richard BELLO Johnston', 'Richard Malcolm Johnston', '1900', 'Autobiography', '12.53', '3'),
  ('The Awakening', 'Kate Chopin', '1899', 'Fantasy', '7.99', '2'),
  ('Balcony Stories', 'Grace Elizabeth King', '1914', 'Fantasy', '11', '2'),
  ('The Battle-Ground', 'Ellen Anderson Gholson Glasgow', '1902', 'Fantasy', '11', '2'),
  ('Bayou Folk', 'Kate Chopin', '1894', 'history', '3.45', '4'),
  ('Cabbages and Kings', 'O. Henry', '1904', 'Young Adult', '6.52', '6'),
  ('Cannibals All! or, Slaves Without Masters', 'George  Fitzhugh', '1857', 'Fantasy', '11', '2'),
  ('The Colonels Dream', 'Charles Waddell Chesnutt', '1899', 'Drama', '6.00', '0'),
  ('The Conjure Woman', 'Charles Waddell Chesnutt', '1905', 'Fantasy', '12.99', '1');

INSERT INTO `library_management_system`.`consumer` (`Name`, `DOB`, `email`, `Address`, `Subscription`)
 VALUES ('Josh Williams', '2010-02-15', 'joshmcquillen1@gmail.com', 'NIL', 'weekly'),
 ('Brown Robert', '2006-03-14', 'robertseggel@gmail.com', 'NIL', 'annual'),
 ('Jones Hofstedar', '1997-02-25', 'Joneshofstedar@gmail.com', 'NIL', 'monthly'),
 ('Garcia Holmes', '2002-01-13', 'cj428hughes@gmail.com', 'NIL', 'monthly'),
 ('Miller Hughes', '2004-04-13', 'jkolar777@gmail.com', 'NIL', 'weekly'),
 ('Davis Sheldon', '1999-08-15', 'kcirvam33@gmail.com', 'NIL', 'annual'),
 ('Penny Hernandez', '2003-08-23', 'mmcintyre44@gmail.com', 'NIL', 'annual'),
 ('Alicia Martinez', '1997-06-01', 'trudgen@hotmail.com', 'NIL', 'none'),
 ('Josper Rodriguez', '1993-05-25', 'adina1977@hotmail.com', 'NIL', 'monthly'),
 ('Johnson Nesh', '1988-06-20', 'neshpayer@gmail.com', 'NIL', 'none');

INSERT INTO `library_management_system`.`borrowed` (`Costumer_ID`, `Book_ID`, `Date_collected`, `Due_date`,)
 VALUES ('2', '5', '2022-03-12 10:10:11', NOW(), '2022-03-16 12:10:11'),
('3', '2', NOW(), NOW(), '2022-03-16 12:10:11'),
('1', '3', '2022-03-12 10:10:11', NOW(), '2022-03-16 12:10:11'),
('2', '1', '2022-03-12 10:10:11', NOW(), '2022-03-16 12:10:11'),
('10', '4', '2022-03-12 10:10:11', NOW(), '2022-03-16 12:10:11'),
('5', '3', '2022-03-12 10:10:11', '2022-03-12 06:10:11', '2022-03-12 06:10:11'),
('7', '1', '2022-03-12 10:10:11', '2022-03-12 13:10:11', '2022-03-12 13:10:11'),
('6', '10', NOW(), '2022-03-12 10:10:11', '2022-03-12 13:10:11'),
('4', '1', '2022-03-12 10:10:11', '2022-02-22 10:14:11', '2022-03-12 10:10:11'),
('7', '3', '2022-03-12 10:10:11', '2022-03-14 15:55:11', '2022-03-12 10:10:11'),
('9', '6', '2022-03-12 10:10:11', '2022-03-12 22:12:11', '2022-03-12 22:12:11'),
('8', '7', NOW(), '2022-03-16 12:10:11', '2022-03-16 12:10:11'),
('1', '9', '2022-03-12 10:10:11', '2022-03-16 12:10:11', '2022-03-16 12:10:11'),
('3', '4', '2022-03-12 10:10:11', '2022-03-19 11:10:11', '2022-03-19 11:10:11'),
('6', '9', '2022-03-12 10:10:11', '2022-03-12 01:10:11', '2022-03-12 01:10:11'),
('7', '6', '2022-03-12 10:10:11', '2022-03-22 07:10:11', '2022-03-22 07:10:11'),
('9', '4', NOW(), '2022-03-22 10:10:11', '2022-03-22 10:10:11'),
('10', '7', '2022-03-12 10:10:11', '2022-03-22 09:10:11', '2022-03-22 09:10:11'),
('4', '3', '2022-03-12 10:10:11', '2022-03-22 11:10:11', '2022-03-22 11:10:11'),
('5', '6', NOW(), '2022-03-12 10:10:11', '2022-03-12 10:10:11');

/*===============Creating Queries================*/

/*search for books, based on the author and name of book, alphabetically, genre.*/

SELECT * FROM `library_management_system`.`books` 
WHERE MATCH(`Author`, `Name`, `Genre`) AGAINST(?) 
ORDER BY `Name` DESC

/*records of a particular person in the library.*/

SELECT `costumer`.`Name`, `costumer`.`email`, `costumer`.`Address`, `costumer`.`Subscription`, `books`.`Name`, `books`.`Author`, `borrowed`.`Date_collected`, `borrowed`.`Date_returned`
 FROM `library_management_system`.`costumer` JOIN `library_management_system`.`borrowed` 
ON costumer.ID = borrowed.Costumer_ID
JOIN `library_management_system`.`books` 
ON borrowed.Book_ID = books.ID
where costumer.Name = ?

/*what books are available*/

SELECT `books`.`Name`, `books`.`Genre`, `books`.`Author`, `books`.`Available`
FROM `library_management_system`.`books` 
WHERE MATCH(`Author`, `Name`, `Genre`) AGAINST('Richard') 
AND `books`.`Available` > 1
ORDER BY `Name` DESC

/*========================NOTE================*/

ALTER TABLE `library_management_system`.`books` 
ADD FULLTEXT INDEX `author_genre_name` (`Author`, `Name`, `Genre`) VISIBLE;
****************************************************************************

ALTER TABLE `library_management_system`.`costumer` 
ADD CONSTRAINT `costumer id`
  FOREIGN KEY (`ID`)
  REFERENCES `library_management_system`.`borrowed` (`ID`)
  ON DELETE NO ACTION
  ON UPDATE NO ACTION;
***************************************************************************

ALTER TABLE `library_management_system`.`books` 
ADD CONSTRAINT `booksid`
  FOREIGN KEY (`ID`)
  REFERENCES `library_management_system`.`borrowed` (`ID`)
  ON DELETE NO ACTION
  ON UPDATE NO ACTION;


