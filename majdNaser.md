# week3day2HW
create database store;
create  table countries(
    code int primary key,
    name varchar(10) unique,
    continent_name varchar(20) not null

);
create table users
(
    id            int primary key,
    full_name     varchar(20),
    email         varchar(20) unique,
    gender        char(1) check ( gender = 'm' or gender = 'f' ),
    data_of_birth varchar(15),
    created_code  datetime,
    code_id       int,
    foreign key (code_id) references countries (code)


);

create table orders(
    id int primary key ,
    status varchar(6) check ( status='start' or 'finish' ),
    user_id  int,
    foreign key (user_id) references users(id),
    creates_at datetime

);
create table products (
    id int primary key ,
    name varchar(10) not null ,
    price int default 0,
    status varchar(10) check ( status= 'valid' or 'expired' ),
    created_at datetime


);

create table order_product(
    order_id int ,
    foreign key (order_id) references orders (id),
    product_id int ,
    foreign key (product_id) references products (id),
    quantity int default 0
);
insert into countries values (10123,'saudi','Asia');
insert into users values (1094,'majdNaser','majd@gmail','f','1996','8-8-2022 22:20:22',10123);
insert into orders values (111,1094,'start','11-8-2022 10:50:55');
insert into products values (5555,'watch','1000','valid','14-6-2022 20:20:20');
insert into order_product values (111,5555,1);
update countries set name='UAE' where code=10123;
delete from products where name='watch';
