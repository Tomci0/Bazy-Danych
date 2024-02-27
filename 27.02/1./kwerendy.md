# Zadanie 1


### 0.

CREATE TABLE OSOBA ( Imie VARCHAR(15) NOT NULL, Nazwisko VARCHAR(20) NOT NULL, Telefon INT NOT NULL );

INSERT INTO OSOBA (Imie, Nazwisko, Telefon) VALUES ('Jan', 'Kowalski', 123456789), ('Anna', 'Nowak', 987654321), ('Michał', 'Wieczorek', 111222333), ('Kasia', 'Wróbel', 444555666), ('Tomasz', 'Jasiński', 777888999), ('Zofia', 'Mazur', 222333444), ('Marcin', 'Kwiatkowski', 555666777), ('Karolina', 'Górska', 888999000), ('Mateusz', 'Zieliński', 333444555), ('Agnieszka', 'Grabowska', 666777888);

### 1.

SELECT * FROM OSOBA;

### 2. 

SELECT DISTINCT Nazwisko FROM OSOBA;

### 3.

SELECT Nazwisko FROM OSOBA ORDER BY Nazwisko ASC;

### 4.

SELECT Telefon FROM OSOBA WHERE LENGTH(Telefon) = 6;

### 5.

SELECT Imie FROM OSOBA WHERE Imie LIKE 'Ma%';

### 6.

ALTER TABLE OSOBA ADD Miejscowosc VARCHAR(20) NOT NULL DEFAULT 'Łódź';

### 7.

UPDATE OSOBA SET Miejscowosc = 'Warszawa' WHERE Imie LIKE 'Ma%';




