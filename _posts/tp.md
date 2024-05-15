---
toc: true
comments: true
layout: post
title: Write up 
type: hacks
permalink: tpwriteup
---
## My contribution

For my final project, I created a dynamic music streaming platform similar to Spotify, tailored for gamers who want to enjoy their favorite music while playing. I set up two main tables in a single SQLite database. The first table holds user data like usernames, IDs, securely encrypted login info, and birthdates for security and customization. The second table is all about songs, storing details like track names, artists, audio specs, and album artwork for a complete music experience.

On the backend, I built the song database from scratch, making sure it was solid and ready for action. I handled the backend infrastructure, making sure everything connected smoothly and worked efficiently. This included setting up endpoints for communication between the frontend and backend.

Moving to the frontend, I designed a good-looking interface with a neat table layout to show off a big library of songs. Every detail, from the colorful album covers to the easy-to-use play button, was made to keep users engaged and happy. And it wasn't just about looks—I made sure every part worked seamlessly with the backend, so users could enjoy a smooth experience.

One highlight was getting the play button to work perfectly, linking up with the backend to grab audio file links effortlessly. This showed off my skills in frontend development and my ability to make strong connections between different parts of the app.

In short, my project brings together backend and frontend skills to create a polished music streaming platform that's sure to make gaming sessions even more enjoyable.

## Collections

### Requirements:

Show your unique collection or table in the database from VSCode using the SQLite3 Editor. You can also see the rows and columns in the SQLite database's table. 

### My Feature:

This is the database which I used in order to access items and use for implementation in the code. 
<img src="https://tanayshah1.github.io/student2/images/1.png" width = auto height = 300px >


### Requirements:
Present the original code that was written to populate the table and generate test data using the VSCode model. 

### My Feature: 
This code in my model file initializes the table. It establishes the connection between the frontend and the backend. 
<img src="https://tanayshah1.github.io/student2/images/2.png" width = auto height = 300px>

## Lists and Dictionaries

### Requirements:

Show a list that was taken from a database as Python objects in VSCode using the Debugger.

### My Feature:

With the help of a breakpoint in the endpoint code, I debug my collection feature. After hitting the breakpoint, it invokes the class. Subsequently, I traverse the function while the data is transmitted to the front end. 
<img src="https://tanayshah1.github.io/student2/images/3.png" alt="Description of Image"/>

### Requirements:
Use the debugger in VSCode to display two different dictionary examples and to display keys and values.

### My Feature: 
This displays a dictionary of every song, along with details about the artist and album cover. 
<img src="https://tanayshah1.github.io/student2/images/4.png" alt="Description of Image"/>


## APIs and JSON

### Requirements:
Use the GET, POST, and UPDATE methods in VSCode to display the description of the Python API code for requests and responses. Talk about the algorithmic condition that, depending on the request method, directs the request to the proper Python function.

### My Feature: 
This is the code for my API endpoint, which retrieves data from my backend using the GET method. For the purpose of obtaining the database's song collection and information, the class defines an additional resource. It also has a query option that searches for a certain music that may be entered.
<img src="https://tanayshah1.github.io/student2/images/5.png" alt="Description of Image"/> 

### Requirements:
Display the algorithmic criteria in VSCode that are used to verify data on a POST condition.

### My Feature: 
For my machine learning project, this is the code for my API endpoint. It receives the song IDs that the user has imputed in the frontend and verifies them by determining whether the value is null or not an integer. In that scenario, a poor request error is returned. It inputs the song IDs into the prediction model if they are legitimate.
<img src="https://tanayshah1.github.io/student2/images/6.png" alt="Description of Image"/>

Show the required URL request and body for the GET, POST, and UPDATE methods in Postman.
<img src="https://tanayshah1.github.io/student2/images/7.png" alt="Description of Image"/> 


Display the JSON response data in Postman for 200 successful scenarios using the GET, POST, and UPDATE methods. 
<img src="https://tanayshah1.github.io/student2/images/8.png" alt="Description of Image"/> 

Show the JSON response for the 400 error when there is a missing body in a POST request in Postman. 
<img src="https://tanayshah1.github.io/student2/images/9.png" alt="Description of Image"/>

