# Django-Deployment-Quick-Guide
Summary of things to consider before deployment

- Install a production-ready webserver for Heroku <br>
	- pip3 install gunicorn~=20.1 <br>
	- pip3 freeze --local > requirements.txt <br>
<br>

- Procfile <br>
	- web: gunicorn my_project.wsgi:application<br>
 
<br>

- Run project using gunicorn <br>
	- gunicorn my_project.wsgi:application <br>
	- *gunicorn codestar.wsgi:application* <br>
	- pip3 freeze --local > requirements.txt <br>
 
<br>

- Connect to PostgreSQL database (2 packages) <br>
	- pip3 install dj-database-url~=0.5 psycopg2~=2.9<br>
	- pip3 freeze --local > requirements.txt<br>
	- import to settings.py:<br>
		- import os<br>
		- import dj_database_url<br>
		- if os.path.isfile('env.py'):<br>
    			- import env<br>
<br>

- Serve static files <br>
	- pip3 install whitenoise~=5.3.0 <br>
	- pip3 freeze --local > requirements.txt<br>
 
<br>
	- Add to settings.py <br>
 		- MIDDLEWARE = [<br>
    			- ...<br>
    			- "whitenoise.middleware.WhiteNoiseMiddleware",<br>
       
<br>

- runtime.txt
	- Add python version (check documentation from heroku for supported versions, pick the closest one) <br>
	- (e.g.) python-3.12.3 <br>
 
<br>

- Remember to at final deployment: 
	- python3 manage.py collectstatic
	- python3 manage.py makemigrations
	- python3 manage.py migrate
	- pip3 freeze --local > requirements.txt
	- DEBUG = False
	- Database
	- Cloudinary
	- Secret key
	- other requirements


- **Mockup**
	- [Techsini](https://techsini.com/multi-mockup/index.php)
	- [Browser Extension necessary for Mockups with Django](https://chromewebstore.google.com/detail/ignore-x-frame-headers/gleekbfjekiniecknbkamfmkohkpodhe)
