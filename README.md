# sql-subqueries
## Standard Exercise
If you completed the last homework session, you should have a SolarPower dataset containing two tables:
- SolarPower.Generation_Data
- SolarPower.Weather_Sensor_Data

Roughly speaking, when the sunlight hits a solar panel, a flow of charge is created, resulting in the generation of DC Power (Direct Current). The DC Power is then transferred to an inverter, which converts it into AC Power (Alternating Current), which eventually reaches our homes.
![alt text](image.png)
Given this data, answer the following questions:

1. Write a query that shows the average AC and DC Power generated, grouped by each power plant.
2. In the process of DC-to-AC conversion, no inverter can achieve 100% efficiency. This means that the output (AC) energy is not as high as the input (DC) energy. The efficiency of the inverter, calculated as AC Power / DC Power, generally ranges from 95% to 98%.
Starting from the last query, what is the overall average inverter efficiency for each Plant?
3. According to this data, which Plant is the most efficient? Do you notice anything strange? If so, what could the reason be?
4. Let’s now focus on plant_id = 4136001. Write a query that shows the average DA and AC Power as well as the average inverter efficiency for each hour of the day. Hint: careful about the “division by zero” error
5. What can you say about the hourly distribution of power generated? Why are there zeros in the resulting table?
6. How many inverters (source_key) are there in the Generation_Data table? And in the Weather_Sensor_Data table?
7. Are there any source keys in the Weather_Sensor_Data table that are also present in the Generation_Data table? Can you think of a way of using a SUBQUERY (in the WHERE clause of a query) to check for this?
8. Let’s say that the anomaly in the data you observed at question 3 is due to a measurement error. Write a query that will modify only the DC Power data relative to plant_id 4135001 by moving the decimal point one step to the left (eg: divide by 10). Note: you won’t be able to execute the update statement due to BigQuery’s Sandbox limitations, just write down the code that would make the appropriate changes.

## Advanced Exercise
1. Since we can’t update the existing table, let’s re-create the Generation_Data table via a UNION statement and call it Generation_Data_Clean. Make sure you:
   - Fix the DC Power problem in the Plant1 table
   - Add a new string column in the final table called Plant_nr where you manually specify whether that data is relative to “plant_1” or “plant_2”
2. The Weather_Sensor_Data table stores records of the average ambient (outdoor temp) and module (photovoltaic panel temp) temperatures as well as irradiation levels (the amount of the sun's power detected by a sensor). What are the average ambient temperature, module temperature and irradiation by hour of day?
3. What can you say about the data you just generated?
4. Using a JOIN and SUBQUERIES, merge the output table from question 4 (using the new “Clean” table and without the filter on the power plant) to the table produced in question 8. Add the PLANT_ID to both outputs so that you can use that in the JOIN as well. In the end you should have an output table that looks like this (I also used plant_nr instead of plant_id):
![alt text](table.png)
1. The chart below was created using the table from the previous question and it shows the relationship between irradiation and the inverter’s efficiency among the two power plants. What is the chart telling us? What can you say about this relationship?
Note: we will talk about data visualisation later in the course, but if you feel inspired, you can try to replicate this chart using tools like Looker Studio, Tableau or Power BI.
![alt text](plot.png)
