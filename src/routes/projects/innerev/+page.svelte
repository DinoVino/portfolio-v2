<h2  class="doto underline">
    INNER EV: Fontys Projects
</h2>
<div class="text-block">
    <p class="doto">
        My main focus this sprint was to create something that I could create tests for.
        Given the fact that I otherwise had to wait a sprint for my teammates, I took it upon
        myself to develop the backend that handles the logic and stores the data.

        The backend is written in Python, using the Flask backend in combination with SQLAlchemy to handle the
        ORM (object relational mapper).
        <a href="https://github.com/DinoVino/flask-backend" target="_blank">
            <img src="/github-mark-white.svg" width="25px">:(Github repository)
        </a>

    </p>
</div>
<h3 class="doto underline">
    Getting started
</h3>
<div class="text-block">
    <p class="doto">
        In order to get started, I had to configure a lot of things. As you can read in the <a href="../projects/nixos"> nixos</a>,
        parts of the operating system had to be done to make sure that it would work. These were only necessary for the personal
        development.

        If we were to strictly focus on the setup for this project, we had to install Python, along with the packages.
        Using NixOS, this has been declaratively configured. The file can be shared, if the desire to use nix arises.

        For the normal people among us, having installed Python, the next step is to create a virtual environment.
        This ensures that project's packages will not pollute the packages installed on the system and vice versa.

        Clone the repository using Git (either using the terminal or a GUI) and open the terminal within the directory of the Git Repo.
        Run the following command:
        <code>pip install -r requirements.txt</code>

        The necessary packages have been specified in the requirements.txt file.
        In case you are curious, these are the packages.
    </p>
    <ul class="doto">
        <li>
            Flask
        </li>
        <li>
            FlaskSQLAlchemy
        </li>
        <li>
            FlaskMigrate
        </li>
        <li>
            Flask-CORS
        </li>
        <li>
            FlaskRESTful
        </li>
    </ul>
</div>
<h3 class="doto underline">
    Troubleshooting the issues I created for myself
</h3>
<div class="text-block">
    <p class="doto">
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
</div>
<h3 class="doto underline">
    Defining the endpoints for the application
</h3>
<div class="text-block">
    <p class="doto">
        There are 3 models that we will use in the database now:
    </p>
    <ul class="doto">
        <li>
            Batteries
        </li>
        <li>
            Users
        </li>
        <li>
            Coordinates
        </li>
    </ul>
    <p class="doto">
        For these models, properties have been defined so the frontend can request relevant data and
        correct data can be sent to the backend that handles the Machine Learning implementation.
    </p>
    <p class="doto">
        The battery properties are as follows:id, type, status, and a list of coordinates.
        This is the main entity that matters the most to the application. Batteries are the core concept
        that we will work with. We need to save key characteristics of the battery. The brand, model, type are can help us define it.
        We have not yet added the vendor but due to working with an ORM, that is a piece of cake to add.
        The status of the battery is to indicate the overall status. To make it easier for now, we will either
        address it as "good" or "bad". This can help the machine learning algorithm with refining its model by providing labeled data.
        For example: even if there are just a few coordinates with comments, but those coordinates point to damage on vital parts,
        the algorithm will be able to recognise those a lot faster.
    </p>
    <p class="doto">
        The coordinates properties are as follows:id, x, y, and a comment as to what the diagnosed issue is.
        When issues have been diagnosed, a specific point in the image will be marked.
        Along with that, it is required to submit the diagnosis.
    </p>
    <p class="doto">
        The user properties are as follows:id, username, and their email.
        This class is the least flushed out. Functionally, it does not really matter as much.
        In the future, this should be changed or even moved to a module that handles the login of users.
        All we need it for is to log which user input the changes.
    </p>
    <p class="doto">
        These are the endpoints available right now:
    </p>
    <ul>
        <li>
            <code>
                /battery/
            </code>
        </li>
        <li>
            <code>
                /battery/id
            </code>
        </li>
        <li>
            <code>
                /user/id
            </code>
        </li>
        <li>
            <code>
                /AI/process
            </code>
        </li>
    </ul>
</div>
