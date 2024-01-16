
-- <<< Zadania z kursu UDEMY SQL bootcamp >>> --

/* kolejność zapytań
SELECT (DISTINCT), FROM, WHERE, ORDER BY (DESC), LIMIT, OFFSET 
*/

CREATE TABLE pracownicy (
id INT AUTO_INCREMENT PRIMARY KEY,
first_name VARCHAR(25) NOT NULL,
last_name VARCHAR(25) NOT NULL,
middle_name VARCHAR(25),
age INT NOT NULL,
current_status VARCHAR(25) NOT NULL DEFAULT 'employed');

-- AS, WHERE --
SELECT cat_id, age FROM cats WHERE cat_id=age; -- można za pomocą WHERE porównywać kolumny
SELECT name AS imie FROM cats; -- użycie aliasa
SELECT name AS imie FROM cats AS kotki; -- można też tabele aliasować

-- /// UPDATE-SET-WHERE, aktualizowanie wpisów \\\ --
UPDATE cats SET col=val, another_col=val WHERE name='tabby';
 
--!!! zanim zrobię UPDATE, dobrym nawykiem jest najpierw sprawdzić za pomocą SELECT dany WHERE, czy aby na pewno jeden wiersz modyfikuję, czyli:
SELECT * FROM cats WHERE name='Tabby';
UPDATE cats SET name='Klakier' WHERE name='Tabby';

-- DELETE FROM --
DELETE FROM tabela WHERE kolumna=wartość;
DELETE FROM tabela; -- kasuje zawartość całej tabeli

-- CREATE DATABASE, TABLE --
CREATE DATABASE shirts_db;
USE shirts_db;
CREATE TABLE shirts (
shirt_id INT AUTO_INCREMENT PRIMARY KEY,
article VARCHAR(20) NOT NULL DEFAULT 't-shirt',
color VARCHAR(20) NOT NULL,
shirt_size VARCHAR(5) NOT NULL,
last_worn INT);

-- INSERT INTO --
INSERT INTO shirts (article, color, shirt_size, last_worn) VALUES 
('t-shirt', 'white', 'S', 10),
('t-shirt', 'green', 'S', 200),
('polo shirt', 'black', 'M', 10),
('tank top', 'blue', 'S', 50),
('t-shirt', 'pink', 'S', 0),
('polo shirt', 'red', 'M', 5),
('tank top', 'white', 'S', 200),
('tank top', 'blue', 'M', 15);

source nazwa_pliku.sql -- w mysql w terminalu, można zaczytywać w ten sposób gotowe pliki z tabelami

-- STRING functions --

SELECT CONCAT(author_fname, ' ', author_lname) AS full_name FROM books;
SELECT CONCAT_WS(' * ', author_fname, author_lname) AS full_name FROM books;
SELECT book_id AS Lp, CONCAT_WS(' /\\ ', author_fname, author_lname) AS full_name FROM books;

SELECT SUBSTRING('EXTRAORDINARY', 5); -- wyświetli wszsytkie znaki zaczynając od piątego
SELECT SUBSTRING('EXTRAORDINARY', 1, 5); -- wyświetli pierwsze pięć znaków
SELECT SUBSTRING('EXTRAORDINARY', -6, 6); -- wyświetli sześć znaków od końca
SELECT SUBSTRING(author_fname, 1, 1) AS initalF, SUBSTRING(author_lname, 1, 1) AS initalL, CONCAT(author_fname, ' ', author_lname) AS fullName FROM books;
SELECT SUBSTR -- skrót
SELECT CONCAT(SUBSTR(title, 1, 11), '...') AS short_title FROM books;
SELECT CONCAT(author_fname, ' ', author_lname) AS fullname, CONCAT(SUBSTR(author_fname, 1, 1), '.', SUBSTR(author_lname, 1, 1), '.') AS initials FROM books;

SELECT REPLACE(string, from_string, to_string); -- funkcja zawiera trzy wartości, co chcę zmienić, jaki element, na co; FUNKCJA niczego nie zmienia w tabelach!
SELECT REPLACE('cheese bread coffee milk', ' ', ' and '); -- w puste miejsca wstawi napis 'and'
SELECT REPLACE(title, ' ', ' + ') FROM books;

SELECT REVERSE('Hello world'); -- odczyta w odwrotnej kolejności
SELECT REVERSE(title) FROM books;
SELECT CONCAT(author_fname, '/\\', REVERSE(author_fname)) FROM books;

/*
CHAR_LENGTH -- wyświetli długość łańcucha w znakach
LENGTH -- wyświetli "wagę" łańcucha w bajtach
*/
SELECT CHAR_LENGTH('Hello World');
SELECT CHAR_LENGTH(title) AS length, title FROM books;
SELECT CONCAT(author_lname, ' is ', CHAR_LENGTH(author_lname), ' characters long') FROM books;

SELECT LOWER/UPPER lub LCASE/UCASE -- zamienia znaki na małe lub duże
SELECT UPPER(title) FROM books;
SELECT CONCAT('I LOVE ', UPPER(title), ' !!!') AS okrzyk FROM books;

SELECT INSERT('Zaniepokojenie', 3, 4, 'what') -- od trzeciego znaku, usunie cztery i wstawi 'what'
SELECT INSERT('Hello Pawel', 5, 0, ' there'); -- nie usunie znaków, wstawi wyraz
SELECT LEFT/RIGHT('rebranding', 4); -- wyświetli ilość znaków od lewej lub prawej
SELECT REPEAT('ha', 4);
SELECT TRIM(LEADING/TRAILNG/BOTH 'znak')

