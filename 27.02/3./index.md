# CREATE DATABASE

DROP DATABASE `LISTA_PLAC`;
CREATE DATABASE `LISTA_PLAC`;
USE `LISTA_PLAC`;

CREATE TABLE `Pracownicy` (
  `ID` int(11) NOT NULL,
  `Imie` varchar(50) DEFAULT NULL,
  `Nazwisko` varchar(50) DEFAULT NULL,
  `GrupaZaszeregowania` int(11) DEFAULT NULL,
  `ProcentPremii` decimal(5,2) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

INSERT INTO `Pracownicy` (`ID`, `Imie`, `Nazwisko`, `GrupaZaszeregowania`, `ProcentPremii`) VALUES
(1, 'Jan', 'Kowalski', 1, 10.00),
(2, 'Anna', 'Nowak', 2, 8.00),
(3, 'Marek', 'Wiśniewski', 3, 12.00),
(4, 'Katarzyna', 'Wójcik', 1, 15.00);

CREATE TABLE `StawkiWynagrodzenia` (
  `ID` int(11) NOT NULL,
  `GrupaZaszeregowania` varchar(50) DEFAULT NULL,
  `Stawka` decimal(10,2) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

INSERT INTO `StawkiWynagrodzenia` (`ID`, `GrupaZaszeregowania`, `Stawka`) VALUES
(1, 'Grupa A', 5000.00),
(2, 'Grupa B', 4000.00),
(3, 'Grupa C', 3000.00);

ALTER TABLE `Pracownicy`
  ADD PRIMARY KEY (`ID`),
  ADD KEY `GrupaZaszeregowania` (`GrupaZaszeregowania`);

ALTER TABLE `StawkiWynagrodzenia`
  ADD PRIMARY KEY (`ID`);

ALTER TABLE `Pracownicy`
  MODIFY `ID` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=5;


ALTER TABLE `StawkiWynagrodzenia`
  MODIFY `ID` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=4;

ALTER TABLE `StawkiWynagrodzenia`
  ADD CONSTRAINT `stawkiwynagrodzenia_ibfk_1` FOREIGN KEY (`ID`) REFERENCES `Pracownicy` (`GrupaZaszeregowania`);
COMMIT;

# QUERY

SELECT 
    p.Imie,
    p.Nazwisko,
    s.Stawka AS 'Wynagrodzenie zasadnicze',
    (s.Stawka * (p.ProcentPremii / 100)) AS 'Kwota premii',
    (s.Stawka + (s.Stawka * (p.ProcentPremii / 100))) AS 'Kwota do wypłaty'
FROM 
    Pracownicy p
JOIN 
    StawkiWynagrodzenia s ON p.GrupaZaszeregowania = s.ID
ORDER BY 
    p.Nazwisko;