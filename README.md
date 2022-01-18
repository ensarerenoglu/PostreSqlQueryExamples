# PostreSqlQueryExamples
- dvdrental 
- film tablosunda bulunan title ve description sütunlarındaki verileri sıralayınız.
    - `select title, description from film;`
- film tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük VE 75 ten küçük olma koşullarıyla sıralayınız.
    - `select * from film f where f.length >60 and f.length <75;`
- film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 VE replacement_cost 12.99 VEYA 28.99 olma koşullarıyla sıralayınız.
    - `select * from film f where f.rental_rate = 0.99 and (f.replacement_cost = 12.99 or f.replacement_cost = 28.99); `
- customer tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir?
    - `select c.last_name from customer c where c.first_name = 'Mary';`
- film tablosundaki uzunluğu(length) 50 ten büyük OLMAYIP aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız.
    - `select * from film f where not (f.length < 50 and (f.rental_rate = 2.99 or f.rental_rate = 4.99))`
- film tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla sıralayınız ( BETWEEN - AND yapısını kullanınız.)
    - `select * from film f where f.replacement_cost between 12.99 and 16.98 order by f.replacement_cost desc`
- .actor tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız. ( IN operatörünü kullanınız.)
    - `select first_name, last_name from actor where first_name in('Penelope','Nick','Ed');`
- film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 VE replacement_cost 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız. ( IN operatörünü kullanınız.)
    - `select * from film f where f.rental_rate IN(0.99,2.99,4.99) and f.replacement_cost IN(12.99,15.99,28.99);`
- country tablosunda bulunan country sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız.
    - `select * from country c where c.country like 'A%a';`
- country tablosunda bulunan country sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.
    - `select * from country c where c.country like '______%' and c.country like '%a';`
- film tablosunda bulunan title sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren film isimlerini sıralayınız.
    - `select * from film f where f.title ILike '%t%t%t%t%';`
- film tablosunda bulunan tüm sütunlardaki verilerden title 'C' karakteri ile başlayan ve uzunluğu (length) 90 dan büyük olan ve rental_rate 2.99 olan verileri sıralayınız.
    - `select * from film f where f.title Like 'C%' and f.length > 90 and f.rental_rate=2.99;`;
- film tablosunda bulunan replacement_cost sütununda bulunan birbirinden farklı değerleri sıralayınız.
    - `select DISTINCT REPLACEMENT_COST FROM FILM ORDER BY REPLACEMENT_COST;` 
- film tablosunda bulunan replacement_cost sütununda birbirinden farklı kaç tane veri vardır?,
    - `select COUNT(DISTINCT REPLACEMENT_COST) FROM FILM;`
- film tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?
    - `select COUNT(DISTINCT title) from film f where f.title ILIKE 'T%' and f.rating = 'G';` 
- country tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?
    - `select Count(country) from country where country ILIKE '_____';`
- city tablosundaki şehir isimlerinin kaç tanesi 'R' veya r karakteri ile biter?
    - `select Count(city) from city where city ILIKE '%r';` 
- film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en uzun (length) 5 filmi sıralayınız.
    - `select * from film f where f.title ILIKE '%n' order by f.length desc limit 5;` 
- film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en kısa (length) ikinci(6,7,8,9,10) 5 filmi(6,7,8,9,10) sıralayınız.
    - `select * from film f where f.title ILIKE '%n' order by f.length offset 5 limit 5;`   
- customer tablosunda bulunan last_name sütununa göre azalan yapılan sıralamada store_id 1 olmak koşuluyla ilk 4 veriyi sıralayınız.
    - `select * from customer c where c.store_id = 1 order by last_name desc limit 4;` 
- film tablosunda bulunan rental_rate sütunundaki değerlerin ortalaması nedir?
    - `select ROUND(AVG(rental_rate)) from film;`
- film tablosunda bulunan filmlerden kaç tanesi 'C' karakteri ile başlar?
    - `select Count(title) from film f where f.title ILIKE 'c%';` 
- film tablosunda bulunan filmlerden rental_rate değeri 0.99 a eşit olan en uzun (length) film kaç dakikadır?
    - `select MAX(length) from film f where f.rental_rate = 0.99;` 
- film tablosunda bulunan filmlerin uzunluğu 150 dakikadan büyük olanlarına ait kaç farklı replacement_cost değeri vardır?
    - `select Count(Distinct replacement_cost) from film f where f.length > 150;` 
- film tablosunda bulunan filmleri rating değerlerine göre gruplayınız.
    - `select rating , Count(*) from film f Group by f.rating;`
- film tablosunda bulunan filmleri replacement_cost sütununa göre grupladığımızda film sayısı 50 den fazla olan replacement_cost değerini ve karşılık gelen film sayısını sıralayınız.
    - `select replacement_cost, Count(*) from film f Group by f.replacement_cost having Count(*) >50 Order By f.replacement_cost; ` 
- customer tablosunda bulunan store_id değerlerine karşılık gelen müşteri sayılarını nelerdir? 
    - `select c.store_id, Count(Distinct customer_id) from customer c Group by c.store_id;` 
- city tablosunda bulunan şehir verilerini country_id sütununa göre gruplandırdıktan sonra en fazla şehir sayısı barındıran country_id bilgisini ve şehir sayısını paylaşınız.
    - `select country_id, Count(Distinct city) from city c group by c.country_id order by Count(Distinct city) desc limit 1;`
- test veritabanınızda employee isimli sütun bilgileri id(INTEGER), name VARCHAR(50), birthday DATE, email VARCHAR(100) olan bir tablo oluşturalım.
    - ```Create Table employee(
	id serial Primary Key,
	name Varchar(50) not null,
	birthday Date,
	email Varchar(100)
);``` 
- Oluşturduğumuz employee tablosuna 'Mockaroo' servisini kullanarak 50 adet veri ekleyelim.
    - `insert into employee (name, birthday, email) values ('Stern', '2016-07-17', 'sfehnersx@xrea.com');` 
- Sütunların her birine göre diğer sütunları güncelleyecek 5 adet UPDATE işlemi yapalım.
    - `Update employee 
set name = 'Ensar', birthday = '1900-12-01', email = 'ensar@ensar.com'
where Id = 1 ;` 
- Sütunların her birine göre ilgili satırı silecek 5 adet DELETE işlemi yapalım.
    - `Delete from employee where Id=1;`

