# mysql-exercise07-jcwdol011

```sql
-- select * from actor

-- SELECT film_actor.actor_id , film_id , last_update, 
-- (SELECT actor.first_name FROM actor WHERE film_actor.actor_id  = actor.actor_id ) as actor_name  FROM film_actor WHERE film_id 
-- IN (SELECT film_id FROM film WHERE title = 'Alone Trip');

SELECT * from city where country_id 
IN (SELECT country_id from country where country IN 
(select c.country from country c where c.country_id BETWEEN 1 and 3));

select country from country where country_id BETWEEN 1 and 3

SELECT * FROM actor where last_name LIKE '%OD%' order by last_name , first_name asc;

alter table actor add column middle_name varchar(50) after first_name;

select last_name , count(last_name) as lastname_count from actor group by last_name having lastname_count >= 2  ;

select s.first_name, s.last_name, a.address from staff s join address a 
on a.address_id  = s.address_id;


select f.film_id, f.title, count(i.inventory_id) from film f join inventory i 
on f.film_id = i.film_id 
where f.title = 'Hunchback Impossible'
group by film_id

select f.film_id, f.title, count(r.rental_id) as rental_count from 
film f join inventory i 
ON f.film_id = i.film_id
join rental r 
ON i.inventory_id = r.inventory_id
group by film_id
order by rental_count desc;

-- select a.actor_id, a.first_name , a.last_name from actor a
-- where a.actor_id IN (
-- 	select fa.actor_id from film_actor fa where fa.film_id IN (
-- 		select film.film_id from film where film.title  = 'Alone Trip'
-- 	)
-- );

SELECT a.actor_id, a.first_name , a.last_name from actor a
where a.actor_id IN (3,12,13,82,100,160,167,187);

SELECT a.actor_id, a.first_name , a.last_name from actor a
where a.actor_id IN (
    -- 3,12,13,82,100,160,167,187
	SELECT fa.actor_id from film_actor fa WHERE fa.film_id IN (
	    -- 27
		SELECT f.film_id FROM film f WHERE f.title  = 'Alone Trip'
	)
);

select a.actor_id from actor a where a.actor_id IN (1,2,3);
```
