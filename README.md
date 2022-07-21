# Python test task

## The task is:

### You need to develop a script in Python 3, which will perform the following functions:

1. Retrieve data from a document using the Google API made in [Google Sheets](https://docs.google.com/spreadsheets/d/1f-qZEX1k_3nj5cahOzntYAnvO4ignbyesVO7yuBdv_g/edit) (need to copy to your Google account and give yourself permissions).
2. The data should be added to the database, in the same form as in the source file, with the addition of the column "cost in rubles".
    
    a. DB should be created independently, DBMS based on PostgreSQL.
    
    b. Data for $ to ruble conversion should be obtained using [Central Bank of Russia] exchange rate (https://www.cbr.ru/development/SXML/).
    
3. Script works all the time to ensure data is updated online (please note that rows in Google Sheets table can be deleted, added and changed).

### Additions that will give extra points and raise potential pay:

1. a. Packaging the solution in a docker container
    
    b. Development of a functionality to check if the "delivery deadline" from the table is met. If the deadline has passed, the script sends a notification to Telegram.
    
    c. Development of a single-page web application based on Django or Flask. Front-end React.
