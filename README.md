馃憠馃徏*Wy艣wietl tabel臋 actors w kolejno艣ci alfabetycznej sortuj膮c po kolumnie surname*

SELECT * <br />
FROM actors<br />
ORDER BY surname


![alt text](https://github.com/hernika/challenge_portfolio_ola/blob/main/Task5/Subtask3/Images/1.png)

馃憠馃徏*Wy艣wietl film, kt贸ry powsta艂 w 2019 roku*

SELECT * <br />
FROM movies<br />
WHERE year_of_production = 2019

![alt text](https://github.com/hernika/challenge_portfolio_ola/blob/main/Task5/Subtask3/Images/2.png)

馃憠馃徏*Wy艣wietl wszystkie filmy, kt贸re powsta艂y mi臋dzy 1900, a 1999 rokiem*

SELECT * <br />
FROM movies<br />
WHERE year_of_production BETWEEN 1900 AND 1999

![alt text](https://github.com/hernika/challenge_portfolio_ola/blob/main/Task5/Subtask3/Images/3.png)

馃憠馃徏*Wy艣wietl JEDYNIE tytu艂 i cen臋 film贸w, kt贸re kosztuj膮 poni偶ej 7$*

SELECT title, price<br />
FROM movies<br />
WHERE price < 7

![alt text](https://github.com/hernika/challenge_portfolio_ola/blob/main/Task5/Subtask3/Images/4.png)

馃憠馃徏*U偶yj operatora logicznego AND, aby wy艣wietli膰 aktor贸w o actor_id pomi臋dzy 4-7 (4 i
7 powinny si臋 wy艣wietla膰). NIE U呕YWAJ operatora BETWEEN*

SELECT * <br />
FROM actors<br />
WHERE actor_id >= 4 AND actor_id <= 7

![alt text](https://github.com/hernika/challenge_portfolio_ola/blob/main/Task5/Subtask3/Images/5.png)

馃憠馃徏*Wy艣wietl klient贸w o id 2,4,6 wykorzystaj do tego warunek logiczny*

SELECT * <br />
FROM customers<br />
WHERE (customer_id = 2 OR customer_id = 4 OR customer_id = 6)

![alt text](https://github.com/hernika/challenge_portfolio_ola/blob/main/Task5/Subtask3/Images/6.png)

馃憠馃徏*Wy艣wietl klient贸w o id 1,3,5 wykorzystaj do tego operator IN*

SELECT * <br />
FROM customers<br />
WHERE customer_id IN (1, 3, 5)

![alt text](https://github.com/hernika/challenge_portfolio_ola/blob/main/Task5/Subtask3/Images/7.png)


馃憠馃徏*Wy艣wietl dane wszystkich os贸b z tabeli 鈥榓ctors鈥?, kt贸rych imi臋 zaczyna si臋 od ci膮gu
鈥淎n鈥?*

SELECT * <br />
FROM actors<br />
WHERE name LIKE 'An%'

![alt text](https://github.com/hernika/challenge_portfolio_ola/blob/main/Task5/Subtask3/Images/8.png)

馃憠馃徏*Wy艣wietl dane klienta, kt贸ry nie ma podanego adresu email*

SELECT * <br />
FROM customers<br />
WHERE email IS null

![alt text](https://github.com/hernika/challenge_portfolio_ola/blob/main/Task5/Subtask3/Images/9.png)

馃憠馃徏*Wy艣wietl wszystkie filmy, kt贸rych cena wynosi powy偶ej 9$ oraz ich ID mie艣ci si臋
pomi臋dzy 2 i 8 movie_id*

SELECT * <br />
FROM movies<br />
WHERE price > 9 AND (movie_id BETWEEN 2 AND 8)

![alt text](https://github.com/hernika/challenge_portfolio_ola/blob/main/Task5/Subtask3/Images/10.png)


馃憠馃徏*Pope艂ni艂am b艂膮d wpisuj膮c nazwisko Ani Miler 鈥? wpisa艂am Muler. Znajd藕 i zastosuj funkcj臋, kt贸ra poprawi m贸j karko艂omny b艂膮d 馃檲*

UPDATE customers<br />
SET surname = 'Miler'<br />
WHERE customer_id = 3

![alt text](https://github.com/hernika/challenge_portfolio_ola/blob/main/Task6/Subtask1/Images/11.png)

馃憠馃徏*Pobra艂am za du偶o pieni臋dzy od klienta, kt贸ry kupi艂 w ostatnim czasie film o id 4. Korzystaj膮c z
funkcji join sprawd藕, jak ma na imi臋 klient i jakiego ma maila. W celu napisania mu wiadomo艣ci o
pomy艂ce fantastycznej szefowej*

SELECT customers.name, customers.email<br />
FROM customers<br />
INNER JOIN sale ON customers.customer_id = sale.customer_id<br />
WHERE sale.movie_id = 4

![alt text](https://github.com/hernika/challenge_portfolio_ola/blob/main/Task6/Subtask1/Images/12.png)

馃憠馃徏*Na pewno zauwa偶y艂_艣, 偶e sprzedawca zapomnia艂 wpisa膰 emaila klientce Patrycji. Uzupe艂nij ten
brak wpisuj膮c: pati@mail.com*

UPDATE customers<br />
SET email = 'pati@mail.com'<br />
WHERE customer_id = 4

![alt text](https://github.com/hernika/challenge_portfolio_ola/blob/main/Task6/Subtask1/Images/13.png)

馃憠馃徏*Dla ka偶dego zakupu wy艣wietl, imi臋 i nazwisko klienta, kt贸ry dokona艂 wypo偶yczenia oraz tytu艂
wypo偶yczonego filmu. (wykorzystaj do tego funkcj臋 inner join, zastan贸w si臋 wcze艣niej, kt贸re tabele Ci
si臋 przydadz膮 do wykonania 膰wiczenia)*

SELECT customers.name, customers.surname, movies.title<br />
FROM customers<br />
INNER JOIN sale ON customers.customer_id = sale.customer_id<br />
INNER JOIN movies ON movies.movie_id = sale.movie_id

![alt text](https://github.com/hernika/challenge_portfolio_ola/blob/main/Task6/Subtask1/Images/14.png)

馃憠馃徏*W celu anonimizacji danych, chcesz stworzy膰 pseudonimy swoich klient贸w. - Dodaj kolumn臋 o
nazwie 鈥榩seudonym鈥? do tabeli customer,- Wype艂nij kolumn臋 w taki spos贸b, aby pseudonim stworzy艂
si臋 z dw贸ch pierwszych liter imienia i ostatniej litery nazwiska. Np. Natalie Pilling 鈫? Nag*

ALTER TABLE customers<br />
ADD pseudonym char(3);<br />
UPDATE customers SET pseudonym = CONCAT(LEFT(customers.name, 2), RIGHT(customers.surname,
1))

![alt text](https://github.com/hernika/challenge_portfolio_ola/blob/main/Task6/Subtask1/Images/15.png)

馃憠馃徏*Wy艣wietl tytu艂y film贸w, kt贸re zosta艂y zakupione, wy艣wietl tabel臋 w taki spos贸b, aby tytu艂y si臋 nie
powtarza艂y*

SELECT DISTINCT movies.title<br />
FROM movies<br />
INNER JOIN sale ON sale.movie_id=movies.movie_id

![alt text](https://github.com/hernika/challenge_portfolio_ola/blob/main/Task6/Subtask1/Images/16.png)

馃憠馃徏*Wy艣wietl wsp贸ln膮 list臋 imion wszystkich aktor贸w i klient贸w, a wynik uporz膮dkuj alfabetycznie.
(Wykorzystaj do tego funkcji UNION)*

SELECT name FROM customers<br />
UNION<br />
SELECT name FROM actors<br />
ORDER BY name ASC

![alt text](https://github.com/hernika/challenge_portfolio_ola/blob/main/Task6/Subtask1/Images/17.png)

馃憠馃徏*Polsk臋 opanowa艂a inflacja i nasz sklepik z filmami r贸wnie偶 dotkn膮艂 ten problem. Podnie艣 cen臋
wszystkich film贸w wyprodukowanych po 2000 roku o 2,5 $ (Pami臋taj, 偶e dolar to domy艣lna
jednostka- nie u偶ywaj jej nigdzie)*

UPDATE movies<br />
SET price = price + 2.5<br />
WHERE movies.year_of_production>2000

![alt text](https://github.com/hernika/challenge_portfolio_ola/blob/main/Task6/Subtask1/Images/18.png)

馃憠馃徏*Wy艣wietl imi臋 i nazwisko aktora o id 4 i tytu艂 filmu, w kt贸rym zagra艂*

SELECT actors.name, actors.surname, movies.title<br />
FROM actors<br />
INNER JOIN cast ON cast.actor_id = actors.actor_id<br />
INNER JOIN movies ON movies.movie_id = cast.movie_id<br />
WHERE actors.actor_id = 4

![alt text](https://github.com/hernika/challenge_portfolio_ola/blob/main/Task6/Subtask1/Images/19.png)

馃憠馃徏*A gdzie nasza HONIA!? Dodaj do tabeli customers now膮 krotk臋, gdzie customer_id = 7, name =
Honia, surname = Stuczka-Kucharska, email = honia@mail.com oraz pseudonym = Hoa*

INSERT INTO customers (customer_id, name, surname, email, pseudonym)<br />
VALUES (7, 'Honia', 'Stuczka-Kucharska', 'honia@mail.com', 'Hoa')

![alt text](https://github.com/hernika/challenge_portfolio_ola/blob/main/Task6/Subtask1/Images/20.png)