-- /// zadania \\\ --
SELECT REVERSE(UPPER('Why does my cat look at me with such hatred?'));
SELECT REPLACE(CONCAT('I', ' ', 'like', ' ', 'cats'), ' ', '-');
SELECT REPLACE(title, ' ', '->') AS title FROM books;
SELECT author_lname AS forwards, REVERSE(author_lname) AS backwards FROM books;
SELECT CONCAT(UPPER(author_fname), ' ', UPPER(author_lname)) AS 'full name in caps' FROM books;
SELECT CONCAT(title, ' was released in ', released_year) AS blurb FROM books;
SELECT title, CHAR_LENGTH(title) AS 'character count' FROM books;

SELECT
   CONCAT(SUBSTR(title, 1, 10), '...') AS short_title,
   CONCAT(author_lname, ',', author_fname) AS author,
   CONCAT(stock_quantity, ' in stock') AS quantity
 FROM
   books;


-- DISTINCT --
SELECT DISTINCT column FROM table; -- wyświetla niepowtarzalne kombinacje wierszy

-- ORDER BY --
ORDER BY (column, column) (nr_column) (DESC); -- zawsze na końcu zapytania, nr_column: gdy podamy kilka kolumn,określamy wg której z nich porządkować
SELECT book_id, author_fname, author_lname FROM books ORDER BY author_lname;
SELECT CONCAT(author_fname, ' ', author_lname) AS author FROM books ORDER BY author; -- można sortować wg aliasa

-- LIMIT --
LIMIT 0, 5; -- pierwsza cyfra oznacza odkąd ma zaczynać(opcjonalnie), a druga ile wpisów wyświetlić; po ORDER BY
SELECT title, released_year FROM books ORDER BY released_year DESC LIMIT 10;

-- LIKE --
WHERE column LIKE '_a_' / 'da%' / '____' ; -- '%' wildcard, zero lub jakakolwiek liczba znaków; '_' dokładnie jeden znak
LIKE '%\%%' /  '%\_%'; -- znak ucieczki \ pozwala użyć znaków % i _

-- /// zadania \\\ --
SELECT title FROM books WHERE title LIKE '%stories%';
SELECT title, pages FROM books ORDER BY pages DESC LIMIT 1;
SELECT CONCAT(title, ' - ', released_year) AS summary FROM books ORDER BY released_year DESC LIMIT 3;
SELECT title, author_lname FROM books WHERE author_lname LIKE '% %';
SELECT title, released_year, stock_quantity FROM books ORDER BY stock_quantity, title LIMIT 3;
SELECT title, author_lname FROM books ORDER BY author_lname, title;
SELECT UPPER(CONCAT('my favourite author is ', author_fname, ' ', author_lname, '!')) AS yell FROM books ORDER BY author_lname;


-- ////// UWAGA! \\\\\\ --
-- TU SIĘ ZACZYNAJĄ SCHODY !!! --
 
-- COUNT (*) -- zwraca ilość wierszy z tabeli, także pustych
SELECT COUNT(*) FROM books;
SELECT COUNT(DISTINCT author_fname) FROM books;
SELECT COUNT(*) FROM books WHERE title LIKE '%the%'; -- zwróci ilość wierszy zawierających 'the'z tabeli books

-- GROUP BY -- grupuje powtarzające się wpisy do jednego wiersza, zwykle używa się z funkcjami COUNT, MIN, MAX, SUM, AVG
SELECT author_lname, COUNT(*) FROM books GROUP BY author_lname;
SELECT author_lname, COUNT(*) AS books_written FROM books GROUP BY author_lname ORDER BY books_written DESC;
SELECT author_fname, author_lname, COUNT(*) FROM books GROUP BY author_lname, author_fname;
SELECT CONCAT(author_fname, ' ', author_lname) AS author, COUNT(*) FROM books GROUP BY author; 

-- MIN MAX -- zwraca wartość, także alfabetyczną
SELECT MAX(pages) FROM books;
SELECT MIN(author_lname) FROM books;

-- Sub query -- zagnieżdzanie zapytania
SELECT title, pages FROM books 
WHERE pages = (SELECT MAX(pages) FROM books);

SELECT title, released_year FROM books 
WHERE released_year = (SELECT MIN(released_year) FROM books);

-- MIN MAX + GROUP BY
SELECT author_lname, MIN(released_year) FROM books GROUP BY author_lname;
SELECT author_lname, MAX(released_year), MIN(released_year) FROM books GROUP BY author_lname;

SELECT
	author_lname,
	COUNT(*) as books_written,
	MAX(released_year) AS latest_release,
	MIN(released_year) AS earliest_release,
	MAX(pages) AS longest_page_count
FROM books GROUP BY author_lname;

-- SUM -- sumowanie(tylko liczby)
 SELECT SUM(pages) FROM books;
 SELECT author_lname, COUNT(*), SUM(pages) FROM books GROUP BY author_lname;

-- AVG -- average, średnia
SELECT AVG(pages) FROM books;
SELECT AVG(released_year) FROM books;
SELECT released_year, AVG(stock_quantity), COUNT(*) FROM books GROUP BY released_year;

