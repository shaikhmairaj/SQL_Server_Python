# SQL_Server_Python
In this repository, we learn how to connect a SQL Server Database to Python using pyodbc.

<h1>Connection WorkFlow</h1>

<h1>Step 1 - Import libraries pyodbc and pandas.</h1>
import pyodbc

import pandas as pd




<h1>Step 2 - Create a connection string.</h1>
If using Windows Authentication, construct the connection string as below-

cnxn_str = ("Driver={ODBC Driver 17 for SQL Server};"

            "Server=DatabaseServerName;"

            "Database=Training;"

            "Trusted_Connection=yes;")

If using username and password, create a connection string as per the below code.

import pyodbc 

# Some other example server values are

# server = 'localhost\sqlexpress' # for a named instance

# server = 'myserver,port' # to specify an alternate port

server = 'tcp:myserver.database.windows.net' 

database = 'mydb' 

username = 'myusername' 

password = 'mypassword' 

# ENCRYPT defaults to yes starting in ODBC Driver 18. It's good to always specify ENCRYPT=yes on the client side to avoid MITM attacks.

cnxn = pyodbc.connect('DRIVER={ODBC Driver 18 for SQL Server};SERVER='+server+';DATABASE='+database+';ENCRYPT=yes;UID='+username+';PWD='+ password)




Connect using pyodbc.connect

cnxn = pyodbc.connect(cnxn_str)




<h1>Step 3 - Option 1 - Use a cursor to execute a SQL command.</h1>
cursor = cnxn.cursor()

cursor.execute("Select * from Dept")

if using this option, cursor methods for fetching data need to be used. We will use the next option to execute and fetch the results from a SQL Query.




<h1>Option - 2 - Use pandas.</h1>
df = pd.read_sql("Select * from Dept", cnxn)

print(df)


