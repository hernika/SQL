👉🏼*Wyświetl tabelę actors w kolejności alfabetycznej sortując po kolumnie surname*

SELECT * <br />
FROM actors<br />
ORDER BY surname


![alt text](https://github.com/hernika/challenge_portfolio_ola/blob/main/Task5/Subtask3/Images/1.png)

👉🏼*Wyświetl film, który powstał w 2019 roku*

SELECT * <br />
FROM movies<br />
WHERE year_of_production = 2019

![alt text](https://github.com/hernika/challenge_portfolio_ola/blob/main/Task5/Subtask3/Images/2.png)

👉🏼*Wyświetl wszystkie filmy, które powstały między 1900, a 1999 rokiem*

SELECT * <br />
FROM movies<br />
WHERE year_of_production BETWEEN 1900 AND 1999

![alt text](https://github.com/hernika/challenge_portfolio_ola/blob/main/Task5/Subtask3/Images/3.png)

👉🏼*Wyświetl JEDYNIE tytuł i cenę filmów, które kosztują poniżej 7$*

SELECT title, price<br />
FROM movies<br />
WHERE price < 7

![alt text](https://github.com/hernika/challenge_portfolio_ola/blob/main/Task5/Subtask3/Images/4.png)

👉🏼*Użyj operatora logicznego AND, aby wyświetlić aktorów o actor_id pomiędzy 4-7 (4 i
7 powinny się wyświetlać). NIE UŻYWAJ operatora BETWEEN*

SELECT * <br />
FROM actors<br />
WHERE actor_id >= 4 AND actor_id <= 7

![alt text](https://github.com/hernika/challenge_portfolio_ola/blob/main/Task5/Subtask3/Images/5.png)

👉🏼*Wyświetl klientów o id 2,4,6 wykorzystaj do tego warunek logiczny*

SELECT * <br />
FROM customers<br />
WHERE (customer_id = 2 OR customer_id = 4 OR customer_id = 6)

![alt text](https://github.com/hernika/challenge_portfolio_ola/blob/main/Task5/Subtask3/Images/6.png)

👉🏼*Wyświetl klientów o id 1,3,5 wykorzystaj do tego operator IN*

SELECT * <br />
FROM customers<br />
WHERE customer_id IN (1, 3, 5)

![alt text](https://github.com/hernika/challenge_portfolio_ola/blob/main/Task5/Subtask3/Images/7.png)


👉🏼*Wyświetl dane wszystkich osób z tabeli ‘actors’, których imię zaczyna się od ciągu
“An”*

SELECT * <br />
FROM actors<br />
WHERE name LIKE 'An%'

![alt text](https://github.com/hernika/challenge_portfolio_ola/blob/main/Task5/Subtask3/Images/8.png)

👉🏼*Wyświetl dane klienta, który nie ma podanego adresu email*

SELECT * <br />
FROM customers<br />
WHERE email IS null

![alt text](https://github.com/hernika/challenge_portfolio_ola/blob/main/Task5/Subtask3/Images/9.png)

👉🏼*Wyświetl wszystkie filmy, których cena wynosi powyżej 9$ oraz ich ID mieści się
pomiędzy 2 i 8 movie_id*

SELECT * <br />
FROM movies<br />
WHERE price > 9 AND (movie_id BETWEEN 2 AND 8)

![alt text](https://github.com/hernika/challenge_portfolio_ola/blob/main/Task5/Subtask3/Images/10.png)


👉🏼*Popełniłam błąd wpisując nazwisko Ani Miler – wpisałam Muler. Znajdź i zastosuj funkcję, która poprawi mój karkołomny błąd 🙈*

UPDATE customers<br />
SET surname = 'Miler'<br />
WHERE customer_id = 3

![alt text](https://github.com/hernika/challenge_portfolio_ola/blob/main/Task6/Subtask1/Images/11.png)

👉🏼*Pobrałam za dużo pieniędzy od klienta, który kupił w ostatnim czasie film o id 4. Korzystając z
funkcji join sprawdź, jak ma na imię klient i jakiego ma maila. W celu napisania mu wiadomości o
pomyłce fantastycznej szefowej*

SELECT customers.name, customers.email<br />
FROM customers<br />
INNER JOIN sale ON customers.customer_id = sale.customer_id<br />
WHERE sale.movie_id = 4

![alt text](https://github.com/hernika/challenge_portfolio_ola/blob/main/Task6/Subtask1/Images/12.png)

👉🏼*Na pewno zauważył_ś, że sprzedawca zapomniał wpisać emaila klientce Patrycji. Uzupełnij ten
brak wpisując: pati@mail.com*

UPDATE customers<br />
SET email = 'pati@mail.com'<br />
WHERE customer_id = 4

![alt text](https://github.com/hernika/challenge_portfolio_ola/blob/main/Task6/Subtask1/Images/13.png)

👉🏼*Dla każdego zakupu wyświetl, imię i nazwisko klienta, który dokonał wypożyczenia oraz tytuł
wypożyczonego filmu. (wykorzystaj do tego funkcję inner join, zastanów się wcześniej, które tabele Ci
się przydadzą do wykonania ćwiczenia)*

SELECT customers.name, customers.surname, movies.title<br />
FROM customers<br />
INNER JOIN sale ON customers.customer_id = sale.customer_id<br />
INNER JOIN movies ON movies.movie_id = sale.movie_id

![alt text](https://github.com/hernika/challenge_portfolio_ola/blob/main/Task6/Subtask1/Images/14.png)

👉🏼*W celu anonimizacji danych, chcesz stworzyć pseudonimy swoich klientów. - Dodaj kolumnę o
nazwie ‘pseudonym’ do tabeli customer,- Wypełnij kolumnę w taki sposób, aby pseudonim stworzył
się z dwóch pierwszych liter imienia i ostatniej litery nazwiska. Np. Natalie Pilling → Nag*

ALTER TABLE customers<br />
ADD pseudonym char(3);<br />
UPDATE customers SET pseudonym = CONCAT(LEFT(customers.name, 2), RIGHT(customers.surname,
1))

![alt text](https://github.com/hernika/challenge_portfolio_ola/blob/main/Task6/Subtask1/Images/15.png)

👉🏼*Wyświetl tytuły filmów, które zostały zakupione, wyświetl tabelę w taki sposób, aby tytuły się nie
powtarzały*

SELECT DISTINCT movies.title<br />
FROM movies<br />
INNER JOIN sale ON sale.movie_id=movies.movie_id

![alt text](https://github.com/hernika/challenge_portfolio_ola/blob/main/Task6/Subtask1/Images/16.png)

👉🏼*Wyświetl wspólną listę imion wszystkich aktorów i klientów, a wynik uporządkuj alfabetycznie.
(Wykorzystaj do tego funkcji UNION)*

SELECT name FROM customers<br />
UNION<br />
SELECT name FROM actors<br />
ORDER BY name ASC

![alt text](https://github.com/hernika/challenge_portfolio_ola/blob/main/Task6/Subtask1/Images/17.png)

👉🏼*Polskę opanowała inflacja i nasz sklepik z filmami również dotknął ten problem. Podnieś cenę
wszystkich filmów wyprodukowanych po 2000 roku o 2,5 $ (Pamiętaj, że dolar to domyślna
jednostka- nie używaj jej nigdzie)*

UPDATE movies<br />
SET price = price + 2.5<br />
WHERE movies.year_of_production>2000

![alt text](https://github.com/hernika/challenge_portfolio_ola/blob/main/Task6/Subtask1/Images/18.png)

👉🏼*Wyświetl imię i nazwisko aktora o id 4 i tytuł filmu, w którym zagrał*

SELECT actors.name, actors.surname, movies.title<br />
FROM actors<br />
INNER JOIN cast ON cast.actor_id = actors.actor_id<br />
INNER JOIN movies ON movies.movie_id = cast.movie_id<br />
WHERE actors.actor_id = 4

![alt text](https://github.com/hernika/challenge_portfolio_ola/blob/main/Task6/Subtask1/Images/19.png)

👉🏼*A gdzie nasza HONIA!? Dodaj do tabeli customers nową krotkę, gdzie customer_id = 7, name =
Honia, surname = Stuczka-Kucharska, email = honia@mail.com oraz pseudonym = Hoa*

INSERT INTO customers (customer_id, name, surname, email, pseudonym)<br />
VALUES (7, 'Honia', 'Stuczka-Kucharska', 'honia@mail.com', 'Hoa')

![alt text](https://github.com/hernika/challenge_portfolio_ola/blob/main/Task6/Subtask1/Images/20.png)