-- ///=== zadania ===\\\ --
SELECT COUNT(title) FROM books WHERE title IS NOT NULL;
SELECT released_year, COUNT(*) AS number_released FROM books GROUP BY released_year ORDER BY released_year DESC;
SELECT SUM(stock_quantity) AS all_books FROM books;
SELECT CONCAT(author_fname, ' ', author_lname) AS author, AVG(released_year) FROM books GROUP BY author;
SELECT CONCAT(author_fname, ' ', author_lname) AS author, pages FROM books WHERE pages=(SELECT MAX(pages) FROM books) GROUP BY author, pages ORDER BY author;
SELECT released_year AS year, COUNT(*) AS '# books', AVG(pages) AS 'avg pages' FROM books GROUP BY year ORDER BY year;

-- DATA TYPES zaawansowane --

-- CHAR vs VARCHAR --
/*
CHAR(wielkość 0-255) - zawsze zużywa ilość podanego miejsca na znaki(doda białe znaki, któych nie widać, jeśli podamy mniejszy wyraz niż wielkość danej)
CHAR is faster for fixed length text(np. zip codes, yes/no Y/N, skróty)
VARCHAR(wielkość 0-65 535) - zużywa tyle miejsca ile podamy,ale finalnie może być nieefektywne i zabierać więcej bajtów
*/

-- TINYINT, SMALLINT, MEDIUMINT, INT, BIGINT --
-- TYLKO LICZBY CAŁKOWITE --
/*
TINYINT(wielkość -128 do 128)
SMALLINT(wielkość -32768 do 32768) 
MEDIUMINT(wielkość -8388608 do 8388608)
INT(wielkość -2147483648 do 2147483648)
BIGINT(wielkość -2do63 do 2do63-1) 
*/
-- SIGNED(domyślnie) lub UNSIGNED(bez ujemnych) np.:
CREATE TABLE parents (children TINYINT UNSIGNED);

-- DECIMAL --
-- DECIMAL(5,2); -- pierwsza cyfra oznacza całkowitą ilość cyfr w liczbie, a druga ilość miejsc po przecinku, czyli np. 111,11

-- FLOAT(4 bajty) and DOUBLE(8 bajtów) --
/* zabierają mniej miejsca od DECIMAL ale są mniej dokładne */

-- DATE and TIME --
-- DATE 'YYYY-MM-DD' format
-- TIME 'HH:MM:SS' format
-- DATETIME 'YYYY-MM-DD HH:MM:SS' format
INSERT INTO people (name, birthdate, birthtime, birthdt) VALUES ('Juan', '2020-08-15', '23:59:00', '2020-08-15 23:59:00');

SELECT CURRENT_TIME(); -- CURTIME()
SELECT CURRENT_DATE(); -- CURDATE()
SELECT NOW(); -- CURRENT_TIMESTAMP()
INSERT INTO people (name, birthdate, birthtime, birthdt) VALUES ('Hazel', CURDATE(), CURTIME(), NOW());

-- ///DATE functions\\\ --
-- DAY(date)
-- YEAR(date)
-- DAYOFWEEK(date)
-- DAYOFYEAR(date)
-- MONTHNAME(date)
-- DAYNAME(date)
SELECT name, birthdt, DAYNAME(birthdt), MONTHNAME(birthdt), DAYOFYEAR(birthdt) FROM people;
SELECT name, birthtime, HOUR(birthtime), MINUTE(birthtime), SECOND(birthtime) FROM people;

--DATE FORMAT --
SELECT birthdate, DATE_FORMAT(birthdate, '%a, %b, %c, ...') FROM people;

-- DATE math --
DATEDIFF -- oblicza różnicę między datami
SELECT birthdate, DATEDIFF(CURDATE(), birthdate) FROM people;

-- DATE_ADD, DATE_SUB --
DATE_ADD(date, INTERVAL 5 YEAR)
DATE_SUB(date, INTERVAL 5 YEAR)

SELECT birthdate, DATE_ADD(birthdate, INTERVAL 18 YEAR) FROM people;
SELECT TIMEDIFF(CURTIME(), '6:00:00');
SELECT name, birthdate, birthdate + INTERVAL 21 YEAR FROM people;
SELECT name, birthdate, YEAR(birthdate + INTERVAL 21 YEAR) AS 'will be 21' FROM people;

-- DEFAULT & ON UPDATE
CREATE TABLE captions (
text VARCHAR(150), 
created_at TIMESTAMP default CURRENT_TIMESTAMP, 
updated_at TIMESTAMP ON UPDATE CURRENT_TIMESTAMP);
-- TIMESTAMP -- lżejszy, z ograniczoną rozpiętością dat, używany najczęściej do aktualnych zdarzeń np. instagram, facebook, youtube

-- //== zadania ==\\ --
SELECT DATE_FORMAT(NOW(), '%c/%d/%Y');
SELECT DAY(NOW());
SELECT DAYOFWEEK(NOW());
SELECT DAYNAME(NOW());
SELECT DATE_FORMAT(NOW(), '%M %D at %H:%i');

--/// LOGICAL OPERATORS \\\--
> , <, <=, >=, =
!=, <>
-- NOT LIKE
SELECT * FROM books WHERE title NOT LIKE '%e%';
SELECT * FROM books WHERE released_year <= 2000;

-- AND 
SELECT title, author_lname, released_year FROM books WHERE released_year > 2010 AND author_lname ='Eggers' AND title LIKE '%novel%';

