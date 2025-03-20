# MIST-4610-Group-5

# Team Name:
21484 Group 5
# Team Members
1. Jeremiah Doherty: https://github.com/jeremiahd72
2. Chase Ratelle: https://github.com/Bubb-Rattle
3. Isaac Self: https://github.com/mrslimeballl
4. Alex Vuong: https://github.com/akv74603
5. Deven Yadav: https://github.com/dmy41514
# Problem Description:

Atlanta Falcons football has been a disappointment for many years in a row. With lackluster rosters and poor coaching, the Falcons have been losing many fans as the attendance for games has gone down every year since they made the super bowl back in 2017. But this past offseason, the falcons drafted a rookie QB named Michael Penix Jr and in the last few games of the past regular season, he showed a lot of promise with his play and brought the excitement back to Atlanta Falcons football. With the excitement coming back, the fans and attendance for games next season are expected to increase, and as a result, a select group of students from the MIST4610 class at UGA have been selected to gather and organize important information about the Atlanta Falcons Football Organization for the coming season.

# Data Model

Explanation:
Our data model represents a structured database designed for the Atlanta Falcons Football Team, capturing key aspects of fans, players, coaches, games, seasons, merchandise, and related transactions. The Fan entity contains attributes such as Fan_ID, Full_name, Email, and Favorite_player, which are used to track individual fans, their contact details, and their favorite player. The Ticket entity associates with fans via Fan_ID and contains attributes like Ticket_ID, Number_sold, Price, and Gameday_ID, linking each ticket purchase to a specific game.

The Gameday entity records game details with attributes including Game_ID, Game_date, Away_team, Stadium, Score_home_team, and Score_away_team. These attributes provide full coverage of individual game events, with scores and logistics. Player performance during each game is tracked by the Player_Statistics entity, which captures data such as Passing_yards, Rushing_yards, Touchdowns, and Fumbles. It links directly to Player_ID and Gameday_ID, allowing performance to be measured for each player per game.

Player details are stored in the Player entity with attributes like Player_ID, Full_name, Position, Jersey_number, physical attributes (Height, Weight), Date_of_birth, Nationality, and contractual details such as Contract_start_date, Contract_end_date, and Salary. Complementing this, Season_Stats aggregates player performance at the season level, tracking metrics like Total_passing_yards, Total_rushing_yards, and Total_touchdowns for each player, linking them to the Season entity which defines the seasonal context with Season_ID, Season_wins, and Season_losses.

Coaching details are handled by the Coach entity, which captures each coach's identity and employment information, including Coach_ID, Full_name, Role, Hire_date, Contract_end_date, and Salary. The Coaching_Duration entity links coaches to specific seasons using Season_ID and includes Start_date and End_date fields, enabling analysis of coaching impact over different seasons. This allows for both longitudinal tracking and performance correlation with seasonal outcomes.

Lastly, the financial side of the football organization is represented through Merchandise, Sale, and Lineitem entities. Merchandise details (Merchandise_ID, Category, Price, Stock_quantity) are tied to Sales, which log transactions via Sale_ID, Sale_date, Sale_price, and Fan_ID. Each sale can include multiple line items, recorded in the Lineitem entity by Lineitem_ID, linking to both Sale_ID and Merchandise_ID. This setup ensures full visibility into fan purchases, enabling merchandising strategy and inventory control to be optimized.

