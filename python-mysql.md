## Python + MySQL

Link video YouTube:
https://www.youtube.com/watch?v=V7L2Sks8Osk

Code:
```python
import mysql.connector

mydb = mysql.connector.connect(
  host="localhost",
  user="root",
  password="myroot",
  database="mt_public_db"
)

mycursor = mydb.cursor()

mycursor.execute("SELECT * FROM customer")

myresult = mycursor.fetchall()

for x in myresult:
  print(x)
```