-- OR
SELECT title, author_lname, released_year FROM books WHERE author_lname='Eggers' OR released_year > 2010;
SELECT title, pages FROM books WHERE CHAR_LENGTH(title) > 30 AND pages > 500;

-- BETWEEN
SELECT title, released_year FROM books WHERE released_year <= 2015 AND released_year >= 2004; -- zamiast BETWEEN
SELECT title, released_year FROM books WHERE released_year BETWEEN 2004 AND 2014;
SELECT title, pages FROM books WHERE pages NOT BETWEEN 200 AND 300;

-- Comparing dates --
-- CAST zamieniamy string na inny typ danych
SELECT * FROM people WHERE birthtime BETWEEN CAST('12:00:00' AS TIME) AND CAST('16:00:00' AS TIME);
SELECT * FROM people WHERE HOUR(birthtime) BETWEEN 12 AND 16;

-- IN
SELECT title, author_lname FROM books WHERE author_lname IN ('Carver', 'Lahiri', 'Smith'); -- działa tak samo jak OR
SELECT title, author_lname FROM books WHERE author_lname NOT IN ('Carver', 'Lahiri', 'Smith');
SELECT title, released_year FROM books WHERE released_year >= 2000 AND released_year % 2 = 1; -- '%'(modulo) to reszta z dzielenia

-- CASE (WHEN, THEN, ELSE, END) --
SELECT title, released_year,
CASE
	WHEN released_year >= 2000 THEN 'modern lit' -- CASE służy do zamieniania wartości w kolumnach na inne, tymczasowo oczywiście
	ELSE '20th century lit'
END AS genre 
FROM books;

SELECT title, stock_quantity,
CASE
	WHEN stock_quantity BETWEEN 0 AND 40 THEN '*'
	WHEN stock_quantity BETWEEN 41 AND 70 THEN '**'
	WHEN stock_quantity BETWEEN 71 AND 100 THEN '***'
	WHEN stock_quantity BETWEEN 101 AND 140 THEN '****'
	ELSE '*****'
END AS stock
FROM books;

SELECT title, stock_quantity,
CASE
	WHEN stock_quantity <= 40 THEN '*'
	WHEN stock_quantity <= 70 THEN '**'
	WHEN stock_quantity <= 100 THEN '***'
	WHEN stock_quantity <= 140 THEN '****'
	ELSE '*****'
END AS stock
FROM books;

-- Zamiana wartości w danej kolumnie, ważne aby po CASE określić kolumnę!
CASE First_name	-- określenie w jakiej kolumnie działamy!
        WHEN 'Bob' THEN Salary * 0.2
        WHEN 'Alex' THEN Salary * 0.1
        ELSE Salary * 0.15
    END AS req_amount
    FROM Employee;

-- IS NULL, IS NOT NULL --
SELECT * FROM books WHERE author_lname IS NULL;
SELECT * FROM books WHERE author_lname IS NOT NULL;

-- ///=== zadania ===\\\ --
SELECT title, released_year FROM books WHERE released_year < 1980;
SELECT title, author_lname FROM books WHERE author_lname='Eggers' OR author_lname='Chabon';
SELECT title, author_lname FROM books WHERE author_lname IN('Eggers', 'Chabon');
SELECT title, author_lname, released_year FROM books WHERE author_lname='Lahiri' AND released_year > 2000;
SELECT title, pages FROM books WHERE pages>100 AND pages<200 ;
SELECT title, pages FROM books WHERE pages BETWEEN 100 AND 200;
SELECT author_lname FROM books WHERE author_lname LIKE 'C%' OR author_lname LIKE 'S%';
SELECT title, author_lname FROM books WHERE SUBSTR(author_lname, 1, 1) in ('C', 'S'); 
SELECT title, author_lname, 
CASE
    WHEN title LIKE '%stories%' THEN 'Short stories' -- CASE służy do zamieniania wartości w kolumnach na inne, tymczasowo oczywiście
    WHEN title = 'Just Kids' OR title LIKE '%A heartbreaking%' THEN 'Memoir'
    ELSE 'Novel'
END AS Type
FROM books;

SELECT
  author_fname,
  author_lname,
  CONCAT(
    COUNT(*), ' ',
    CASE
      WHEN COUNT(*) = 1 THEN 'book'
      ELSE 'books'
    END
  ) AS 'count'
FROM
  books
GROUP BY
  author_fname,
  author_lname;

-- CONSTRAINTS czyli ograniczenia w wartościach VALUES --
  
-- UNIQUE --
CREATE TABLE contacts (
	name VARCHAR(100) NOT NULL,
	phone VARCHAR(15) NOT NULL UNIQUE -- nie pozwoli utworzyć drugiego wpisu z tą samą wartością
);

-- CHECK --
CREATE TABLE users (
	username VARCHAR(100) NOT NULL,
	age INT CHECK (age > 18) -- wpisana wartość musi być większa od 18
);
CREATE TABLE palindromes (
	word VARCHAR(100) CHECK(REVERSE(word) = word)
);

-- naming constraints --
CREATE TABLE users (
	username VARCHAR(100) NOT NULL,
	age INT, 
	CONSTRAINT is_adult CHECK (age >= 18) 
);

-- multiple columns constraints --
CREATE TABLE companies (
	name VARCHAR(255) NOT NULL,
	address VARCHAR(255) NOT NULL,
	CONSTRAINT name_address UNIQUE (name, address) -- musi być unikalna kombinacja 
);

