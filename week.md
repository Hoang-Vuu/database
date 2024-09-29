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

![Screenshot 2024-09-17 140556](https://github.com/user-attachments/assets/56140f38-97b6-47b3-b74a-989ab92ce67a)



#9:
select distinct co2_budget from game;

![Screenshot 2024-09-17 135642](https://github.com/user-attachments/assets/06d25731-fde9-4238-b104-c7617b90ef1b)

#10:
select screen_name, co2_budget, co2_consumed, @co2_left := (co2_budget - co2_consumed) co2_left from users where screen_name = 'Ilkka';

![Screenshot 2024-09-17 140014](https://github.com/user-attachments/assets/3b47da87-19a7-42cf-9fbd-2727de6b1205)


Exercises 3: Multiple Table Queries

#1:
select country.name as "country name", airport.name as "airport name"
from airport, country
where airport.iso_country = country.iso_country and country.name = "Iceland";

![1](https://github.com/user-attachments/assets/db9f2405-a48b-4e29-92da-205f47b958ee)

#2:
select airport.name as "airport name"
from airport, country
where airport.iso_country = country.iso_country and country.name = "France" and airport.type = "large_airport";


![2](https://github.com/user-attachments/assets/622c8cf5-d594-4223-aa4d-cba9776c63ef)

#3:
select country.name as country_name, airport.name as airport_name
from airport, country
where airport.iso_country = country.iso_country and country.continent = "AN";

![3](https://github.com/user-attachments/assets/d3bd5658-73a8-47e5-be57-96547dfdf3db)

#4:
select elevation_ft
from airport, game
where location = ident and screen_name = "Heini";

![4](https://github.com/user-attachments/assets/68567596-90a9-4c8f-b30e-0236b068b73a)

#5:
select 179 * 0.3048 as elevation_m;

![5](https://github.com/user-attachments/assets/23ff56f9-ed8a-4839-b81b-060ecb16f695)

#6:
select name
from airport, game
where location = ident and screen_name = "Ilkka";

![6](https://github.com/user-attachments/assets/7ddbd3c2-18da-4a3e-9805-99bf0792f747)

#7:
select country.name
from airport, game, country
where location = ident and airport.iso_country = country.iso_country  and screen_name = "Ilkka";

![7](https://github.com/user-attachments/assets/7f4a59e2-4288-4be7-92fa-4924c00cd79c)

#8:
select name
from goal, goal_reached, game
where game.id = game_id and goal.id = goal_id and screen_name = "Heini";

![8](https://github.com/user-attachments/assets/1107e763-6bab-4b30-a797-68166b237558)

#9:
	
select airport.name
from airport, game, goal, goal_reached
where ident = location and game.id = game_id and goal.id = goal_id and screen_name = "Ilkka" and goal.name = "CLOUDS";

![9](https://github.com/user-attachments/assets/71eac3f2-1c96-464e-a09d-7f04dca33762)

#10:

select country.name
from country, airport, game, goal, goal_reached
where airport.iso_country = country.iso_country and ident = location and game.id = game_id and goal.id = goal_id and screen_name = "Ilkka" and goal.name = "CLOUDS";


![Screenshot 2024-09-17 203718](https://github.com/user-attachments/assets/903aa1f4-098e-4f2f-b4bd-d5761426b397)


Exercise 4:

#1:
select country.name as "country name", airport.name as "airport name"
from country inner join airport on airport.iso_country = country.iso_country
where country.name = "Finland" and scheduled_service = "yes";

![Screenshot 2024-09-29 193448](https://github.com/user-attachments/assets/2518074d-3c44-4ba6-976e-83def2de5cbd)


#2:
select screen_name, airport.name
from game inner join airport on location = ident;

![2](https://github.com/user-attachments/assets/8a8386f6-a2aa-4694-8fc2-3d5559145933)

#3:
select screen_name, country.name
from game inner join airport on location = ident inner join country on airport.iso_country = country.iso_country;


![3](https://github.com/user-attachments/assets/dbcba7df-aca1-422c-819c-a84927fbcb85)

#4:
select airport.name, screen_name
from airport left join game on ident = location where name like "%Hels%";

![4](https://github.com/user-attachments/assets/fb283bb8-923c-4374-9cf1-aba758c7b5d3)

#5:
select name, screen_name
from goal left join goal_reached on goal.id = goal_id  left join game on game.id = game_id;


![5](https://github.com/user-attachments/assets/61c84260-3937-4e53-a354-31035c9d0185)



