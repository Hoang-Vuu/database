# database
Exercises 2: Single Table Queries
#1:
select * from goal;
![Screenshot (144)](https://github.com/user-attachments/assets/9d2e65dc-ceea-4b89-a1a4-b3b698949945)

#2:
select name from airport where iso_country = "FI";
![Screenshot (145)](https://github.com/user-attachments/assets/0d9054b3-4354-42a3-b775-5c0be03b3ee1)

#3:
select name from airport where iso_country = "FI" order by name;


![Screenshot (146)](https://github.com/user-attachments/assets/66c60211-658a-4437-acd7-da7a43f289ea)

#4:
select name, type from airport where iso_country = "FI" order by type, name;


![Screenshot (147)](https://github.com/user-attachments/assets/46fd5fe5-7271-4d32-84a3-2f42b0238065)

#5:
select name from country where name like "F%";


![Screenshot 2024-09-17 135423](https://github.com/user-attachments/assets/317818e7-6b9b-4c42-bc49-a28ac607039c)

#6:
select name from country where name like "%F%";

![Screenshot 2024-09-17 135519](https://github.com/user-attachments/assets/2e39378e-7e78-4c0d-af7c-51fc86ec40fc)

#7:
select location from game where screen_name = "Vesa";

![Screenshot 2024-09-17 135605](https://github.com/user-attachments/assets/f5751579-8ee4-43b2-89b8-8ae8b2e513b0)

#8:
select co2_consumed from game where screen_name = "Ilkka";

![Screenshot 2024-09-17 140014](https://github.com/user-attachments/assets/1fca5ae0-256d-4047-8108-e7ed765be7cd)



#9:
select distinct co2_budget from game;

![Screenshot 2024-09-17 135642](https://github.com/user-attachments/assets/06d25731-fde9-4238-b104-c7617b90ef1b)

#10:
select screen_name, co2_budget, co2_consumed, @co2_left := (co2_budget - co2_consumed) co2_left from users where screen_name = 'Ilkka';

![Screenshot 2024-09-17 140014](https://github.com/user-attachments/assets/3b47da87-19a7-42cf-9fbd-2727de6b1205)