Visual:
![Data_Model_Project_One](https://github.com/user-attachments/assets/ac014e37-d411-4bcd-9a8e-d388c9141b9f)

# Data Dictionary

## Table: Fan

| **Column Name**  | **Description**                                           | **Data Type** | **Size** | **Format** | **Key?** |
| ---------------- | --------------------------------------------------------- | ------------- | -------- | ---------- | -------- |
| Fan\_ID          | Primary key, unique sequential number identifying the fan | INT           | N/A      |            | PK       |
| Full\_name       | Full name of the fan                                      | VARCHAR       | 45       |            |          |
| Email            | Email address of the fan                                  | VARCHAR       | 45       |            |          |
| Favorite\_player | Favorite player of the fan                                | VARCHAR       | 45       |            |          |

## Table: Ticket

| **Column Name** | **Description**                                              | **Data Type** | **Size** | **Format** | **Key?** |
| --------------- | ------------------------------------------------------------ | ------------- | -------- | ---------- | -------- |
| Ticket\_ID      | Primary key, unique sequential number identifying the ticket | INT           | N/A      |            | PK       |
| Number\_sold    | Number of tickets sold                                       | INT           | N/A      |            |          |
| Price           | Price of the ticket                                          | INT           | N/A      |            |          |
| Fan\_ID         | Foreign key, reference to the fan who purchased the ticket   | INT           | N/A      |            | FK       |
| Gameday\_ID     | Foreign key, reference to the gameday for the ticket         | INT           | N/A      |            | FK       |

## Table: Merchandise

| **Column Name** | **Description**                                               | **Data Type** | **Size** | **Format** | **Key?** |
| --------------- | ------------------------------------------------------------- | ------------- | -------- | ---------- | -------- |
| Merchandise\_ID | Primary key, unique sequential number identifying merchandise | INT           | N/A      |            | PK       |
| Category        | Category of merchandise                                       | VARCHAR       | 45       |            |          |
| Price           | Price of the merchandise                                      | VARCHAR       | 45       |            |          |
| Stock\_quantity | Quantity of merchandise in stock                              | VARCHAR       | 45       |            |          |

## Table: Sale

| **Column Name** | **Description**                                         | **Data Type** | **Size** | **Format** | **Key?** |
| --------------- | ------------------------------------------------------- | ------------- | -------- | ---------- | -------- |
| Sale\_ID        | Primary key, unique sequential number for the sale      | INT           | N/A      |            | PK       |
| Sale\_date      | Date of the sale                                        | VARCHAR       | 45       | mm/dd/yyyy |          |
| Sale\_price     | Total price of the sale                                 | VARCHAR       | 45       |            |          |
| Fan\_ID         | Foreign key, reference to the fan who made the purchase | INT           | N/A      |            | FK       |

## Table: Lineitem

| **Column Name** | **Description**                                                 | **Data Type** | **Size** | **Format** | **Key?** |
| --------------- | --------------------------------------------------------------- | ------------- | -------- | ---------- | -------- |
| Lineitem\_ID    | Primary key, unique sequential number identifying the line item | INT           | N/A      |            | PK       |
| Sale\_ID        | Foreign key, reference to the sale                              | INT           | N/A      |            | FK       |
| Merchandise\_ID | Foreign key, reference to merchandise                           | INT           | N/A      |            | FK       |

## Table: Gameday

| **Column Name**   | **Description**                                            | **Data Type** | **Size** | **Format** | **Key?** |
| ----------------- | ---------------------------------------------------------- | ------------- | -------- | ---------- | -------- |
| Game\_ID          | Primary key, unique sequential number identifying the game | INT           | N/A      |            | PK       |
| Game\_date        | Date of the game                                           | VARCHAR       | 45       | mm/dd/yyyy |          |
| Away\_team        | Name of the away team                                      | VARCHAR       | 45       |            |          |
| Stadium           | Name of the stadium                                        | VARCHAR       | 45       |            |          |
| Score\_home\_team | Home team score                                            | INT           | N/A      |            |          |
| Score\_away\_team | Away team score                                            | INT           | N/A      |            |          |

## Table: Player

| **Column Name**       | **Description**                                              | **Data Type** | **Size** | **Format** | **Key?** |
| --------------------- | ------------------------------------------------------------ | ------------- | -------- | ---------- | -------- |
| Player\_ID            | Primary key, unique sequential number identifying the player | INT           | N/A      |            | PK       |
| Full\_name            | Full name of the player                                      | VARCHAR       | 45       |            |          |
| Position              | Player’s position                                            | VARCHAR       | 45       |            |          |
| Jersey\_number        | Player’s jersey number                                       | INT           | N/A      |            |          |
| Height                | Height of the player                                         | VARCHAR       | 45       |            |          |
| Weight                | Weight of the player                                         | VARCHAR       | 45       |            |          |
| Date\_of\_birth       | Date of birth of the player                                  | DATE          | N/A      | mm/dd/yyyy |          |
| Nationality           | Nationality of the player                                    | VARCHAR       | 45       |            |          |
| University            | University attended by the player                            | VARCHAR       | 45       |            |          |
| Contract\_start\_date | Player’s contract start date                                 | VARCHAR       | 45       |            |          |
| Contract\_end\_date   | Player’s contract end date                                   | VARCHAR       | 45       |            |          |
| Salary                | Player’s salary                                              | VARCHAR       | 45       |            |          |

## Table: Player Statistics

| **Column Name**   | **Description**                                             | **Data Type** | **Size** | **Format** | **Key?** |
| ----------------- | ----------------------------------------------------------- | ------------- | -------- | ---------- | -------- |
| PS\_ID            | Primary key, unique sequential number for player statistics | INT           | N/A      |            | PK       |
| Passing\_yards    | Passing yards made by the player                            | INT           | N/A      |            |          |
| Rushing\_yards    | Rushing yards made by the player                            | INT           | N/A      |            |          |
| Retrieving\_yards | Retrieving yards made by the player                         | INT           | N/A      |            |          |
| Tackles           | Tackles made by the player                                  | INT           | N/A      |            |          |
| Interceptions     | Interceptions by the player                                 | INT           | N/A      |            |          |
| Touchdowns        | Touchdowns made by the player                               | INT           | N/A      |            |          |
| Fumbles           | Fumbles made by the player                                  | INT           | N/A      |            |          |
| Gameday\_ID       | Foreign key, reference to Gameday                           | INT           | N/A      |            | FK       |
| Player\_ID        | Foreign key, reference to Player                            | INT           | N/A      |            | FK       |

## Table: Season Statistics

| **Column Name**          | **Description**                                             | **Data Type** | **Size** | **Format** | **Key?** |
| ------------------------ | ----------------------------------------------------------- | ------------- | -------- | ---------- | -------- |
| SS\_ID                   | Primary key, unique sequential number for season statistics | INT           | N/A      |            | PK       |
| Total\_passing\_yards    | Total passing yards in the season                           | INT           | N/A      |            |          |
| Total\_rushing\_yards    | Total rushing yards in the season                           | INT           | N/A      |            |          |
| Total\_retrieving\_yards | Total retrieving yards in the season                        | INT           | N/A      |            |          |
| Total\_tackles           | Total tackles in the season                                 | INT           | N/A      |            |          |
| Total\_interceptions     | Total interceptions in the season                           | INT           | N/A      |            |          |
| Total\_touchdowns        | Total touchdowns in the season                              | INT           | N/A      |            |          |
| Player\_ID               | Foreign key, reference to Player                            | INT           | N/A      |            | FK       |
| Season\_ID               | Foreign key, reference to Season                            | INT           | N/A      |            | FK       |

## Table: Season

| **Column Name** | **Description**                                              | **Data Type** | **Size** | **Format** | **Key?** |
| --------------- | ------------------------------------------------------------ | ------------- | -------- | ---------- | -------- |
| Season\_ID      | Primary key, unique sequential number identifying the season | INT           | N/A      |            | PK       |
| Season\_wins    | Number of wins in the season                                 | VARCHAR       | 45       |            |          |
| Season\_losses  | Number of losses in the season                               | VARCHAR       | 45       |            |          |

## Table: Coaching Duration

| **Column Name** | **Description**                                             | **Data Type** | **Size** | **Format** | **Key?** |
| --------------- | ----------------------------------------------------------- | ------------- | -------- | ---------- | -------- |
| CD\_ID          | Primary key, unique sequential number for coaching duration | INT           | N/A      |            | PK       |
| Full\_name      | Full name of the coach                                      | VARCHAR       | 45       |            |          |
| Start\_date     | Start date of the coaching duration                         | VARCHAR       | 45       | mm/dd/yyyy |          |
| End\_date       | End date of the coaching duration                           | VARCHAR       | 45       | mm/dd/yyyy |          |
| Coach\_ID       | Foreign key, reference to Coach                             | INT           | N/A      |            | FK       |
| Season\_ID      | Foreign key, reference to Season                            | INT           | N/A      |            | FK       |

## Table: Coach

| **Column Name**     | **Description**                                             | **Data Type** | **Size** | **Format** | **Key?** |
| ------------------- | ----------------------------------------------------------- | ------------- | -------- | ---------- | -------- |
| Coach\_ID           | Primary key, unique sequential number identifying the coach | INT           | N/A      |            | PK       |
| Full\_name          | Full name of the coach                                      | VARCHAR       | 45       |            |          |
| Role                | Role of the coach                                           | VARCHAR       | 45       |            |          |
| Hire\_date          | Hire date of the coach                                      | VARCHAR       | 45       | mm/dd/yyyy |          |
| Contract\_end\_date | Contract end date of the coach                              | VARCHAR       | 45       | mm/dd/yyyy |          |
| Salary              | Salary of the coach                                         | VARCHAR       | 45       |            |          |

# Queries
1.  List the full name, university, and position of a player where the position of the player is QB. This query would be important because fans of the team or NFL owners and executives can see the background and some useful information about the player/QB.
   <img width="1156" alt="Screenshot 2025-03-18 at 7 40 31 PM" src="https://github.com/user-attachments/assets/3893b459-5c27-4a12-8b8f-a650ba66a4ee" />
2. List the category and price of the merchandise where the category is large. This query can be important because the Atlanta Falcons can use this to see what category is most popular among fans and how much fans are willing to spend on merchandise.
   <img width="1150" alt="Screenshot 2025-03-18 at 7 50 53 PM" src="https://github.com/user-attachments/assets/62b60a63-4c09-41eb-9e9e-c971b990ac03" />
3. List all fans whose favorite player on the Atlanta Falcons is Julio Jones. This query is relatively important because it shows who was a popular player for the Falcons during their tenure and who was most beloved.
   <img width="1150" alt="Screenshot 2025-03-18 at 8 13 05 PM" src="https://github.com/user-attachments/assets/d7347aa8-6328-4a28-84ab-ce7d62c1420b" />
4. List the game date, game score for the home team, and stadium where the game score for the home team was more than 30 points. Fans can sometimes be curious as to how high the Falcons and other teams have scored in a game, and in the NFL, scoring 30 is a big feat. With this query, fans and NFL executives can see who has scoored over 30 points and the frequency of that.
   <img width="1154" alt="Screenshot 2025-03-18 at 8 18 10 PM" src="https://github.com/user-attachments/assets/529c616c-2438-40ac-9469-03921b07679a" />
5. List the full name and total rushing yards of players who have more than 1000 rushing yards over many games. Management working for the Atlanta Falcons could use this query for a few reasons. They can identify the top rushers on the team and assess individual performance for rostering, scouting, and recruiting purposes. This information can also be used to cater to specific game plans and strategies as well as to offer contracts to high performing players. 
<img width="773" alt="Screenshot 2025-03-18 at 4 57 21 PM" src="https://github.com/user-attachments/assets/2fcac07e-6a42-453b-82e8-3fa6f7d57f87" />

# Database Information
Name of the database: al_Group_21484_G5

Additional information: Each query listed above is marked in the database using stored procedures which can be called using the following format: CALL TP_Q1();