CREATE TABLE houses (
	purchase_price INT NOT NULL,
	sale_price INT NOT NULL,
	CONSTRAINT sprice_greaterthan_pprice CHECK(sale_price >= purchase_price) -- także dwie kolumny sprawdza
);

-- ALTER TABLE --
ALTER TABLE companies 
	ADD COLUMN phone VARCHAR(15), -- COLUMN jest opcjonalne
	ADD employee_count INT NOT NULL DEFAULT 1;

-- DROP COLUMN --
ALTER TABLE companies
	DROP COLUMN phone;

-- Renaming tables and columns --
RENAME TABLE companies TO suppliers;

ALTER TABLE suppliers 
	RENAME TO companies;

ALTER TABLE companies
	RENAME COLUMN name TO company_name;

-- CHANGE and MODIFY column --
ALTER TABLE companies	
	MODIFY company_name VARCHAR(100) DEFAULT 'unknown'; -- zmieniamy typ danych w kolumnie, warto najpierw sprawdzić np. DESCRIBE zanim zmienimy

ALTER TABLE suppliers	
	CHANGE business biz_name VARCHAR(50); -- zmiana jednocześnie nazwy kolumny(z 'business' na 'biz_name') jak i jej typu danych

-- ADDING CONSTRAINT to an existing table --
ALTER TABLE houses 
	ADD CONSTRAINT positive_pprice CHECK (purchase_price >= 0);

ALTER TABLE houses DROP CONSTRAINT positive_pprice;

-- ///=== PRIMARY and FOREIGN KEYS ==\\\--

 CREATE TABLE customers (
        id INT PRIMARY KEY AUTO_INCREMENT, -- klucz główny
        first_name VARCHAR(50),
        last_name VARCHAR(50),
        email VARCHAR(50)
    );
     
CREATE TABLE orders (
        id INT PRIMARY KEY AUTO_INCREMENT, -- klucz główny
        order_date DATE,
        amount DECIMAL(8,2),
        customer_id INT,
        FOREIGN KEY (customer_id) REFERENCES customers(id) -- ustalenie klucza obcego
    );

-- JOINS --

-- łopatologiczne szukanie zamówień klienta o nazwisku 'George':
SELECT id FROM customers WHERE last_name = 'George';
SELECT * FROM orders WHERE customer_id=1;
-- trochę lepsze szukanie w jednym zapytaniu:
SELECT * FROM orders WHERE customer_id = (SELECT id FROM customers WHERE last_name = 'George');

-- CROSS JOIN:
SELECT * FROM customers, orders; -- raczej bezużyteczny join, tworzy wszystkie możliwe kombinacje wierszy z obu tabel

-- INNER JOIN:
 SELECT * FROM customers JOIN orders ON orders.customer_id = customers.id; -- łączymy miejsca które mają sens by połączyć, czyli klucze
-- grupowanie i sumowanie:
SELECT
		first_name,
		last_name,
		SUM(amount) AS total -- w select można korzystać z kolumn z obu tabel(lub więcej jeśli są)
		customers
		JOIN orders ON orders.customer_id = customers.id
	GROUP BY
		first_name,
		last_name
	ORDER BY
		total; -- dzięki temu zapytaniu widać sumę wszystkich zamówień danego klienta

-- LEFT JOIN: (pobiera wszystkie wpisy z lewej tabeli(nawet te, które nie mają jeszcze korespondujących w prawej tabeli) wraz z pokrywającymi się wpisami z prawej tabeli)
SELECT
		first_name,
		last_name,
		order_date,
		amount
	FROM
		customers -- to jest lewa strona, ta będzie pobrana cała, czyli customers
	LEFT JOIN orders -- to jest prawa strona
	ON orders.customer_id = customers.id; 

-- GROUP BY z IFNULL:
SELECT
		first_name,
		last_name,
		IFNULL(SUM(amount), 0) AS 'money spent' -- jeśli w wyniku pojawią się nulle, zamień na 0
	FROM
		customers
		LEFT JOIN orders ON orders.customer_id = customers.id
GROUP BY
	first_name,
	last_name;

-- RIGHT JOIN: (analogicznie, pobiera wszystko z prawej tabeli)
SELECT
		first_name,
		last_name,
		order_date,
		amount
	FROM
		customers -- to jest lewa strona
	RIGHT JOIN orders -- to jest prawa strona, ta będzie pobrana cała, czyli orders
	ON orders.customer_id = customers.id; 

-- ON DELETE CASCADE: (usuwanie wpisów wraz z połączonymi foreign key wpisami w innej tabeli)
DELETE FROM customers WHERE last_name='George'; -- to nie pozwoli usunąć, gdyż jest 'parent row'
-- w tej sytuacji możemy zrobić UPDATE customer'a na NULL(i zostawić jego zamówienia w bazie) lub wcześniej przy tworzeniu tabeli to:
CREATE TABLE orders (
        id INT PRIMARY KEY AUTO_INCREMENT, -- klucz główny
        order_date DATE,
        amount DECIMAL(8,2),
        customer_id INT,
        FOREIGN KEY (customer_id) REFERENCES customers(id) ON DELETE CASCADE-- pozwoli usunąć customer wraz z jego zamówieniami
    );

-- //= ZADANIA =\\ --
CREATE DATABASE dziennik;

USE dziennik;

