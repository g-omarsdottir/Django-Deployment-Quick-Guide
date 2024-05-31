# Django-Deployment-Quick-Guide
Summary of things to consider before deployment

Deployment
•	Install a production-ready webserver for Heroku.
pip3 install gunicorn~=20.1 
pip3 freeze --local > requirements.txt

•	Create file Procfile for production / deployment and add:
web: gunicorn my_project.wsgi:application

•	Run project using gunicorn:
gunicorn my_project.wsgi:application
gunicorn codestar.wsgi:application
pip3 freeze --local > requirements.txt

•	Connect to PostgreSQL database
pip3 install dj-database-url~=0.5 psycopg2~=2.9
pip3 freeze --local > requirements.txt
import to settings.py:
		import os
		import dj_database_url
		if os.path.isfile('env.py'):
    		import env

•	Serve static files
pip3 install whitenoise~=5.3.0 
pip3 freeze --local > requirements.txt
Add to settings.py:
 	MIDDLEWARE = [
    	...
    	"whitenoise.middleware.WhiteNoiseMiddleware",

•	runtime.txt
Add python version (check documentation from heroku for supported versions, pick the closest one) 
python-3.12.3

Remember to at final deployment:
python3 manage.py collectstatic
python3 manage.py makemigrations
python3 manage.py migrate
pip3 freeze --local > requirements.txt
DEBUG = False
Database
Cloudinary
Secret key
other requirements


**Mockup**
https://techsini.com/multi-mockup/index.php 
**Browser Extension for Django**
https://chromewebstore.google.com/detail/ignore-x-frame-headers/gleekbfjekiniecknbkamfmkohkpodhe
