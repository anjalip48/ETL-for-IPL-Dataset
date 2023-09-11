# ETL-for-IPL-Dataset
Curated a comprehensive database spanning the Indian Premier League (IPL) seasons from 2008 to 2017, consisting of three distinct files: "First Matches," "Second Deliveries," and "Third Region." This dataset serves as a valuable resource for conducting in-depth ETL , statistical analyses of IPL teams and players.
Business Requirements:
1.To find the team that won the most number of matches in a season.
2.To find the Match wise Player performances

**Schema:**
•	Bottom up approach has been used while building the Schema of the Datawarehouse, according to Kimballs bottom up approach the data model can either consist of one fact table or more than on fact table with its respective dimension tables attached to it . In the dimensional table their exists information and primary key which is inserted and used by fact table as foreign keys . Also the fact table contains all the measures.
![image](https://github.com/anjalip48/ETL-for-IPL-Dataset/assets/144174001/0636a46b-5d50-44a9-be44-639a9538609f)

**ETL:**
The first structured dataset is the Matches data which was downloaded as a CSV file from DataWorld, Match Details by Year. It consisted of Nineteen columns from which I removed the unwanted columns in MS-Excel.
![image](https://github.com/anjalip48/ETL-for-IPL-Dataset/assets/144174001/54b3689c-c23a-4976-b3d1-80ede0ef9ad5)

The second structured data is the Deliveries data which was downloaded as a CSV file from the source same as Matches. It consisted of 21 columns. The table was opened in SSMS where operations were performed to clean the data. 
![image](https://github.com/anjalip48/ETL-for-IPL-Dataset/assets/144174001/9b5437de-a45d-42a9-b322-58a7ab480193)

The third structured data is the Region data downloaded in CSV. It consists of Four columns; the unwanted columns were removed using MS Excel.
![image](https://github.com/anjalip48/ETL-for-IPL-Dataset/assets/144174001/3b88a660-d1b9-4756-8677-008cfc5771e9)

**Transformation and loading:**
In this project once all the data was extracted from its source and cleaned it was directly loaded inside the SQL server 2019 database under the database name IPL. This is used for the IPL_DW and the database for Dimensional table for dimensions and facts.
![image](https://github.com/anjalip48/ETL-for-IPL-Dataset/assets/144174001/b9d6e575-d823-45b1-8d02-7b097a510a83)
Each of the above-mentioned structured data behaved as raw data shown in Fig above. After all my raw data is loaded inside SSMS, dimensions which were required for this data model such as Dim Player, Dim Match, Dim Team, Dim Matchday, Dim Extra Runs, Dim Venue were created using SSMS . It was done by CREATE TABLE query, creating new table and inserting values for it and giving different joins to it manually. For each of these dimensional table primary key was defined. After creating these dimensions in SSMS the insert queries were then inserted into SQL task feature in SSIS.
![image](https://github.com/anjalip48/ETL-for-IPL-Dataset/assets/144174001/4a59043a-037f-4683-b210-e6084f22dc07)
![image](https://github.com/anjalip48/ETL-for-IPL-Dataset/assets/144174001/4915d829-933c-4275-ba33-e72350455603)
![image](https://github.com/anjalip48/ETL-for-IPL-Dataset/assets/144174001/0bf47788-9b53-456c-8f59-88e8141ee9cd)
![image](https://github.com/anjalip48/ETL-for-IPL-Dataset/assets/144174001/b771dc7f-5350-4dad-8a20-23952263c890)
![image](https://github.com/anjalip48/ETL-for-IPL-Dataset/assets/144174001/7244398a-ec9d-408b-b926-3d0b4c017276)
![image](https://github.com/anjalip48/ETL-for-IPL-Dataset/assets/144174001/f68ad6e1-243d-4a33-a77b-2b4a481b825e)
![image](https://github.com/anjalip48/ETL-for-IPL-Dataset/assets/144174001/b123681c-5201-4660-9a9e-11b987412bbb)
![image](https://github.com/anjalip48/ETL-for-IPL-Dataset/assets/144174001/2c6ef875-93f8-4f05-8a06-cbf8635524e8)

**Fact table:** All the dimensional table are being related to each other using the fact table where all the primary key from every dimensional table is present which are referenced as foreign keys in this table. Foreign Key is used here as a reference to create a Join between Fact and Dimension Table. This table stored the most granulated information about the IPL data for data analysis. Measures from all the dimension tables are fetched in this table which will be used in the analysis of data.
![image](https://github.com/anjalip48/ETL-for-IPL-Dataset/assets/144174001/e5f51576-6a03-42d5-8bf6-1f2e1f37e80b)
![image](https://github.com/anjalip48/ETL-for-IPL-Dataset/assets/144174001/7ab5c563-fa7e-4bb2-a289-acfa5cb90a65)

**Star Schema:**
![image](https://github.com/anjalip48/ETL-for-IPL-Dataset/assets/144174001/aa4275c1-85d3-4c9e-a7c0-160e85512611)

**SSRS Reports:**
Player of the Match:This report shows the player of the match counts for all the players. Based on these counts we
can find the best player of the match and finally the player of the tournament.
It contains name of the players that play in this tournament doesn’t matter what team he plays for.
This can be helpful for the team auctioneers and individual players with franchises too.
<img width="232" alt="SSRS-1" src="https://github.com/anjalip48/ETL-for-IPL-Dataset/assets/144174001/bb7edc6b-0e7d-4df9-80bb-826db143fdb1">

Team Winner count: This report is much more helpful than we can think of. As the players shuffle every season the
team that wins most of the matches is known as the best team of tournament and whole era.
This includes names and team id. Total win count is also displayed for visualization purpose.
<img width="200" alt="SSRS-2" src="https://github.com/anjalip48/ETL-for-IPL-Dataset/assets/144174001/be21c089-8dbe-4902-bddc-d10c09aea58c">

Venuewise Matches:
Goal was to Analyze the performance of the Players below Report gives the details about Which player has won maximum number of Player of the Match Awards which helps to analyze best performer and helps to choose Best Player. Similarly, we have the data for Best team based on Match Winning count.
<img width="176" alt="SSRS-3" src="https://github.com/anjalip48/ETL-for-IPL-Dataset/assets/144174001/6627320c-15cc-45eb-8081-8d8561141323">

**Visualization:**
![image](https://github.com/anjalip48/ETL-for-IPL-Dataset/assets/144174001/9c64f230-be75-432a-b0e5-9467fc35d099)
Region Wise Match Analysis:
![image](https://github.com/anjalip48/ETL-for-IPL-Dataset/assets/144174001/632f0f9c-5889-441d-87c5-0bf43b6ac6a4)
Top teams by Winning:
![image](https://github.com/anjalip48/ETL-for-IPL-Dataset/assets/144174001/adaccca0-65d3-4ccc-bb32-050fff31cb66)
Biggest Wins Team Wise:
![image](https://github.com/anjalip48/ETL-for-IPL-Dataset/assets/144174001/67ee6fc5-d21a-4b01-8f51-6cf137210b1c)
Top Players:
![image](https://github.com/anjalip48/ETL-for-IPL-Dataset/assets/144174001/4310b65a-7b1c-4c26-901b-ff7394549952)

