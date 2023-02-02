# Домашнее задание к занятию "`SQL. Часть 2`" - `Никулин Михаил Сергеевич`



---

### Задание 1



```
select concat(s.first_name, ' ', s.last_name) as Staff, c2.city as City, count(c.customer_id) as Customers
from staff s 
join store s2 on s2.store_id = s.store_id 
join customer c on c.store_id = s2.store_id 
join address a on a.address_id = s2.address_id 
join city c2 on c2.city_id = a.city_id 
group by s.first_name , s.last_name , c2.city 
having Customers > 300
```

![task_1.png](img%2Ftask_1.png)


---

### Задание 2


```
select count(f.film_id) as 'Film count' 
from film f 
where f.`length` > (
select avg(f.`length`) 
from film f
);
```

![task_2.png](img%2Ftask_2.png)


---

### Задание 3



```
select month(p.payment_date) as Month , sum(p.amount) as Amount , count(p.amount) as 'Rental count'
from payment p 
group by month(p.payment_date)
order by Amount desc 
limit 1;
```

![task_3.png](img%2Ftask_3.png)



---
## Дополнительные задания (со звездочкой*)


### Задание 4*

```
select concat(s.first_name , ' ' , s.last_name) as Name , count(p.payment_id) as Payments ,
case
	when count(p.amount) > 8000 then 'Да'
	when count(p.amount) <= 8000 then 'Нет'
end as Премия, 
sum(p.amount) as Total
from payment p
join staff s on s.staff_id = p.staff_id 
where p.amount  > 0
group by Name;
```

![task_4.png](img%2Ftask_4.png)

---


### Задание 5*

`В базе данных все фильмы брали в аренду хотя бы 2 раза, запрос попытался 
написать с учетом, что появится фильм, который возьмут в аренду только 1 раз, 
тогда запрос в разделе with покажет лишний фильм.`

`Просьба пояснить, верная мысль или нет?`


```
with 
take as (
select count(f.title) as Number, f.film_id as id 
from film f 
left join inventory i on i.film_id = f.film_id 
left join rental r  on r.inventory_id = i.inventory_id
group by f.film_id  
having  Number = 1)

SELECT f.title, r.rental_id 
FROM film f
LEFT JOIN inventory i ON i.film_id = f.film_id
LEFT JOIN rental r ON r.inventory_id = i.inventory_id
right join take t on t.id = f.film_id 
WHERE t.Number = 1 and r.rental_id is null; 
```

![task_5.png](img%2Ftask_5.png)

---