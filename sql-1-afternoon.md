# Person   

1.
 create table person (
	id serial primary key,
  name char(30),
  age int,
  height int,
  city text,
  favorite_color text
);

2.
insert into person
(name, favorite_color, city, height, age)
values
('George', 'maroon', 'Seattle', 182, 28),
('Lisa', 'blue', 'New Orleans', 150, 60),
('Nathaniel', 'burnt umber', 'Chicago', 167, 43),
('Harry', 'red', 'New York', 169, 54),
('Kiddo', 'orange', 'Fort Worth', 100, 8);

3.
select * from person
	order by height desc;

4.
select * from person
	order by height asc;

5.
select * from person
	order by age desc;

6.
select * from person
	where age > 20;

7.
select * from person
	where age = 18;

8.
select * from person
	where age < 20
  or age > 30;

9.
select * from person
	where age != 27;

10.
select * from person
	where favorite_color != 'red';

11.
select * from person
	where favorite_color != 'red'
  and favorite_color != 'blue';

12.
select * from person
	where favorite_color = 'orange'
  or favorite_color = 'green';

13.
select * from person
	where favorite_color in ('orange', 'green', 'blue');

14.
select * from person
	where favorite_color in ('yellow', 'purple');

# Table-orders
1.
create table orders (
  order_id serial primary key,
  person_id int,
  product_name text,
  product_price float,
  quantity int
  );

2.
insert into orders 
(product_price, quantity, person_id, product_name)
values
(12.50, 2, 1, 'squatty potty'),
(5.99, 4, 1, 'notebook'),
(3.99, 2, 2, 'fancy pen'),
(7.99, 1, 1, 'extention cord'),
(999.95, 1, 2, 'arcteryx clothing item');

3.
select * from orders;

4.
select sum(quantity) from orders;

5.
select order_id, sum(product_price* quantity) from orders
 group by order_id;		

6.
select person_id, sum(product_price * quantity) from orders
	group by person_id;
  
# Table- artist

1.
insert into artist 
(artist_id, name)
values
(276, 'Bonobo'),
(277, 'Jaques Green'),
(278, 'Justice');

select * from artist;

2.
select * from artist
	order by name desc
  limit 10;

3.
select * from artist
	order by name asc
  limit 5;

4.
select * from artist
	where name like 'Black%';

5.
select * from artist
 where name like '%Black%';

# Table - employee

1.
select first_name, last_name from employee
	where city = 'Calgary';

2.
select first_name, last_name, min(birth_date) from employee
	group by first_name, last_name;

3.
select first_name, last_name, max(birth_date) from employee
	group by first_name, last_name;

4.
select employee_id from employee
	where first_name = 'Nancy'
  and last_name = 'Edwards';
  
 select first_name, last_name, employee_id from employee
 	where reports_to = 2
  group by first_name, last_name, employee_id;

5.
select count(employee_id) from employee
	where city = 'Lethbridge';

# Table - invoice

1.
select count(invoice_id) from invoice;

2.
select max(total) from invoice;

3.
select min(total) from invoice;

4.
select * from invoice
 	where total > 5;

5.
select count(invoice_id) from invoice
 	where total < 5;

6.
select count(invoice_id) from invoice
	where billing_state in ('CA', 'TX', 'AZ');

7.
select avg(total) from invoice;

8.
select sum(total) from invoice;
  