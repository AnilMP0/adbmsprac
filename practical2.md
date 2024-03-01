1-> USING (practical 1)

1. Count the customers with grades above Bangalore’s average. 
mysql> select count(*) as Average_Count from customer where grade > (select avg(grade) from customer where city = "New York");
+---------------+
| Average_Count |
+---------------+
|             5 |
+---------------+
1 row in set (0.00 sec)

2. Find the name and numbers of all salesmen who had more than one customer. 
mysql> select salesman_id,name from salesman a where 1<(select count(*) from
    -> customer where salesman_id=a.salesman_id);
+-------------+------------+
| salesman_id | name       |
+-------------+------------+
| 5001        | James Hoog |
| 5002        | Nail Knite |
+-------------+------------+
2 rows in set (0.01 sec)

3. List all salesmen and indicate those who have and don’t have customers in their cities (Use UNION operation.) 
mysql> ALTER TABLE orders
    -> ADD CONSTRAINT fk_salesman_id
    -> FOREIGN KEY (salesman_id)
    -> REFERENCES salesman(salesman_id)
    -> ON DELETE CASCADE;
Query OK, 12 rows affected (0.22 sec)
Records: 12  Duplicates: 0  Warnings: 0

mysql> DELETE FROM salesman where salesman_id = 5001;
Query OK, 1 row affected (0.01 sec)

2-> Write SQL queries to:
1. List the titles of all movies directed by ‘Hitchcock’. 
select mov_title from movies where dir_id =
(select dir_id from director where dir_name = 'HITCHCOCK') 

2. Find the movie names where one or more actors acted in two or more movies.
select m.mov_title
    from movies m
    natural join movie_cast mc
     where act_id in (select act_id
     from movie_cast
     group by act_id
     having count(act_id)>1)
     group by mov_title
     having count(*) > 1;

3. List all actors who acted in a movie before 2000 and also in a movie after 2015 (use JOIN operation). 
select distinct act_name
from (actor join movie_cast using(act_id)) join movies using(mov_id)
where mov_year not between 2000 and 2015;

4. Find the title of movies and number of stars for each movie that has at least one rating and find the highest number of stars that movie received. Sort the result by movie title.
select mov_title , max(rev_stars)
from movies natural join rating
group by mov_title
order by mov_title;

5. Update rating of all movies directed by ‘Steven Spielberg’ to 5.
update rating set rev_stars = 5
where mov_id in ( select mov_id 
from director natural join movies
where dir_name = 'STEVEN SPIELBERG'
 );  