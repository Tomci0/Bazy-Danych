# Zadanie 2

### 0.

CREATE TABLE TOWAR (
  Nazwa VARCHAR(15) NOT NULL,
  Cena DECIMAL(10,2) NOT NULL,
  Data_Prod DATE NOT NULL,
  Ilosc INT NOT NULL,
  Waga DECIMAL(10,3) NOT NULL
);

INSERT INTO TOWAR (Nazwa, Cena, Data_Prod, Ilosc, Waga) VALUES
  ('Produkt 1', 25.50, '2005-02-01', 10, 1.250),
  ('Produkt 2', 48.99, '2004-05-12', 20, 2.000),
  ('Produkt 3', 12.34, '2003-10-23', 30, 3.500),
  ('Produkt 4', 77.77, '2006-01-04', 40, 4.750),
  ('Produkt 5', 33.33, '2002-04-05', 50, 5.000),
  ('Produkt 6', 66.66, '2007-07-06', 60, 6.250),
  ('Produkt 7', 10.00, '2001-11-07', 70, 7.500),
  ('Produkt 8', 55.55, '2008-02-08', 80, 8.750),
  ('Produkt 9', 99.99, '2009-05-09', 90, 9.000),
  ('Produkt 10', 22.22, '2010-08-10', 100, 10.250);

### 1.

SELECT * FROM TOWAR WHERE Cena BETWEEN 10 AND 50;

### 2.

SELECT SUM(Cena * Ilosc) FROM TOWAR WHERE Data_Prod > '2004-01-01';

### 3.

SELECT COUNT(*) AS IloscRekordow, AVG(Waga) AS SredniaWaga, SUM(Ilosc) AS SumaIlosc, MIN(Cena) AS MinimalnaCena, MAX(Cena) AS MaksymalnaCena
FROM TOWAR;


### 4.

SELECT Nazwa, COUNT(*) AS IloscSztuk
FROM TOWAR
GROUP BY Nazwa
HAVING COUNT(*) > 2;


### 5.

SELECT * FROM TOWAR WHERE Waga > 50;

### 6.

SELECT * FROM TOWAR WHERE Cena BETWEEN 10 AND 99;

### 7.

SELECT * FROM TOWAR WHERE Cena * 0.22 > 50;

### 8.

SELECT * FROM TOWAR WHERE (Cena < 50 OR Cena > 100) AND Ilosc > 5;

### 9.

SELECT * FROM TOWAR WHERE Cena / Waga BETWEEN 10 AND 50;

### 10.

SELECT * FROM TOWAR WHERE Ilosc * Waga BETWEEN Cena AND Cena * 3;

### 11.

SELECT Nazwa FROM TOWAR WHERE Nazwa NOT LIKE '%A%';

### 12.

SELECT * FROM TOWAR WHERE Data_Prod < DATE_SUB(CURRENT_DATE(), INTERVAL 5 YEAR);

### 13.

SELECT * FROM TOWAR WHERE Data_Prod BETWEEN '2000-01-01' AND '2004-12-31' AND Cena BETWEEN 10 AND 99 AND Waga < 5;

### 14.

SELECT COUNT(DISTINCT Nazwa) AS IloscUnikalnychNazw FROM TOWAR;

### 15.

SELECT Nazwa, SUM(Ilosc * Cena) AS Wartosc, SUM(Ilosc * Waga) AS Masa, AVG(Ilosc * Cena) AS SredniaWartosc, AVG(Ilosc * Waga) AS SredniaMasa
FROM TOWAR
GROUP BY Nazwa;

### 16.

ALTER TABLE TOWAR ADD VAT INT NOT NULL;

### 17.

UPDATE TOWAR SET VAT = CASE WHEN Ilosc < 50 THEN 22 ELSE 7 END;

### 18.

UPDATE TOWAR SET Cena = Cena * 1.5 WHERE Cena < 50;
