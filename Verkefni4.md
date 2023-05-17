# GAGN2VG05CU
### Verkefni 4

#### Gagnagrunnur útbúinn
```
CREATE TABLE Sveitarfelog (
  NumerSveitarfelags VARCHAR(10) PRIMARY KEY,
  NafnSveitarfelags VARCHAR(255)
);
```
```
CREATE TABLE FjoldiIbua (
  NumerSveitarfelags VARCHAR(10),
  Fjoldi2018 INT,
  Fjoldi2017 INT,
  FOREIGN KEY (NumerSveitarfelags) REFERENCES Sveitarfelog (NumerSveitarfelags)
);
```
```
ALTER TABLE Sveitarfelog
ADD JSONData JSON;
```
```
-- Innsetning Sveitarfélaga
INSERT INTO Sveitarfelog (NumerSveitarfelags, NafnSveitarfelags)
VALUES
  ('0000', 'Reykjavík'),
  ('1000', 'Kópavogur'),
  ('1100', 'Seltjarnarnesbær'),
  ('1300', 'Garðabær'),
  ('1400', 'Hafnarfjörður'),
  ('1604', 'Mosfellsbær'),
  ('1606', 'Kjósarhreppur'),
  ('2000', 'Reykjanesbær'),
  ('2300', 'Grindavíkurbær'),
  ('2503', 'Sandgerðisbær'),
  ('2504', 'Sveitarfélagið Garður'),
  ('2506', 'Sveitarfélagið Vogar'),
  ('3000', 'Akraneskaupstaður'),
  ('3506', 'Skorradalshreppur'),
  ('3511', 'Hvalfjarðarsveit'),
  ('3609', 'Borgarbyggð'),
  ('3709', 'Grundarfjarðarbær'),
  ('3710', 'Helgafellssveit'),
  ('3711', 'Stykkishólmsbær'),
  ('3713', 'Eyja- og Miklaholtshreppur'),
  ('3714', 'Snæfellsbær'),
  ('3811', 'Dalabyggð'),
  ('4100', 'Bolungarvíkurkaupstaður'),
  ('4200', 'Ísafjarðarbær'),
  ('4502', 'Reykhólahreppur'),
  ('4604', 'Tálknafjarðarhreppur'),
  ('4607', 'Vesturbyggð'),
  ('4803', 'Súðavíkurhreppur'),
  ('4901', 'Árneshreppur'),
  ('4902', 'Kaldrananeshreppur'),
  ('4911', 'Strandabyggð'),
  ('5200', 'Sveitarfélagið Skagafjörður'),
  ('5508', 'Húnaþing vestra'),
  ('5604', 'Blönduósbær'),
  ('5609', 'Sveitarfélagið Skagaströnd'),
  ('5611', 'Skagabyggð'),
  ('5612', 'Húnavatnshreppur'),
  ('5706', 'Akrahreppur'),
  ('6000', 'Akureyrarkaupstaður'),
  ('6100', 'Norðurþing'),
  ('6250', 'Fjallabyggð'),
  ('6400', 'Dalvíkurbyggð'),
  ('6513', 'Eyjafjarðarsveit'),
  ('6515', 'Hörgársveit'),
  ('6601', 'Svalbarðsstrandarhreppur'),
  ('6602', 'Grýtubakkahreppur'),
  ('6607', 'Skútustaðahreppur'),
  ('6611', 'Tjörneshreppur'),
  ('6612', 'Þingeyjarsveit'),
  ('6706', 'Svalbarðshreppur'),
  ('6709', 'Langanesbyggð'),
  ('7000', 'Seyðisfjarðarkaupstaður'),
  ('7300', 'Fjarðabyggð'),
  ('7502', 'Vopnafjarðarhreppur'),
  ('7505', 'Fljótsdalshreppur'),
  ('7509', 'Borgarfjarðarhreppur'),
  ('7613', 'Breiðdalshreppur'),
  ('7617', 'Djúpavogshreppur'),
  ('7620', 'Fljótsdalshérað'),
  ('7708', 'Sveitarfélagið Hornafjörður'),
  ('8000', 'Vestmannaeyjabær'),
  ('8200', 'Sveitarfélagið Árborg'),
  ('8508', 'Mýrdalshreppur'),
  ('8509', 'Skaftárhreppur'),
  ('8610', 'Ásahreppur'),
  ('8613', 'Rangárþing eystra'),
  ('8614', 'Rangárþing ytra'),
  ('8710', 'Hrunamannahreppur'),
  ('8716', 'Hveragerðisbær'),
  ('8717', 'Sveitarfélagið Ölfus'),
  ('8719', 'Grímsnes- og Grafningshreppur'),
  ('8720', 'Skeiða- og Gnúpverjahreppur'),
  ('8721', 'Bláskógabyggð'),
  ('8722', 'Flóahreppur');
```