CREATE TABLE students (
	id INT PRIMARY KEY AUTO_INCREMENT,
	first_name VARCHAR(20)
);

CREATE TABLE papers (
	title VARCHAR(100),
	grade TINYINT UNSIGNED,
	student_id INT,
	FOREIGN KEY (student_id) REFERENCES students(id) ON DELETE CASCADE 
);

SELECT first_name, title, grade FROM students RIGHT JOIN papers ON students.id = papers.student_id ORDER BY grade DESC;

SELECT first_name, title, grade FROM students LEFT JOIN papers ON students.id = papers.student_id;

SELECT first_name, IFNULL(title, 'MISSING'), IFNULL(grade, 0) FROM students LEFT JOIN papers ON students.id = papers.student_id;

SELECT
	first_name,
	IFNULL(AVG(grade), 0) AS average
FROM
	students
	LEFT JOIN papers ON students.id = papers.student_id
GROUP BY
	first_name
ORDER BY
	average DESC;

SELECT
	first_name,
	IFNULL(AVG(grade), 0) AS average,
	CASE 
		WHEN IFNULL(AVG(grade), 0) < 75 THEN 'FAILING'
		ELSE 'PASSING'
		END AS 'passing_status'
FROM
	students
	LEFT JOIN papers ON students.id = papers.student_id
GROUP BY
	first_name
ORDER BY
	average DESC;


-- ///=== MANY to MANY joins ===\\\ --

CREATE DATABASE tv_db;
USE tv_db;

CREATE TABLE reviewers (
	id INT PRIMARY KEY AUTO_INCREMENT,
	first_name VARCHAR(50) NOT NULL,
	last_name VARCHAR(50) NOT NULL
);

CREATE TABLE series (
	id INT PRIMARY KEY AUTO_INCREMENT,
	title VARCHAR(100),
	released_year YEAR,
	genre VARCHAR(100)
);

CREATE TABLE reviews (
	id INT PRIMARY KEY AUTO_INCREMENT,
	rating DECIMAL(2,1),
	series_id INT,
	reviewer_id INT,
	FOREIGN KEY (series_id) REFERENCES series(id),
	FOREIGN KEY (reviewer_id) REFERENCES reviewers(id)
);

-- /// zadania \\\ --

SELECT title, rating FROM series JOIN reviews ON series.id = reviews.series_id; -- zwykłe połączenie wspólnych wierszy 'OVERLAP'

-- nowa funkcja ROUND ! --
SELECT title, ROUND(AVG(rating), 2) AS avg_rating FROM series JOIN reviews ON series.id = reviews.series_id GROUP BY title ORDER BY avg_rating;
SELECT ROUND(3.126458); -- funkcja zaokrąglenia
SELECT ROUND(3.126458, 2); -- po przecinku można podać ilość miejsc po przecinku jakie chcemy wywołać

SELECT first_name, last_name, rating FROM reviewers JOIN reviews ON reviewers.id = reviews.reviewer_id;
SELECT title AS unreviewed_series FROM series LEFT JOIN reviews ON series.id = reviews.series_id WHERE rating IS NULL; -- tytuły bez recenzji
SELECT title AS unreviewed_series FROM reviews RIGHT JOIN series ON series.id = reviews.series_id WHERE rating IS NULL; -- dla odmiany join z prawej
SELECT genre, ROUND(AVG(rating), 2) AS avg_rating FROM series JOIN reviews ON series.id = reviews.series_id GROUP BY genre ORDER BY avg_rating; -- grupowanie ocen po gatunku

-- poniżej trzy wersje tego zapytania --
SELECT
	first_name,
	last_name,
	COUNT(rating) AS COUNT,
	IFNULL(MIN(rating), 0) AS MIN,
	IFNULL(MAX(rating), 0) AS MAX,
	ROUND(IFNULL(AVG(rating), 0), 2) AS avg_rating,
	CASE
		WHEN reviews.id IS NULL THEN 'INACTIVE'
		ELSE 'ACTIVE'
	END AS 'STATUS'
FROM reviewers
LEFT JOIN reviews ON reviewers.id = reviews.reviewer_id
GROUP BY first_name, last_name, STATUS;

-- alternatywna wersja CASE --
SELECT
	first_name,
	last_name,
	COUNT(rating) AS COUNT,
	IFNULL(MIN(rating), 0) AS MIN,
	IFNULL(MAX(rating), 0) AS MAX,
	ROUND(IFNULL(AVG(rating), 0), 2) AS avg_rating,
	CASE
		WHEN COUNT(rating) > 0 THEN 'ACTIVE'
		ELSE 'INACTIVE'
	END AS 'STATUS'
FROM reviewers
LEFT JOIN reviews ON reviewers.id = reviews.reviewer_id
GROUP BY first_name, last_name;

-- jeszcze jedna wersja z IF --
SELECT
	first_name,
	last_name,
	COUNT(rating) AS COUNT,
	IFNULL(MIN(rating), 0) AS MIN,
	IFNULL(MAX(rating), 0) AS MAX,
	ROUND(IFNULL(AVG(rating), 0), 2) AS avg_rating,
	IF(COUNT(rating > 0), 'ACTIVE', 'INACTIVE') -- pierwszy przypadek z 'IF' - IF(WARUNEK, then, else)
FROM reviewers
LEFT JOIN reviews ON reviewers.id = reviews.reviewer_id
GROUP BY first_name, last_name;

