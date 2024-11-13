<h2 align="center">
    INNER EV: Fontys Projects
</h2>

<p>
    My main focus this sprint was to create something that I could create tests for. 
    Given the fact that I otherwise had to wait a sprint for my teammates, I took it upon 
    myself to develop the backend that handles the logic and stores the data. 

    The backend is written in Python, using the Flask backend in combination with SQLAlchemy to handle the 
    ORM (object relational mapper). 
</p>
<h3 align="center">
    Troubleshooting the issues I created for myself
</h3>
<p>
    It did not go as planned: there were many issues I encountered due to following different 
    tutorials from different periods. This caused me to use deprecated syntax in the newer version.
    I should have paid attention to which version I was using and stuck to 1 of the tutorials. 
    Another issue I had encountered was following the tutorial too closely and blindly
    implementing code without looking at it more closely. 
    I had to instantiate the database connection with the integrated api call from SQLAlchemy. 
    To make it easier for myself, I created a User object when instantiating the connection and 
    added it to the database.

    Along the way I changed some fields from the models and tried to migrate those changes to the database
    but this did not go well. I thought it was an issue with the models, no luck. Looked at the implementation 
    of the query, no luck.

    The issue was that I created that object everytime I instantiated the application. Given the fact that it was 
    a unique field, this yielded an error and prohibited me from doing anything when running 'flask db migrate "commit text"'. 

    Before I even noticed this, I already recreated the whole database from scratch and rewrote the models to figure out the issue. 
</p>
<h3>
    Defining the endpoints for the application
</h3>
<p>
    There are 3 models that we will use in the database now: 
    - Battery
    - User
    - Coordinates
</p>