# Class notes for 9/1/2025

- JSON and XML provide some structure to what are the labels of data but does not provide any robust structure so these are commonly known as semi-structured data

- Columnar Databases 
    - Instead of row columns are used as the base of the database.
    - In a row based database for machine productivity one row with the headers as (`id, part_number, production_per_hour, cost`) will look like - `001(ID Assigned by the database): m1, 2000, 10000` but in column based database all the same type of data are on the same row. So all the `production_per_hour` will be in one row somewhat like - `2000,1200,4000,5000`
    - This makes performing aggregation on the data faster. So mainly used for data analysis
    - very fast append, slower in finding all data regarding one entry
    - slow in updating data
    - Example: Cassandra