```
-- Innsetning í Fjölda
INSERT INTO FjoldiIbua (NumerSveitarfelags, Fjoldi2018, Fjoldi2017)
VALUES
  ('0000', 126771, 126108),
  ('1000', 36290, 35903),
  ('1100', 4608, 4569),
  ('1300', 15869, 15691),
  ('1400', 29603, 29371),
  ('1604', 10730, 10514),
  ('1606', 227, 221),
  ('2000', 18074, 17732),
  ('2300', 3380, 3326),
  ('2503', 1807, 1785),
  ('2504', 1597, 1599),
  ('2506', 1275, 1269),
  ('3000', 7299, 7225),
  ('3506', 55, 56),
  ('3511', 649, 656),
  ('3609', 3751, 3745),
  ('3709', 888, 884),
  ('3710', 59, 59),
  ('3711', 1186, 1178),
  ('3713', 126, 123),
  ('3714', 1672, 1637),
  ('3811', 663, 666),
  ('4100', 935, 943),
  ('4200', 3771, 3709),
  ('4502', 278, 277),
  ('4604', 244, 245),
  ('4607', 1004, 1023),
  ('4803', 200, 196),
  ('4901', 45, 41),
  ('4902', 108, 109),
  ('4911', 451, 449),
  ('5200', 3985, 3945),
  ('5508', 1184, 1190),
  ('5604', 906, 892),
  ('5609', 466, 480),
  ('5611', 88, 92),
  ('5612', 379, 387),
  ('5706', 195, 194),
  ('6000', 18817, 18789),
  ('6100', 3202, 3278),
  ('6250', 2013, 2011),
  ('6400', 1886, 1889),
  ('6513', 1017, 1012),
  ('6515', 596, 581),
  ('6601', 499, 482),
  ('6602', 365, 372),
  ('6607', 507, 493),
  ('6611', 58, 58),
  ('6612', 930, 969),
  ('6706', 93, 92),
  ('6709', 493, 480),
  ('7000', 687, 674),
  ('7300', 4810, 4780),
  ('7502', 657, 661),
  ('7505', 74, 76),
  ('7509', 105, 108),
  ('7613', 191, 183),
  ('7617', 462, 461),
  ('7620', 3540, 3545),
  ('7708', 2323, 2299),
  ('8000', 4289, 4283),
  ('8200', 9131, 8964),
  ('8508', 652, 626),
  ('8509', 568, 564),
  ('8610', 243, 251),
  ('8613', 1818, 1801),
  ('8614', 1608, 1599),
  ('8710', 780, 777),
  ('8716', 2582, 2554),
  ('8717', 2111, 2106),
  ('8719', 468, 479),
  ('8720', 615, 607),
  ('8721', 391, 399),
  ('8722', 1109, 1097);
  ```

