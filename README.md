#SQLite-with-python
 how can i mix both SQLite?
import sqlite3
#Connecting to sqlite
#connection object
conn = sqlite3.connect('INSTRUCTOR.db')
#cursor object
cursor_obj = conn.cursor()
#Creating table
table = """ create table If NOT EXISTS INSTRUCTOR(ID INTEGER PRIMARY KEY NOT NULL, FNAME VARCHAR(20), LNAME VARCHAR(20), CITY VARCHAR(20), CCODE CHAR(2));"""
 
cursor_obj.execute(table)
 
print("Table is Ready")

cursor_obj.execute('''insert into INSTRUCTOR values (1, 'Rav', 'Ahuja', 'TORONTO', 'CA')''')

cursor_obj.execute('''insert into INSTRUCTOR values (2, 'Raul', 'Chong', 'Markham', 'CA'), (3, 'Hima', 'Vasudevan', 'Chicago', 'US')''')

statement = '''SELECT * FROM INSTRUCTOR'''
cursor_obj.execute(statement)
print("All the data")
output_all = cursor_obj.fetchall()
for row_all in output_all:
  print(row_all)

    ## Fetch few rows from the table
statement = '''SELECT * FROM INSTRUCTOR'''
cursor_obj.execute(statement)
  
print("All the data")
#If you want to fetch few rows from the table we use fetchmany(numberofrows) and mention the number how many rows you want to fetch
output_many = cursor_obj.fetchmany(2) 
for row_many in output_many:
  print(row_many)

    #Fetch only FNAME from the table
statement = '''SELECT FNAME FROM INSTRUCTOR'''
cursor_obj.execute(statement)
  
print("All the data")
output_column = cursor_obj.fetchall()
for fetch in output_column:
  print(fetch)

statement = '''SELECT * FROM INSTRUCTOR'''
cursor_obj.execute(statement)

!pip install pandas
import pandas as pd
#retrieve the query results into a pandas dataframe
df = pd.read_sql_query("select * from instructor;", conn)

#print the dataframe
df

#print just the LNAME for first row in the pandas data frame
df.LNAME[0]

print(df)

# Close the connection
conn.close()