-- pierwsza metoda 
SELECT
	title,
	rating,
	CONCAT(first_name, ' ', last_name) AS reviewer
FROM reviews
	LEFT JOIN series ON series.id = reviews.series_id
	LEFT JOIN reviewers ON reviewers.id = reviews.reviewer_id;

-- druga metoda
SELECT
	title,
	rating,
	CONCAT(first_name, ' ', last_name) AS reviewer
FROM series
	JOIN reviews ON reviews.series_id = series.id 
	JOIN reviewers ON reviews.reviewer_id = reviewers.id;


-- /// CREATING VIEW \\\ --

CREATE VIEW full_reviews AS -- utworzy wirtualną tabelę, można na niej działać jak na zwykłej tabeli
SELECT title, released_year, genre, rating, first_name, last_name FROM reviews
JOIN series ON series.id = reviews.series_id
JOIN reviewers ON reviewers.id = reviews.reviewer_id;
-- z widoku nie można usuwać ani dodawać wpisów NOT UPDATEABLE--
-- wyjątkiem są widoki, które nie mają określonych warunków jak JOIN, AGGREGATE, GROUP BY i inne (zob. dokumentacja ORACLE)

-- REPLACING/ALTERING VIEWS --
CREATE VIEW ordered_series AS
SELECT * FROM series ORDER BY released_year;

CREATE OR REPLACE VIEW ordered_series AS -- jeśli nie istnieje widok to stwórz, jeśli istnieje to podmień
SELECT * FROM series ORDER BY released_year DESC;

ALTER VIEW ordered_series AS -- druga metoda
SELECT * FROM series ORDER BY released_year DESC;

DROP VIEW ordered_series; -- usuwanie widoku

-- HAVING - zaawansowane GROUP BY --
-- dzięki tej funkcji możemy kontrolować co GROUP BY wyświetli --
SELECT title, AVG(rating), COUNT(rating) AS review_count 
FROM full_reviews -- to jest widok
GROUP BY title HAVING COUNT(rating) > 1; -- odfiltrujemy tylko te wiersze, które mają więcej niż jedną recenzję
-- ORAZ trzeba używać zamiast WHERE gdy korzystamy z funkcji agregujących
SELECT  
        user_id,
        COUNT(photo_id) AS sum_of_likes
    FROM likes
    GROUP BY user_id
    HAVING sum_of_likes = (SELECT COUNT(*) FROM photos) -- zamiast WHERE i po GROUP BY!!!
    ORDER BY sum_of_likes DESC;

-- WITH ROLL UP (z GROUP BY) --
-- funkcja ta niejako podsumowuje grupowanie dla każdej grupy. Ciężko to opisać, lepiej na przykładzie to widać --
SELECT title, COUNT(rating) FROM full_reviews
GROUP BY title WITH ROLLUP; -- tu podsumowuje wszystkie recenzje

SELECT first_name, released_year, genre, AVG(rating)
FROM full_reviews
GROUP BY released_year, genre, first_name WITH ROLLUP; -- a tu robi to co robi ;)

-- SQL modes --
-- TO view modes:
SELECT @@GLOBAL.sql_mode;
SELECT @@SESSION.sql_mode;

-- To set them:
SET GLOBAL sql_mode = 'modes'; -- 'modes' zastępuję trybami, które mają zostać, a pomijam te, które chcę wyłączyć, '' wyłączy wszystko
SET SESSION sql_mode = 'modes'; -- jak już grzebać, to lepiej w sesji, po restarcie wrócą domyślne ustawienia

-- STRICT_TRANS_TABLES --
-- jeden z trybów, nie pozwala wprowadzać np. niepoprawnych typów danych np. tekst do INT

-- /// Window functions - OVER(), PARTITION BY \\\ --
-- funkcje window działają podobnie do GROUP BY z tą różnicą, że nie tworzy jednego wiersza z kilku tych samych, lecz zostawia je i obok tworzy kolumnę 
CREATE TABLE employees (
    emp_no INT PRIMARY KEY AUTO_INCREMENT,
    department VARCHAR(20),
    salary INT
);

SELECT department, AVG(salary) FROM employees GROUP BY department; -- zwykłe GROUP BY, okroi ilość wierszy ze średnią wartością
SELECT emp_no, department, salary, AVG(salary) OVER(PARTITION BY department) AS dept_avg FROM employees; -- średnia na dział
SELECT emp_no, department, salary, AVG(salary) OVER() FROM employees; -- średnia ogólnie, łącznie z wszystkimi działami
SELECT emp_no, department, salary, MIN(salary) OVER(), MAX(salary) OVER() FROM employees;

SELECT 
	emp_no, 
	department, 
	salary, 
	AVG(salary) OVER(PARTITION BY department) AS dept_avg, -- średnia pensja na dział
	AVG(salary) OVER() AS company_avg -- średnia pensja na całą firmę
FROM employees;

SELECT 
	emp_no, 
	department, 
	salary, 
	SUM(salary) OVER(PARTITION BY department) AS dept_payroll, -- suma pensji na dział
	SUM(salary) OVER() AS total_payroll -- suma pensji na firmę
FROM employees; 

SELECT 
	emp_no, 
	department, 
	salary, 
	SUM(salary) OVER(PARTITION BY department ORDER BY salary) AS rolling_dept_salary, -- sumuje kolejne wpisy
	SUM(salary) OVER(PARTITION BY department) AS total_dept_salary
FROM employees;

