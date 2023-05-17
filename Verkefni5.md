# GAGN2VG05CU
## Verkefni 5   || Enn í vinnslu
### Liður 1
#### Uppsetning
```
-- Uppsetning
CREATE TABLE User (
  UserID INT PRIMARY KEY,
  Username VARCHAR(255),
  UserPassword VARCHAR(255),
  UserTypeID INT,
  UserStatusID INT,
  -- Other user information columns
  -- ...
  FOREIGN KEY (UserTypeID) REFERENCES UserType(UserTypeID),
  FOREIGN KEY (UserStatusID) REFERENCES UserStatus(UserStatusID)
);

CREATE TABLE UserType (
  UserTypeID INT PRIMARY KEY,
  TypeName VARCHAR(255)
);

CREATE TABLE UserStatus (
  UserStatusID INT PRIMARY KEY,
  StatusName VARCHAR(255)
);

CREATE TABLE ProblemCategory (
  CategoryID INT PRIMARY KEY,
  CategoryName VARCHAR(255)
);

CREATE TABLE Problem (
  ProblemID INT PRIMARY KEY,
  UserID INT,
  CategoryID INT,
  ProblemDescription TEXT,
  Timestamp TIMESTAMP,
  FOREIGN KEY (UserID) REFERENCES User(UserID),
  FOREIGN KEY (CategoryID) REFERENCES ProblemCategory(CategoryID)
);

CREATE TABLE Solution (
  SolutionID INT PRIMARY KEY,
  ProblemID INT,
  UserID INT,
  SolutionDescription TEXT,
  Timestamp TIMESTAMP,
  FOREIGN KEY (ProblemID) REFERENCES Problem(ProblemID),
  FOREIGN KEY (UserID) REFERENCES User(UserID)
);

CREATE TABLE Evaluation (
  EvaluationID INT PRIMARY KEY,
  UserID INT,
  SolutionID INT,
  Rating INT,
  FOREIGN KEY (UserID) REFERENCES User(UserID),
  FOREIGN KEY (SolutionID) REFERENCES Solution(SolutionID)
);
```

