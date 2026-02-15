# Домашнее задание к занятию "Расширенные возможности SQL" - Борзенков Валерий


---

### Задание 1

`select
	s.first_name,
	s.last_name,
	c.city,
	customer_count.total_customers
from (
	select
		store_id,
		count(*) as total_customers
	from sakila.customer
	group by store_id
	having count(*) > 300
) as customer_count
join sakila.staff s on s.store_id = customer_count.store_id
join sakila.store st on st.store_id = customer_count.store_id
join sakila.address a on a.address_id = st.address_id
join sakila.city c on c.city_id = a.city_id;`

![img.png](img/img.png)

---

### Задание 2

`SELECT COUNT(*) AS films_count
FROM sakila.film
WHERE length > (SELECT AVG(length) FROM sakila.film);`

![img.png](img/img_1.png)
---

### Задание 3

`SELECT 
    YEAR(payment_date) AS year,
    MONTH(payment_date) AS month,
    SUM(amount) AS total_amount,
    COUNT(*) AS rental_count
FROM sakila.payment
GROUP BY YEAR(payment_date), MONTH(payment_date)
ORDER BY total_amount DESC
LIMIT 1;`

![img.png](img/img_2.png)
