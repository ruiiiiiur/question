## **Question Setting App**

##### What is Question Setting App?

**Question setting app is a web-based application which is designed to create new question points
on a map. The points will then be stored in a databased and displayed in a Quiz
App.**

##### System requirements

**Software**: An SSH file transfer system is needed to upload files onto your server

- > For Mac: Fugu [1.2.1pre1](http://sourceforge.net/projects/fugussh/files/Unstable/fugu-1.2.1pre1/Fugu-1.2.1pre1.zip/download). (Download link: http://rsug.itd.umich.edu/software/fugu/)

- > For Windows: BitVise Client [8.29](https://www.bitvise.com/ssh-client-download) (Download link: https://www.bitvise.com/ssh-client-download)

**Browser**: 

|      |   Chrome   | Firefox     |    Internet Explorer   |  MicrosoftEdge    |   Opera   |  Safari     |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- |
|   Mac   |   Supported    | Supported     |   N/A   |   N/A   |  Supported    |   Supported   |
| Windows | Supported | Supported | IE10+Supported* | Supported | Supported | Not supported |

*: Internet Explorer 10+ is supported; IE9 and down is not. Please be aware that some CSS3 properties and HTML5 elements are not fully supported in IE10, or require prefixed properties for full functionality. 

**Hardware**:

Requirements for Material Design:

- Mac OS X 10.2.3 or newer, with BSD subsystem installed (included in the default install). Mac OS X 10.3 or newer recommended. Version 1.2.0 supports Mac OS X 10.4.

##### How to deploy the code

1. Clone the server

   ```
   cd code
   
   git clone https://github.com/ucl-geospatial/ucesrji-server.git
   ```

2. Switch off the existing servers

   ```
   pm2 list
   
   pm2 stop 0/1/2/...
   ```

3. Start the server created for this app

   - Debug mode (error messages are visible)

   ```
         cd code/ucesrji-server
         node myServer.js
   ```

   - Or keep the server running permanently (error messages are not visible)

   ```
         cd code/ucesrji-server
         pm2 start myServer.js
   ```

4. Clone the question setting app

   ```
   cd code
   git clone https://github.com/ucl-geospatial/ucesrji-questions.git
   ```

5. Remove the existing js, css and images files

   ```
   cd /home/studentuser/code/ucesrji-questions/ucesrji/www
   rm -Rf js
   rm -Rf css
   rm -Rf images
   ```

6. Commit

   ```
   cd /home/studentuser/code/ucesrji-questions
   git add -A
   git commit -am ""
   git push
   ```

7. Clone submodules from GitHub

   ```
   cd ucesrji/www
   git submodule add https://github.com/ruiiiiiur/cege0043-jsReference js
   git submodule add https://github.com/ruiiiiiur/cege0043-cssReference css
   git submodule add https://github.com/ruiiiiiur/cege0043-imagesReference images
   ```

##### How to test the code

1. Open a browser
2. Type the following link: http://developer.cege.ucl.ac.uk:30284/ucesrji-questions/ucesrji/www/index.html

##### Description of HTML file

| File Name     |  Description    |
| ---- | ---- |
| index.html                |  This is the web application page for question setting app. The HTML code in this file allows users to type in their questions when they click on the leaflet map.    |
|  help_question.html               |  This is the user guide for question setting app. Step-by-step instruction with screenshots is displayed on the web page to guide the user through what they need to do.  |

##### Description of JS file

|  File Name     |  Description    |
| ---- | ---- |
|  dailyParticipation.js    |  For question setting app, get the values of daily participation rates for all users.     |
|  questionstartup.js    |  For question setting app, automatically get port number, add a point and add a circle  when the application starts.     |
|  loadDifQs.js    |  For question setting app, load 5 most difficult questions created by all users.    |
|  loadAllQs.js    |  For question setting app, load questions set by all users on the map.  |
|  uploadData.js    |  For question setting app, upload question title, question text, answer 1, answer 2, answer 3, answer 4 and correct answer to the database.    |
|  lastFiveQs.js    |  For quiz app, load the last 5 questions that the user answered.      |
|  loadCorrectAnswerNumber.js    | For quiz app, load the number of answers the user answered correctly. |
|  loadRanking.js    |  For quiz app, load ranking among all users.    |
|   loadTopFive.js   |  For quiz app, load top 5 scorers by D3.js graph.    |
|  quizstartup.js    |  For quiz app, automatically get port number, track location, add a circle and get quiz points when the application starts.     |
|  uploadAnswer.js    | For quiz app, upload question id, correct answer and selected answer to the database.     |
|  userTracking.js    | For quiz app, track the user's location. Add an orange icon to user's current location. Calculate the distance from user's current location to the question points and determine the closest question point.     |
|  utilities.js    |  For both apps, get http port number and https port number. Load all the quiz points after http and https port numbers are received.    |
|  loadFormData.js    | For both apps, load question points created by the current user to the map.     |
|  question.js    |   For both apps, pop up lat/lng when user clicks on the map (lat/lng enters in the form in question setting app). Create a GeoJSON feature showing the location of UCL main gate. Add a point and circle to the map.   |
|leaflet.js| For both apps, add a leaflet map. Add a function to relocate to the main gate of UCL. |

##### Third party code & Open source technologies

Question setting app was built using the following amazing open-source technologies:

- [W3](https://www.w3schools.com/w3js/default.asp)
- [Material design](https://material.io/design/)

- [Leaflet](https://leafletjs.com/)

- [D3.js](https://d3js.org/)

