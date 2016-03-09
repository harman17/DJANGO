# DJANGO
Django is a high-level Python Web framework that encourages rapid development and clean, pragmatic design. It's free and open source.

Django's primary goal is to ease the creation of complex, database-driven websites. Django emphasizes reusability and "pluggability" of components, rapid development, and the principle of don't repeat yourself.

#HOW TO INSTALL

FOR DJANGO WE HAVE TO INSTALL
#1.
   ** PYTHON  **
   ** PIP  ** (FOR MANAGE SOFTWARE PACKAGES) 
   
       FOR THIS TO INSTALL WE HAVE TO SET UP ENVRONMENT PATH FOR PYTHON, SCRIPTS, THEN FOR DJANGO
     NOW ENVIRONMENT PATH HAS BEEN SET. NOW WE NEED TO INSTALL PYTHON AND THEN INSTALL PIP BY GIVING THE COMMAND (PYTHON GET PIP.PY) 
#2.
   SECOND STEP IS TO MAKE THE VIRTUAL ENVIRONMENT(for making a particular project )
   COMMAND:-" VIRTUALENV 'NAME' "
     AFTER MAKING VIRTUAL ENV. THERE IS SEPRETE FOLDER OF VIRTUALENV HAVING NAME AS YOU GIVEN IN COMMAND
  ACTIVATE THE VIRTUALENV BY GIVING THE COMMAND 
    COMMAND:.\scripts\activate IN CMMD
  NOW IN VIRTUALENV WE INSTALL DJANGO BY GIVING THE COMMAND
   COMMAND:pip install django
#3.
   #start the project
   command:python .\scripts\django-admin.py startproject "name of project"
  
#FOR RUN THE SERVER
   command:python manage.py runserver(this will gives you ip address of your srever or projectserver

##IN THIS WAY DJANGO IS  INSTALLED BY ACTIVATING VIRTUALENV

#This framework works according to MVC framework 
   ** model  **
   ** view  **
   ** controller **
  
1. MODEL:- Model works at background of the project.It manages the database of your project.
2. VIEW:- it works at frontend .how the website looks.
3. controller:- It controll or manages the working of molels and views

#FOR MAKING THE DATABASE OR WORKING ON ADMIN PAGE
   command: python manage.py createsuperuser (for old version syncdb is used instead of superuser)
   This creates the admin page of ur website by requeting username and password
   
#STARTING APP
   COMAND: startapp 'app name'
   This make the new folder in the project having subfolderss like
   1. migrations
   2. models
   3. admin

   
#URLS
  when we request something URLS controll the request andsend back the data acc. to our request.therefore we have to define in url in   which we are requesting in views by giving the command
   command: url(r'^$', 'views destination', name='filename'),
   Note: template must exist whose request is made.
   
#DJANGO SETTINGS
   now in django settings 
     IN installed apps we have to define our app for for worling well
     IN dirs we have to set basedir 
     command:[os.path.join(BASE_DIR, "templates")]

IN THIS WAY URLS AND VIEWS ARE CONNECTED THROUGH SETTING

#MODELS
   we make a class in models and define the feilds as per requirement for ex:
   class SignUp(models.Model):
   email = models.EmailField()
   full_name = models.CharField()
   
   now after every change we have to make the migrations and run the server
   command: python manage.py makemigrations
            python manage.py migrate
            python manage.py runserver
   This will create the moled in admin page
   now to show the form in admin page we have to import this form in admin page


#ADMIN
 from.models import signup<br>
    class SignUpAdmin(admin.models.Admin)
    class meta:
    models = signup
  This creates the from in admin page 




   