When an unknown user ID is provided in response to a UPDATE call in Postman, provide the JSON answer for error 404.
<img src="https://tanayshah1.github.io/student2/images/10.png" alt="Description of Image"/>


## Frontend

### Requirements:

Display the JSON object response from the retrieve of the GET, POST, and UPDATE methods in the Chrome inspect window.

### My Feature:

<img src="https://tanayshah1.github.io/student2/images/11.png" width = auto height = 300px >

### Requirements:

Show an example (GET) of how to get an array of formatted JSON objects into the browser's screen with the Chrome browser.

### My Feature:

I'll demonstrate how to open the freeze. The picture is shown on a card format that contains the music data that has been formatted into containers.

### Requirements:
Describe the retrieve and method used to acquire the Array of JSON objects in the JavaScript code.

### My Feature:
This retrieves the variable endpoint of the API, which varies based on the song you select.
<img src="https://tanayshah1.github.io/student2/images/12.png" alt="Description of Image"/>

The song title, artist, and album cover are displayed in the bar at the bottom when the ply button is pressed. This code is as follows: 
<img src="https://tanayshah1.github.io/student2/images/13.png" alt="Description of Image"/>

### Requirements:

Show code in JavaScript that iterates through data and formats it into HTML.

### My Feature:

This generates the HTML container and iteratively loops over the card data from the backend so that the music picture icons may be shown. 
<img src="https://tanayshah1.github.io/student2/images/14.png" alt="Description of Image"/>

### Requirements:

Show an example (POST or UPDATE) of gathering data, transmitting it, and receiving a response that displays an update in the Chrome browser. Try again with this demonstration of success and failure.

### My Feature:

To show a failure, I will launch the frontend with the backend disabled and play a song while the endpoint code is operational.

### Requirements:

Show and explain the code in JavaScript code that deals with success.Explain to the user how the Chrome browser displays code success.

### My Feature:

The songs are run from the retrieve data into a show fards function by this code, which then appends the songs to the containers that were made during the style process. The songs are run from the retrieve data into a show fards function by this code, which then appends the songs to the containers that were made during the style process. 
<img src="https://tanayshah1.github.io/student2/images/15.png" alt="Description of Image"/>

### Requirements:
Show and explain the code in JavaScript that handles failures. Describe the way the user sees the code's failure on the Chrome browser screen. 

### My Feature:
This determines whether the backend is error-free. If so, the error will be shown in the console. 
<img src="https://tanayshah1.github.io/student2/images/16.png" alt="Description of Image"/>


## Extras

- Demonstrate data preparation for analysis and algorithms. This covers one-hot encoding, cleaning, and encoding.
<img src="https://tanayshah1.github.io/student2/images/17.png" alt="Description of Image"/> 

- Demonstrate prediction preparation and algorithms.
<img src="https://tanayshah1.github.io/student2/images/18.png" alt="Description of Image"/>

- Discuss concepts and understanding of Linear Regression algorithms.

A fundamental statistical technique called linear regression is used to examine and comprehend the relationship between one or more independent variables (like size or number of bedrooms) and a dependent variable (like property prices). This approach is predicated on the idea that a straight line may roughly represent this connection. Consider graphing data points with the dependent variable (s) represented by the vertical axis and the independent variable (s) by the horizontal axis. By varying the line's slope and intercept to reduce the discrepancy between the expected and actual values, linear regression seeks to identify the best-fitting line between these locations. This method is frequently used to forecast or infer correlations between variables in a variety of domains, including engineering, finance, and economics.

- Discuss concepts and understanding of Decision Tree analysis algorithms.

In machine learning and data mining, decision trees are a kind of model that are used to make judgments based on input features. They have topologies that are similar to flowcharts, with each internal node standing for a test or query about a particular attribute, each branch for a potential response or test result, and each leaf node for a final judgment or categorization. Decision trees are helpful for deciphering the underlying patterns in data and are employed in both regression and classification applications. They are adaptable for a range of applications, including consumer segmentation, fraud detection, and medical diagnosis. They can handle both numerical and categorical data and are capable of capturing complicated correlations between variables.
