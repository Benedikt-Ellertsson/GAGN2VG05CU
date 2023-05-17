# GAGN2VG05CU
## Verkefni 5   || Enn í vinnslu
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
```
