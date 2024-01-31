# SQL-Ödev12

1. Film tablosunda film uzunluğu length sütununda gösterilmektedir. Uzunluğu ortalama film uzunluğundan fazla kaç tane film vardır?
```
SELECT COUNT(*) FROM film
WHERE length > 
(
	select AVG(length) from film
);
```
2. Film tablosunda en yüksek rental_rate değerine sahip kaç tane film vardır?
```
select count(*) from film
where rental_rate = any
(
	select max(rental_rate) from film
);
```
3. Film tablosunda en düşük rental_rate ve en düşün replacement_cost değerlerine sahip filmleri sıralayınız.
```
select * from film 
where rental_rate = any 
(
	select min(rental_rate) from film
) and
replacement_cost = any
(
	select min(replacement_cost) from film
);
```

4. Payment tablosunda en fazla sayıda alışveriş yapan müşterileri(customer) sıralayınız.
```
select distinct customer_id from payment
where amount = any
(
	select max(amount) from payment
);
```
