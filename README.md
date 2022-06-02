# Deplying-ML-model-on-heroku-demo

### Deployment on Heroku
In order to make the application available for others, we still need a couple of minor steps. 

signing you up for a free account at GIT and Heroku. In order to interact with the two, we need to install GIT and the Heroku command-line interface known as Heroku-CLI. 

Gunicorn
Although flask is wonderful, it’s mainly used for local development. It isn’t designed to handle the requests that a normal web server receives. In order to handle a larger amount of requests, we need to install the gunicorn python library.

pip install gunicorn
Procfile
Having installed gunicorn, we now need to tell Heroku to use it. We do that by creating a file called procfile without file extension (for example, Procfile.txt is not valid.). The file will specify which commands to execute on startup.

Enter this line inside the empty Procfile file:
web: gunicorn app:app

The first ‘app’ represents the name of the python file that runs your application or the name of the module it is in (i.e., if you had an application called run.py, then it would be run:app)
.
The second ‘app’ represents your app name (i.e. app = Flask(__name__)).
Requirements.txt

```
Heroku needs to know which libraries to install to run your application. We can automate this process by running:
pip freeze > requirements.txt
```

This will generate a txt file called requirements.txt with the libraries used in your application. Although brilliant, it does not include all the necessary packages. The list below shows the content of my requirements file (notice that I have included scikit-learn since XGBClassifier object directly interacts with scikit-learn API):

click==8.0.1
Flask==2.0.1
gunicorn==20.1.0
itsdangerous==2.0.1
Jinja2==3.0.1
MarkupSafe==2.0.1
Werkzeug==2.0.1
pandas
xgboost
scikit-learn
pickle-mixin


Runtime.txt
Although not necessary, you can add a runtime.txt file if you wish to specify a specific python version. You can check which python version you're running by typing:

python -V
My runtime.txt file has the following:

python-3.9.6
This is the final stage before deployment, and the MyApp directory should look similar to this:


Login to Heroku

```
If all went well, you should start interacting with your Heroku account through the command line. Open your command line while you are inside the project folder and type:
heroku login
Use the email address and password used when creating your Heroku account. The command will open a browser window, but if you prefer to stay in the command line, just type:

heroku login -i
```




```

Make a git repository for your web app
Create a local git repository by typing:
git init


Add all your local files to the online repository by typing:
git add .

Make sure to include the dot after add. The dot means you are adding the entire directory to the repository.

Commit your files with:
git commit -m "First commit"

```

Create an empty app on Heroku
The next steps consist of creating an empty app on Heroku and sending our local files to that app. And we will be sending the files using git.


```
Create an empty Heroku app:
heroku create <app-name-you-choose>
Once the app has been created, you can enter your Heroku account to get an overview:



git push heroku master
Activate the app and set the number of dynos (anything more than one will cost):

heroku ps:scale web=1
Access app and see performance
If all went well, then you should be able to access your app at:

<app-name-you-choose>.herokuapp.com
You can open it by simply following the URL above or typing:

heroku open
It might take some time to function, so have patience. If all went well, you should have an app running on the web. You should be proud of yourself.



``` 

```
The following commands have been great dealing with all the errors I saw along the way:
heroku local Use this to open Heroku on a local server. Remember to install all required libraries.
heroku logout It should be self-explanatory.
heroku run 'ls -al' A copy of your dyno to have it list the directory contents. This is useful when you add more files and need to check that they have been added on Heroku.
heroku logs --tail With this Heroku command, you can access information about your app’s performance once it’s up and running.
heroku restart It should be self-explanatory.
heroku apps:rename <newname> Rename your app.
```
 