#### Store Procedures
##### 1)
```
CREATE PROCEDURE FelagsUpplysingar(numerFelags VARCHAR(10))
BEGIN
    SELECT c.*, p.Fjoldi2018, p.Fjoldi2017
    FROM Sveitarfelog c
    JOIN FjoldiIbua p ON c.NumerSveitarFelags = p.NumerSveitarFelags
    WHERE c.NumerSveitarfelags = numerFelags;
END €€
DELIMITER ;
call FelagsUpplysingar('1100');
```
##### 3)
```
DROP PROCEDURE IF EXISTS FjoldiEftirAri;
DELIMITER €€
CREATE PROCEDURE FjoldiEftirAri(targetYear INT)
BEGIN
    IF targetYear = 2018 THEN
        SELECT SUM(p.Fjoldi2018) AS TotalPopulation
        FROM FjoldiIbua p;
    ELSEIF targetYear = 2017 THEN
        SELECT SUM(p.Fjoldi2017) AS TotalPopulation
        FROM FjoldiIbua p;
    ELSE
        -- Handle other years or invalid inputs
        SELECT NULL AS NafnSveitarfelags, NULL AS TotalPopulation;
    END IF;
END €€
DELIMITER ;
CALL FjoldiEftirAri(2018);
```
##### 4)
```
Drop procedure BreytingFjolda;
DELIMITER €€
CREATE PROCEDURE BreytingFjolda()
BEGIN
    SELECT c.NafnSveitarfelags,
           ((p.Fjoldi2018 - p.Fjoldi2017) / p.Fjoldi2017) * 100 AS Breyting
    FROM Sveitarfelog c
    JOIN FjoldiIbua p ON c.NumerSveitarfelags = p.NumerSveitarfelags;
END €€
DELIMITER ;
CALL BreytingFjolda();
```
##### 5)
```
drop procedure FjoldiMilliAra;
DELIMITER €€
CREATE PROCEDURE FjoldiMilliAra(targetYear1 INT, targetYear2 INT)
BEGIN
    DECLARE columnName1 VARCHAR(10);
    DECLARE columnName2 VARCHAR(10);
    
    -- Dynamically determine the column names based on the target years
    SET columnName1 = CONCAT('Fjoldi', targetYear1);
    SET columnName2 = CONCAT('Fjoldi', targetYear2);

    SET @query = CONCAT('SELECT c.NafnSveitarfelags, ((', columnName2, ' - ', columnName1, ') / ', columnName1, ') * 100 AS Breyting ',
                        'FROM Sveitarfelog c JOIN FjoldiIbua p ON c.NumerSveitarfelags = p.NumerSveitarfelags');
    
    -- Prepare and execute the dynamic query
    PREPARE stmt FROM @query;
    EXECUTE stmt;
    DEALLOCATE PREPARE stmt;
END €€
DELIMITER ;
CALL FjoldiMilliAra(2017, 2018);
```

#### Python kóði sem exportar gögn í json (json skrá má sjá í viðhengi á repo)
```
import json
import mysql.connector


db = mysql.connector.connect(
  host='127.0.0.1',
  user='root',
  password='93089548Be',
  database='verkefni4'
)


cursor = db.cursor()


query = '''
SELECT c.NumerSveitarfelags, c.NafnSveitarfelags, p.Fjoldi2018, p.Fjoldi2017
FROM Sveitarfelog c
JOIN FjoldiIbua p ON c.NumerSveitarfelags = p.NumerSveitarfelags
'''

cursor.execute(query)

rows = cursor.fetchall()

data = []

with open('data.json', 'w') as file:
    for row in rows:
        NumerSveitarfelags, NafnSveitarfelags, Fjoldi2018, Fjoldi2017 = row
        data = {
            'Numer Sveitarfelags': NumerSveitarfelags,
            'Sveitarfelag': NafnSveitarfelags,
            'Fjoldi ibua 2018': Fjoldi2018,
            'Fjoldi ibua 2017': Fjoldi2017
        }
        # Write the data as a JSON object followed by a newline character
        file.write(json.dumps(data) + '\n')


cursor.close()
db.close()
```
