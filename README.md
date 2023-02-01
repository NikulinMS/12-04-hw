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

### Задание 4

`Приведите ответ в свободной форме........`

1. `Заполните здесь этапы выполнения, если требуется ....`
2. `Заполните здесь этапы выполнения, если требуется ....`
3. `Заполните здесь этапы выполнения, если требуется ....`
4. `Заполните здесь этапы выполнения, если требуется ....`
5. `Заполните здесь этапы выполнения, если требуется ....`
6. 

```
Поле для вставки кода...
....
....
....
....
```

`При необходимости прикрепитe сюда скриншоты
![Название скриншота](ссылка на скриншот)`

---
## Дополнительные задания (со звездочкой*)


### Задание 5

`Приведите ответ в свободной форме........`

1. `Заполните здесь этапы выполнения, если требуется ....`
2. `Заполните здесь этапы выполнения, если требуется ....`
3. `Заполните здесь этапы выполнения, если требуется ....`
4. `Заполните здесь этапы выполнения, если требуется ....`
5. `Заполните здесь этапы выполнения, если требуется ....`
6. 

`При необходимости прикрепитe сюда скриншоты
![Название скриншота](ссылка на скриншот)`
