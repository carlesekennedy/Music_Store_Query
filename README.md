# Music_Store_Query
Query a Digital Music Store Database

For Query 1, I wanted to know the album/artist thatsold the most copies. Here was the query I ran:
/* Query 1 - query used for first insight /
SELECT a.Name Artist,
       al.title album,
       SUM(i.quantity) total_copies_sold
FROM Artist a
JOIN album al ON a.ArtistId = al.ArtistId
JOIN Track t ON al.AlbumId = t.AlbumId
JOIN InvoiceLine i ON t.TrackId = i.TrackId
GROUP BY Album
ORDER BY total_copies_sold DESC
LIMIT 5;

For Query 2, I wanted to know the sales agent that had the highest total sales revenue. I found the answer by running this query:
/* Query 2 - query used for second insight /
SELECT e.firstname FirstName,
       e.lastname LastName,
       e.title Job_Title,
       SUM(i.total) Total_Sales_Revenue
FROM employee e
JOIN customer c ON e.employeeid = c.supportrepid
JOIN invoice i ON c.customerid = i.customerid
GROUP BY e.FirstName,
         e.LastName,
         e.title
ORDER BY Total_Sales_Revenue DESC;

For Query 3, I wanted to know the genre that had the highest total sales revenue so I ran this query:
/* Query 3 - query used for third insight /
SELECT g.Name Genre,
       sum(il.Unitprice * il.quantity) Total_Revenue_Sales
FROM Genre g
JOIN Track t ON g.GenreId = t.GenreId
JOIN InvoiceLine il ON il.TrackId = t.TrackId
JOIN Invoice i ON i.InvoiceId = il.InvoiceId
GROUP BY Genre
ORDER BY Total_Revenue_Sales DESC;

For Query 4, I wanted to know the artist that had the most tracks featured in playlists. Here is the query I ran to find the answer:
/* Query 4 - query used for fourth insight /
SELECT a.name Artist,
       COUNT(t.trackid) Num_Tracks_Featured
FROM PlaylistTrack p
JOIN Track t ON p.trackid = t.trackid
JOIN Album al ON t.albumid = al.albumid
JOIN Artist a ON al.artistid = a.artistid
GROUP BY Artist
ORDER BY Num_Tracks_Featured DESC
LIMIT 10;