SELECT 
	emp_no, 
	department, 
	salary, 
	MIN(salary) OVER(PARTITION BY department ORDER BY salary DESC) AS rolling_min
FROM employees;

-- ROW_NUMBER, RANK, DENSE_RANK --
SELECT 
	emp_no, 
	department, 
	salary, 
	ROW_NUMBER() OVER(PARTITION BY department ORDER BY salary DESC) AS dept_row_number, -- numeruje wiersze w działach
	RANK() OVER(PARTITION BY department ORDER BY salary DESC) AS dept_salary_rank, -- określa miejsce pracownika pod kątem pensji w dziale
	RANK() OVER(ORDER BY salary DESC) AS overall_rank, -- określa ogólne miejsce w firmie(pomija numery gdzie był remis)
	DENSE_RANK() OVER(ORDER BY salary DESC) AS overall_dense_rank, -- jak wyżej lecz nie pomija numerów
	ROW_NUMBER() OVER(ORDER BY salary DESC) AS overall_num -- numeruje wiersze ogólnie w całej firmie
FROM employees ORDER BY overall_rank;

--NTILE() - dzielenie na 'n' grup --
SELECT 
	emp_no, 
	department, 
	salary, 
	NTILE(4) OVER(PARTITION BY department ORDER BY salary DESC) AS dept_salary_quartile, -- NTILE dzieli sumę na kwarty(4), tu pokaże w działach
	NTILE(4) OVER(ORDER BY salary DESC) AS salary_quartile -- jw. lecz tu pokaże kwarty na firmę
FROM employees;

-- FIRST_VALUE -- 
SELECT 
	emp_no, 
	department, 
	salary,
	FIRST_VALUE(emp_no) OVER(PARTITION BY department ORDER BY salary DESC) AS highest_paid_dept,
	FIRST_VALUE(emp_no) OVER (ORDER BY salary DESC) AS highest_paid_overall
FROM employees;

-- LEAD and LAG - do znajdywania różnic między wierszami --
SELECT 
	emp_no, 
	department, 
	salary,
	salary - LAG(salary) OVER(ORDER BY salary DESC) AS salary_diff -- wyświetla różnicę pensji względem poprzedniego wiersza
FROM employees;

SELECT 
	emp_no, 
	department, 
	salary,
	salary - LAG(salary) OVER(PARTITION BY department ORDER BY salary DESC) AS dept_salary_diff -- jw. lecz posortowane wg działu
FROM employees;


-- ///  Database triggers  \\\ --

--SHOW TRIGGERS; - sprawdzenie aktywnych triggerów w bazie w której się znajduję
--DROP TRIGGER trigger_name; - usunięcie triggera z bazy
-- the syntax --
CREATE TRIGGER trigger_name
	trigger_time trigger_event ON table_name FOR EACH ROW
	BEGIN
	...
	END;

-- trigger_time - BEFORE or AFTER
-- trigger_event - INSERT, UPDATE or DELETE

-- the trigger --
DELIMITER $$	-- znak $$ jest po to aby można w triggerze zawrzeć kilka żadań zakończonych ;, ale można użyć jakichkolwiek znaków np. //, || itd.
				-- to delimeter określa że dalej będzie blok kilku żądań
CREATE TRIGGER must_be_adult
     BEFORE INSERT ON users FOR EACH ROW
     BEGIN
          IF NEW.age < 18		-- NEW oznacza nowy wpis
          THEN
              SIGNAL SQLSTATE '45000'	-- jest baza kodów błędu na Oracle
                    SET MESSAGE_TEXT = 'Must be an adult!';	-- pierwszy ;
          END IF;	-- drugi ;
     END;	-- trzeci ;
$$	-- dzięki $$ można było użyć kilka ;

DELIMITER ;
-- zaczytanie trigger zadziałało tylko metodą wczytania pliku source trigger.sql

-- trigger do IG database - tworzę plik .sql z triggerem i zaczytuję go do DB metodą source
DELIMITER $$

CREATE TRIGGER example_cannot_follow_self
     BEFORE INSERT ON follows FOR EACH ROW
     BEGIN
          IF NEW.follower_id = NEW.followee_id
          THEN
               SIGNAL SQLSTATE '45000'
                    SET MESSAGE_TEXT = 'Cannot follow yourself, silly';
          END IF;
     END;
$$

DELIMITER ;

-- INSERT do IG
INSERT INTO follows (follower_id, followee_id) VALUES(4,4);

-- śledzenie unfollows na IG - w tej tabeli będą zapisywać się każde usuniętę wiersze z tabeli follows, dzięki poniższemu triggerowi
CREATE TABLE unfollows (
    follower_id INT NOT NULL,
    followee_id INT NOT NULL,
    created_at TIMESTAMP DEFAULT NOW(),
    FOREIGN KEY (follower_id) REFERENCES users(id),
    FOREIGN KEY (followee_id) REFERENCES users(id),
    PRIMARY KEY (follower_id, followee_id)
);

-- trigger:
DELIMITER $$

CREATE TRIGGER create_unfollow
    AFTER DELETE ON follows FOR EACH ROW 
BEGIN
    INSERT INTO unfollows
    SET follower_id = OLD.follower_id,
        followee_id = OLD.followee_id;
END$$

DELIMITER ;

-- TRIGGERy są nie popularne, gdyż mogą sprawiać problem z debugowaniem w zespole deweloperskim
