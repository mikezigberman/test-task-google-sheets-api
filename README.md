# Test Job for Middle Python Developer Position

## :page_with_curl:    Contents

- [The task is:](#the-task-is)
    - [Minimal functionality](#minimal-functionality)
    - [Advanced functionality](#advanced-functionality)
- [Technology stack](#technology-stack)
- [Solution steps](#solution-steps)
- [Part 1: Base settings](#placard-part-1:-base-settings) :white_check_mark:
    - [Copying the table](#copying-the-table) :white_check_mark:
    - [Getting the necessary Google API's and access rights](#step-2) :white_check_mark:
- [Part 2: Backend](#technologist-creating-an-application) (:construction: in process)
    - [Step 1: Creating an environment](#step-1:-сreating-an-environment) :white_check_mark:
    - [Creating a Django Application](#creating-a-django-application) (:construction: in process)
    - [Creating a PostgreSQL database](#creating-a-postgresql-database) (:construction: in process)
    - [Merging a database with a Google table](#merging-a-database-with-a-google-table) (:construction: in process)
- [Part 3: Frontend](#framed_picture-creating-an-application) (:construction: in process) <!-- :framed_picture:	-->
    - [Website template development](#framed-picture-website-template-development) (:construction: in process) 
- [Instructions for installing and running the project](#instructions-for-installing-and-running-the-project) (:construction: in process)

## The task is:

### Minimal functionality

### You need to develop a script in Python 3, which will perform the following functions:

1. Retrieve data from a document using the Google API made in [Google Sheets](https://docs.google.com/spreadsheets/d/1f-qZEX1k_3nj5cahOzntYAnvO4ignbyesVO7yuBdv_g/edit) (need to copy to your Google account and give yourself permissions).
2. The data should be added to the database, in the same form as in the source file, with the addition of the column "cost in rubles".
    
    a. DB should be created independently, DBMS based on PostgreSQL.
    
    b. Data for $ to ruble conversion should be obtained using [Central Bank of Russia] exchange rate (https://www.cbr.ru/development/SXML/).
    
3. Script works all the time to ensure data is updated online (please note that rows in Google Sheets table can be deleted, added and changed).

### Advanced functionality

### Additions that will give extra points and raise potential pay:

1. a. Packaging the solution in a docker container
    
    b. Development of a functionality to check if the "delivery deadline" from the table is met. If the deadline has passed, the script sends a notification to Telegram.
    
    c. Development of a single-page web application based on Django or Flask. Front-end React.
    
## Technology stack:

![Python](https://img.shields.io/badge/-Python-black?style=flat-square&logo=Python)
![Django](https://img.shields.io/badge/-Django-0aad48?style=flat-square&logo=Django)
![React](https://img.shields.io/badge/-React-2f3f52?style=flat-square&logo=React)
![Postgresql](https://img.shields.io/badge/-PostgreSQL-%232c3e50?style=flat-square&logo=Postgresql)
![Docker](https://img.shields.io/badge/-Docker-46a2f1?style=flat-square&logo=docker&logoColor=white)

## Solution steps:

### :placard: Part 1: Working with the table and getting the necessary Google API's and access rights 

### Step 1: Copying the table 

    a. Selecting the required table fields
    
    b. CTRL+C
    
    c. Create a new table with the name test-task-chanelservice
    
    d. CTRL+V
    
<img width="1440" alt="Screenshot 2022-07-21 at 16 42 30" src="https://user-images.githubusercontent.com/30218257/180228398-15334e52-c7f3-47ef-ba2d-6f35e2b9b399.png">
    
### Step 2: Getting the necessary Google API's and access rights 

    a. Visit https://console.cloud.google.com/
    
    b. Click on "Select a project" (look at the screenshot below)
    
    c. Click on "New Project" (look at the screenshot below)
    
<img width="1440" alt="Screenshot 2022-07-21 at 16 52 25" src="https://user-images.githubusercontent.com/30218257/180231521-8ed0c247-83ae-47e1-a15e-ca11ade570ff.png">

    d. Then you need to write the name of the project (in my example it is test-google-sheets-api) 
    
    and click on the "Create" button

<img width="1440" alt="Screenshot 2022-07-21 at 17 16 20" src="https://user-images.githubusercontent.com/30218257/180237545-5fc3fce5-f3a8-4d51-b72f-d4db2f99a780.png">

    e. Once the project has been created, go to Credentials 
    
    (make sure you configure Credentials for the right project)
    
    f. Click on "Create Credentials".

    g. And select "Service Account"
    
<img width="1440" alt="Screenshot 2022-07-21 at 17 32 41" src="https://user-images.githubusercontent.com/30218257/180241402-c4e3e0ca-6ab8-42e6-93b2-64fc8424d2fa.png">

    h. Then enter the service account name and click on the Create and continue button
    
<img width="1440" alt="Screenshot 2022-07-21 at 17 41 20" src="https://user-images.githubusercontent.com/30218257/180242987-c9d539f3-2bdb-4fcb-8745-e430fccc7aa7.png">
    
    i. Next, select the Owner role and click Continue
    
<img width="1440" alt="Screenshot 2022-07-21 at 17 47 09" src="https://user-images.githubusercontent.com/30218257/180244137-7e04d354-f2c7-4434-a066-55ad681945c6.png">

    j. Next press the "Done" button

<img width="1440" alt="Screenshot 2022-07-21 at 17 50 55" src="https://user-images.githubusercontent.com/30218257/180244784-3ca37373-a066-4d1d-adc8-8587df747048.png">

    k. After redirecting to the Credentials section in the Service Account subsection, 
    
    click on the (somewhat strange) email
    
<img width="1440" alt="Screenshot 2022-07-21 at 17 58 15" src="https://user-images.githubusercontent.com/30218257/180246549-f111bf2b-60e3-4590-8b69-4610fbfd6d2a.png">

    l. Next, from the section Details go to the section Keys click on "Add key" select "Create new key" 
    
    (the key must be in .json format) and click on "Create"
    
<img width="1440" alt="Screenshot 2022-07-21 at 18 01 44" src="https://user-images.githubusercontent.com/30218257/180248742-b67d2ee4-2360-49b8-bc17-6dd4b406c60d.png">
    
    m. After this a file (key) with the extension .json will be downloaded to your computer
    
    n. Then, in Details, copy the (strange) email and paste it into Google Sheets 
    
    (it will be useful to share the necessary information)
    
<img width="1440" alt="Screenshot 2022-07-21 at 18 12 48" src="https://user-images.githubusercontent.com/30218257/180250945-10d718e5-9f99-412b-9845-54712dcf7187.png">

<img width="1440" alt="Screenshot 2022-07-21 at 18 22 11" src="https://user-images.githubusercontent.com/30218257/180252637-d92cf6a5-1ece-467d-8560-dc7f3e7cd65c.png">

### 🤩 First point is done 🤩 

### Part 2: Creating a Django application

## :technologist: Creating an application

### Step 1: Creating an environment 

    a. Open the terminal
    
    b. Go to the Desktop directory (with the command cd Desktop)
    
    c. Create a new folder for the project (with the command mkdir test-google-api)
    
    d. Go to the project directory (command cd test-google-api)

    e. Create a virtual environment for the project (with the command virtualenv googleenv)
    
![Screen-Recording-2022-07-22-at-16 54 20-_online-video-cutter com_](https://user-images.githubusercontent.com/30218257/180456288-6c42c341-10d7-478e-8f10-c0313118f43a.gif)

### Step 2: Creating a Django Application
