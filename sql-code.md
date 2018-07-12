/_ ////PRACTICE JOINS//// _/
/_ SELECT _ FROM
Invoice
JOIN InvoiceLine ON InvoiceLine.invoiceId = Invoice.invoiceId
WHERE InvoiceLine.UnitPrice > .99 \*/

/_ SELECT i.invoiceDate, i.Total, c.FirstName, c.LastName
FROM Invoice i
JOIN Customer c ON i.CustomerID = c.CustomerId
_/

/_ SELECT c.FirstName, c.LastName, e.FirstName, e.LastName
FROM Customer c
JOIN Employee e ON c.SupportRepId = e.EmployeeId _/

/_ SELECT al.Title, ar.Name
FROM Album al
JOIN Artist ar ON al.ArtistId = ar.ArtistId _/

/_ SELECT pt.TrackId
FROM PlaylistTrack pt
JOIN Playlist p on p.PlaylistId = pt.PlaylistId
WHERE p.Name = 'Music' _/

/_ SELECT t.Name
FROM Track t
JOIN PlaylistTrack pt ON pt.TrackId = t.TrackId
WHERE pt.PlaylistId = 5 _/

/_ SELECT t.name, p.name
FROM Track t
JOIN PlaylistTrack pt ON t.TrackId = pt.TrackId
JOIN Playlist p ON pt.PlaylistId=p.PlaylistId _/

/_ SELECT t.Name, a.title
FROM Track t
JOIN Album a ON t.Albumid = a.AlbumId
JOIN Genre g ON g.GenreId = t.GenreId
WHERE g.name = "Alternative" _/

/_////PRACTICE NESTED QUERIES////_/

/_ SELECT _ FROM Invoice
WHERE InvoiceId IN (SELECT InvoiceId FROM InvoiceLine WHERE UnitPrice > 0.99) \*/

/_ SELECT _
FROM PlaylistTrack
WHERE PlaylistId IN (SELECT PlaylistId FROM Playlist WHERE Name = "Music") \*/

/_ SELECT Name
FROM Track
WHERE TrackId IN (SELECT TrackId FROM PlaylistTrack WHERE PlaylistId = 5) _/

/_ SELECT _
FROM Track
WHERE GenreId IN(SELECT GenreId FROM Genre WHERE Name ="Comedy") \*/

/_ SELECT _
FROM Track
WHERE AlbumId IN (SELECT AlbumId FROM Album WHERE Name="Fireball") \*/

/_ SELECT _
FROM Track
WHERE AlbumId IN (SELECT AlbumId FROM Album WHERE ArtistID IN
(SELECT ArtistId FROM Artist WHERE Name = "Queen")) \*/

/_ ////PRACTICE UPDATING ROWS//// _/
/\* CREATE TABLE practice_delete ( Name string, Type string, Value integer );
INSERT INTO practice_delete ( Name, Type, Value ) VALUES ("delete", "bronze", 50);
INSERT INTO practice_delete ( Name, Type, Value ) VALUES ("delete", "bronze", 50);
INSERT INTO practice_delete ( Name, Type, Value ) VALUES ("delete", "bronze", 50);
INSERT INTO practice_delete ( Name, Type, Value ) VALUES ("delete", "silver", 100);
INSERT INTO practice_delete ( Name, Type, Value ) VALUES ("delete", "silver", 100);
INSERT INTO practice_delete ( Name, Type, Value ) VALUES ("delete", "gold", 150);
INSERT INTO practice_delete ( Name, Type, Value ) VALUES ("delete", "gold", 150);
INSERT INTO practice_delete ( Name, Type, Value ) VALUES ("delete", "gold", 150);
INSERT INTO practice_delete ( Name, Type, Value ) VALUES ("delete", "gold", 150);

SELECT _ FROM practice_delete; _/

/_ DELETE FROM practice_delete WHERE Type = "bronze" _/

/_ DELETE FROM practice_delete WHERE Type = "silver" _/

/_ DELETE FROM practice_delete WHERE value = 150 _/

/_ //// eCOMMERCE SIM //// _/
/_ Create a table for users with name and email
CREATE TABLE Users
(ID INTEGER PRIMARY KEY AUTOINCREMENT,
Name string,
Email string) _/

/_ Create a table for products with prod name and price
CREATE TABLE Products
(ID INTEGER PRIMARY KEY AUTOINCREMENT,
ProductName string,
ProductPrice integer ) _/

/_ CREATE TABLE Orders(
OrderID integer,
ProductId REFERENCES Products(ID),
UsersId REFERENCES Users(ID) ) _/

/_ //// INSERT DATA INTO THE TABLES //// _/
/_ INSERT INTO Products(ProductName, ProductPrice)
VALUES("Tank", 100)
SELECT _ FROM Products
INSERT INTO Products(ProductName, ProductPrice)
VALUES("A-10", 200)
INSERT INTO Products(ProductName, ProductPrice)
VALUES("Boat", 500)

INSERT INTO Users(Name, Email)
VALUES("Blorb","Blorb@Blorb.Blorb")
INSERT INTO Users(Name, Email)
VALUES("Gob","Gob@Gob.Gob")
INSERT INTO Users(Name, Email)
VALUES("Yub","Yub@Yub.Yub")_/
/_ SELECT _ FROM Orders _/

/_ select _ from products \*/

/_ select _ from orders \*/

Select p.ProductPrice from products p join orders o on p.ID = o.ProductID join users u on o.usersid = u.ID where o.usersId = 2

/_ INSERT INTO Orders (OrderID, ProductId, UsersId)
VALUES (1, 1, 1),
(1, 2, 1),
(1, 3, 1) _/