### Innsetning
```
-- Innsetning
INSERT INTO UserStatus (UserStatusID, StatusName)
VALUES
  (1, 'Active'),
  (2, 'Inactive'),
  (3, 'Temporary ban'),
  (4, 'Prohibition');
  
INSERT INTO UserType (UserTypeID, TypeName)
VALUES
  (1, 'Beginner'),
  (2, 'User'),
  (3, 'Advanced user'),
  (4, 'Super user'),
  (5, 'Administrator');
  
INSERT INTO User (UserID, Username, Password, UserTypeID, UserStatusID)
VALUES
  (1, 'Bósi', 'password1', 1, 1),
  (2, 'Benjamín', 'password2', 2, 1),
  (3, 'Katla', 'password3', 3, 1),
  (4, 'Bjarniben', 'password4', 4, 1),
  (5, 'Admin', 'adminpass', 5, 1);
  
 INSERT INTO ProblemCategory (CategoryID, CategoryName)
VALUES
  (1, 'Programming'),
  (2, 'Databases'),
  (3, 'Game Development'),
  (4, 'Linux System Administration'),
  (5, 'Windows System Administration'),
  (6, 'Robots'),
  (7, 'Web development'),
  (8, 'Other');
  
INSERT INTO Problem (ProblemID, UserID, CategoryID, ProblemDescription, Timestamp)
VALUES
  -- Programming
  (1, 1, 1, 'Ég á í vandræðum með aðgreiningarvillu í C++ forritinu mínu.', NOW()),
  (2, 2, 1, 'Hvernig get ég fínstillt Python kóðann minn fyrir betri árangur? Ég er að upplifa hæga framkvæmd.', NOW()),
  
  -- Databases
  (3, 3, 2, 'Ég þarf hjálp við að hanna venslagagnagrunnsskema fyrir vefforritið mitt.', NOW()),
  (4, 4, 2, 'Hvernig get ég bætt árangur fyrirspurna í SQL gagnagrunninum mínum?', NOW()),
  
  -- Game Development
  (5, 1, 3, 'Ég er að lenda í rendering vandamáli í Unity leiknum mínum. Texture birtist ekki rétt.', NOW()),
  (6, 2, 3, 'Hverjar eru nokkrar bestu venjur til að innleiða collision detection í leik?', NOW()),
  
  -- Linux System Administration
  (7, 3, 4, 'Ég þarf aðstoð við að stilla eldveggsreglu í Linux.', NOW()),
  (8, 4, 4, 'Hvernig get ég fylgst með kerfisauðlindum og frammistöðu í Linux?', NOW()),
  
  -- System Administration - Windows category
  (9, 1, 5, 'Windows þjónninn minn er að upplifa oft hrun. Hvernig get ég leyst og lagað vandamálið?', NOW()),
  (10, 2, 5, 'Ég vil setja upp áætlað verkefni í Windows Server. Hvernig fer ég að því?', NOW()),
  
  -- Robots
  (11, 3, 6, 'Ég er að vinna að vélfærafræðiverkefni með ROS. Hvernig get ég tengst við skynjara og stýrisbúnað?', NOW()),
  (12, 4, 6, 'Hvað eru góð reiknirit fyrir vélmennaleiðarskipulagningu?', NOW()),
  
  -- Web development
  (13, 1, 7, 'Ég er í vandræðum með CSS skipulag. Hvernig get ég búið til móttækilega hönnun?', NOW()),
  (14, 2, 7, 'Hver er besta aðferðin til að tryggja notendavottun í vefforritum?', NOW()),
  
  -- Other
  (15, 3, 8, 'Ég er með ýmsa spurningu sem tengist hugbúnaðarþróun.', NOW()),
  (16, 4, 8, 'Hvernig get ég bætt árangur JavaScript kóðans míns?', NOW());

INSERT INTO Solution (SolutionID, ProblemID, UserID, SolutionDescription, Timestamp)
VALUES
  (1, 1, 2, 'Til að kemba sundurliðunarvilluna geturðu notað villuforrit eins og gdb. Byrjaðu á því að greina staflasporið til að bera kennsl á upptök málsins.', NOW()),
  
  (2, 2, 3, 'Til að fínstilla Python kóðann þinn geturðu íhugað að nota tækni eins og kóðasnið, reiknirit fínstillingar og skyndiminni.', NOW()),
  
  (3, 3, 4, 'Til að hanna venslagagnagrunnsskema er mikilvægt að greina kröfurnar og staðla gögnin. Íhugaðu að nota verkfæri eins og ER skýringarmyndir og normalization tækni.', NOW()),
  
  (4, 4, 1, 'Til að bæta árangur fyrirspurna í SQL gagnagrunninum þínum geturðu íhugað að skrá viðeigandi dálka, fínstilla framkvæmdaráætlun fyrirspurna og nota skyndiminni.', NOW()),
  
  (5, 5, 2, 'Til að leysa flutningsvandamálið í Unity, athugaðu hvort áferðin sé rétt flutt inn og tryggðu að réttur skyggingur sé úthlutaður á efnin.', NOW()),
  
  (6, 6, 3, 'Til að innleiða árekstrargreiningu í leikjum geturðu notað tækni eins og bindandi rúmmál, staðbundna skiptingu og þröngfasa árekstrargreiningaralgrím.', NOW()),
  
  (7, 7, 4, 'Til að stilla eldveggsreglu í Linux geturðu notað verkfæri eins og iptables eða firewalld. Skilgreindu regluna sem þú vilt byggja á netkröfum þínum og notaðu hana.', NOW()),
  
  (8, 8, 1, 'Til að fylgjast með kerfisauðlindum og frammistöðu í Linux geturðu notað tól eins og top, htop eða systemd verkfæri eins og systemd-cgtop.', NOW()),
  
  (9, 9, 2, 'Til að leysa tíð hrun í Windows Server skaltu greina atburðaskrárnar, athuga hvort vélbúnaðarvandamál séu og uppfæra tækjarekla og kerfisplástra.', NOW()),
  
  (10, 10, 3, 'Til að setja upp áætlað verkefni í Windows Server geturðu notað Verkefnaáætlunina. Skilgreindu verkefnið með æskilegri áætlun, aðgerðum og skilyrðum.', NOW()),
  
  (11, 11, 4, 'Til að tengjast skynjurum og stýribúnaði í ROS, notaðu ROS pakka eins og rosserial eða útfærðu sérsniðna ROS hnúta byggða á vélbúnaðarforskriftum.', NOW()),
  
  (12, 12, 1, 'Fyrir skipulagningu vélmennaleiða skaltu íhuga reiknirit eins og A* leit, reiknirit Dijkstra eða Rapidly-Exploring Random Trees (RRT). Innleiða viðeigandi reiknirit byggt á kröfum þínum.', NOW()),
  
  (13, 13, 2, 'Til að búa til móttækilega hönnun með CSS, notaðu CSS miðlunarfyrirspurnir, flexbox eða CSS rist til að laga útlitið eftir mismunandi skjástærðum.', NOW()),
  
  (14, 14, 3, 'Til að tryggja auðkenningu notenda í vefforritum skaltu íhuga að nota öruggar samskiptareglur eins og HTTPS, innleiða sterkan lykilorðaþvott og beita tækni eins og CSRF vernd og lotustjórnun.', NOW());
  
INSERT INTO Evaluation (EvaluationID, SolutionID, UserID, Rating)
VALUES
  (1, 1, 1, 9),
  (2, 2, 2, 8),
  (3, 3, 3, 7),
  (4, 4, 4, 9),
  (5, 5, 1, 6),
  (6, 6, 2, 7),
  (7, 7, 3, 8),
  (8, 8, 4, 9),
  (9, 9, 1, 5),
  (10, 10, 2, 8),
  (11, 11, 3, 9),
  (12, 12, 4, 7),
  (13, 13, 1, 8),
  (14, 14, 2, 6);
```
### Liður 2
#### Crud
```
-- Create
INSERT INTO User (UserID, Username, UserPassword, UserTypeID, UserStatusID)
VALUES (6, 'Ellert', 'password6',
        (SELECT UserTypeID FROM UserType WHERE TypeName = 'Beginner'),
        (SELECT UserStatusID FROM UserStatus WHERE StatusName = 'Active'));
-- Read
SELECT * FROM User WHERE UserID = 6;
-- Update
UPDATE User 
SET UserTypeID = (SELECT UserTypeID FROM UserType WHERE TypeName = 'Super user')
WHERE UserID = 6;
-- Delete
DELETE FROM User WHERE UserID = 6;
```
### Liður 3
#### Store procedures
##### A)
```
DELIMITER €€
DROP PROCEDURE IF EXISTS AddNewProblem €€
CREATE PROCEDURE AddNewProblem (
  IN p_Username VARCHAR(255),
  IN p_CategoryID INT,
  IN p_ProblemDescription TEXT
)
BEGIN
  DECLARE v_UserID INT;
  
  SELECT UserID INTO v_UserID
  FROM User
  WHERE Username = p_Username;
  
  INSERT INTO Problem (UserID, CategoryID, ProblemDescription, Timestamp)
  VALUES (v_UserID, p_CategoryID, p_ProblemDescription, NOW());
END €€
DELIMITER ;

CALL AddNewProblem('Katla', 2, 'Er að lenda í vandræðum við að tengjast gagnagrunninum.');
```
##### B)
```
DELIMITER €€
DROP PROCEDURE IF EXISTS AddNewSolution €€
CREATE PROCEDURE AddNewSolution (
  IN p_Username VARCHAR(255),
  IN p_ProblemID INT,
  IN p_SolutionDescription TEXT
)
BEGIN
  DECLARE v_UserID INT;
  
  SELECT UserID INTO v_UserID
  FROM User
  WHERE Username = p_Username;
  
  INSERT INTO Solution (UserID, ProblemID, SolutionDescription, Timestamp)
  VALUES (v_UserID, p_ProblemID, p_SolutionDescription, NOW());
END €€
DELIMITER ;

CALL AddNewSolution('Bósi', 1, 'Hér er lausnin sem þú leitar að');
```
##### C)
```
DELIMITER €€
DROP PROCEDURE IF EXISTS UpdateUserStatus €€
CREATE PROCEDURE UpdateUserStatus (
  IN p_Username VARCHAR(255),
  IN p_NewStatus VARCHAR(255),
  IN p_AdminPassword VARCHAR(255)
)
BEGIN
  DECLARE v_AdminID INT;
  DECLARE v_StatusID INT;
  
  
  SELECT UserID INTO v_AdminID
  FROM User
  WHERE Username = 'admin' AND UserPassword = p_AdminPassword AND UserTypeID = 5;
  
  
  IF v_AdminID IS NOT NULL THEN
    SELECT UserStatusID INTO v_StatusID
    FROM UserStatus
    WHERE StatusName = p_NewStatus;
    
    IF v_StatusID IS NOT NULL THEN
      UPDATE User
      SET UserStatusID = v_StatusID
      WHERE Username = p_Username;
    END IF;
  END IF;
END €€
DELIMITER ;

CALL UpdateUserStatus('Benjamín', 'Inactive', 'adminpass');

```
##### D)
```
DELIMITER €€
DROP PROCEDURE IF EXISTS ListUsersByType €€
CREATE PROCEDURE ListUsersByType (
  IN p_UserType VARCHAR(255),
  IN p_AdminPassword VARCHAR(255)
)
BEGIN
  DECLARE v_AdminID INT;
  DECLARE v_UserTypeID INT;
  
  SELECT UserID INTO v_AdminID
  FROM User
  WHERE Username = 'admin' AND UserPassword = p_AdminPassword AND UserTypeID = 5;
  
  
  IF v_AdminID IS NOT NULL THEN
    SELECT UserTypeID INTO v_UserTypeID
    FROM UserType
    WHERE TypeName = p_UserType;
   
    IF v_UserTypeID IS NOT NULL THEN
      SELECT *
      FROM User
      WHERE UserTypeID = v_UserTypeID;
    END IF;
  END IF;
END €€
DELIMITER ;

CALL ListUsersByType('Super user', 'adminpass');
```
#### Liður 4
##### A)
```
DELIMITER €€
DROP FUNCTION IF EXISTS CountUserProblems €€
CREATE FUNCTION CountUserProblems (
  p_Username VARCHAR(255)
) RETURNS INT
READS SQL DATA
BEGIN
  DECLARE v_ProblemCount INT;
  
  SELECT COUNT(*) INTO v_ProblemCount
  FROM Problem
  WHERE UserID = (
    SELECT UserID
    FROM User
    WHERE Username = p_Username
  );
  
  RETURN v_ProblemCount;
END €€
DELIMITER ;

SELECT CountUserProblems('Bósi');
```
##### B)
SELECT CountUserProblems('Bósi');
```
DELIMITER €€
DROP FUNCTION IF EXISTS CountUserSolutions €€
CREATE FUNCTION CountUserSolutions (
  p_Username VARCHAR(255)
) RETURNS INT
READS SQL DATA
BEGIN
  DECLARE v_SolutionCount INT;
  
  SELECT COUNT(*) INTO v_SolutionCount
  FROM Solution
  WHERE UserID = (
    SELECT UserID
    FROM User
    WHERE Username = p_Username
  );
  
  RETURN v_SolutionCount;
END €€
DELIMITER ;

SELECT CountUserSolutions('Bósi');
SELECT CountUserProblems('Bósi');
```
##### C)
```
DELIMITER €€
DROP FUNCTION IF EXISTS IsAdmin €€
CREATE FUNCTION IsAdmin (
  p_Username VARCHAR(255)
) RETURNS BOOLEAN
READS SQL DATA
BEGIN
  DECLARE v_IsAdmin BOOLEAN;
  
  SELECT CASE
    WHEN UserTypeID = 5 THEN TRUE
    ELSE FALSE
  END INTO v_IsAdmin
  FROM User
  WHERE Username = p_Username;
  
  RETURN v_IsAdmin;
END €€
DELIMITER ;

select IsAdmin('Bósi'); -- Skilar 0
select IsAdmin('admin'); -- Skilar 1
```
