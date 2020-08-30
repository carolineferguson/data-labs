![Ironhack logo](https://i.imgur.com/1QgrNNw.png)

# Lab | My First Queries

Open the PgAdmin server from PostgreSQL - pgAdmin 4 is a server that runs on a browser, which is pretty good for an easy start. If you haven't already, start a new server by passing the password you've setup. Create a database called **applestore** and use the `dump file` provided to import a database. 

After creating the `applestore` database, right click it and `restore` it. Select the dump file and hopefully pgAdmin will create the database needed for the following exercises.

Use the table to query the data about Apple Store Apps and answer the following questions: 

**1. What are the different genres?**
SELECT DISTINCT(prime_genre) from data;
**2. Which is the genre with the most apps rated?**
The count of ratings an app has received is in the rating_count_tot column.
SELECT prime_genre FROM DATA WHERE data.rating_count_tot = (SELECT MAX(rating_count_tot) FROM DATA);
**3. Which is the genre with most apps?**
SELECT prime_genre,COUNT(*) FROM data GROUP BY prime_genre; 
games
**4. Which is the one with least?**
catalogs
**5. Find the top 10 apps most rated.**
SELECT track_name FROM data ORDER BY rating_count_tot DESC LIMIT 10;
**6. Find the top 10 apps best rated by users.**
SELECT track_name FROM data ORDER BY user_rating DESC LIMIT 10;
**7. Take a look at the data you retrieved in question 5. Give some insights.**
3 de social media,4 de games,2 de musica.
**8. Take a look at the data you retrieved in question 6. Give some insights.**
9 de games.
**9. Now compare the data from questions 5 and 6. What do you see?**
diferença de generos
**10. How could you take the top 3 regarding both user ratings and number of votes?**
SELECT track_name FROM DATA ORDER BY user_rating,rating_count_tot DESC LIMIT 3;
**11. Do people care about the price of an app?** Do some queries, comment why are you doing them and the results you retrieve. What is your conclusion?
SELECT track_name,price FROM data ORDER BY rating_count_tot DESC LIMIT 20;
--dos 20 apenas 3 são pagos
**Bonus: Find the total number of games available in more than 1 language.**
SELECT prime_genre,COUNT(*) FROM DATA WHERE lang > 1 GROUP BY prime_genre;
**Bonus2: Find the number of free vs paid apps**
SELECT COUNT(price) FROM DATA WHERE price >0;
SELECT COUNT(price) FROM DATA WHERE price=0;
**Bonus3: Find the number of free vs paid apps for each genre**
SELECT COUNT(price) FROM DATA WHERE price >0 GROUP BY prime_genre;
SELECT COUNT(price) FROM DATA WHERE price=0 GROUP BY prime_genre;

## Deliverables 
You need to submit a `.sql` file that includes the queries used to answer the questions above, as well as an `.md` file including your answers. 
