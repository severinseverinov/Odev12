# Patika Odev 12

### Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştirildi.

1. film tablosunda film uzunluğu length sütununda gösterilmektedir. Uzunluğu ortalama film uzunluğundan fazla kaç tane film vardır?
> SELECT COUNT(*) FROM film
WHERE length>(SELECT AVG(length) FROM film);

2. film tablosunda en yüksek rental_rate değerine sahip kaç tane film vardır?
> SELECT COUNT(*) FROM film
WHERE rental_rate=(SELECT MAX(rental_rate) FROM film);

3. film tablosunda en düşük rental_rate ve en düşük replacement_cost değerlerine sahip filmleri sıralayınız.
> SELECT title,(SELECT MIN(rental_rate) FROM film) AS rate, 
(SELECT MIN(replacement_cost) FROM film) AS replacement
FROM film;

4. payment tablosunda en fazla sayıda alışveriş yapan müşterileri(customer) sıralayınız.
> SELECT customer.customer_id,customer.first_name,customer.last_name, COUNT(payment_id) FROM payment 
JOIN customer ON customer.customer_id = payment.customer_id
GROUP BY customer.customer_id, customer.first_name,customer.last_name
ORDER BY COUNT(payment_id) DESC;
