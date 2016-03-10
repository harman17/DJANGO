# DJANGO<br>
Django is a high-level Python Web framework that encourages rapid development and clean, pragmatic design. It's free and open source.

Django's primary goal is to ease the creation of complex, database-driven websites. Django emphasizes reusability and "pluggability" of components, rapid development, and the principle of don't repeat yourself.

#HOW TO INSTALL<br>

FOR DJANGO WE HAVE TO INSTALL<br>
#1.
   ** PYTHON  **<br>
   ** PIP  ** (FOR MANAGE SOFTWARE PACKAGES)<br> 
   
       FOR THIS TO INSTALL WE HAVE TO SET UP ENVRONMENT PATH FOR PYTHON, SCRIPTS, THEN FOR DJANGO<br>
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
   **model**<br>
   **view**<br>
   **controller**<br>
  
1. MODEL:- Model works at background of the project.It manages the database of your project.<br>
2. VIEW:- it works at frontend .how the website looks.<br>
3. controller:- It controll or manages the working of molels and views<br>

#FOR MAKING THE DATABASE OR WORKING ON ADMIN PAGE<br>
   command: python manage.py createsuperuser (for old version syncdb is used instead of superuser)<br>
   This creates the admin page of ur website by requeting username and password<br>
   
#STARTING APP
   COMAND: startapp 'app name'<br>
   This make the new folder in the project having subfolderss like<br>
   1. migrations<br>
   2. models<br>
   3. admin<br>

   
#URLS
  when we request something URLS controll the request andsend back the data acc. to our request.therefore we have to define in url in   which we are requesting in views by giving the command<br><br>
   command: url(r'^$', 'views destination', name='filename'),<br>
  <br><h4> Note: template must exist whose request is made.</h4><br>
   
#DJANGO SETTINGS
   now in django settings<br> 
     IN installed apps we have to define our app for for worling well<br>
     IN dirs we have to set basedir <br><br>
     command:[os.path.join(BASE_DIR, "templates")]<br>

IN THIS WAY URLS AND VIEWS ARE CONNECTED THROUGH SETTING

#MODELS
   we make a class in models and define the feilds as per requirement for ex:<br><br>
   class SignUp(models.Model):<br>
   email = models.EmailField()<br>
   full_name = models.CharField()<br>
   
   now after every change we have to make the migrations and run the server<br><br>
   command: python manage.py makemigrations<br>
            python manage.py migrate<br>
            python manage.py runserver<br><br>
   This will create the moled in admin page<br>
   now to show the form in admin page we have to import this form in admin page


#ADMIN
 from.models import signup<br>
    class SignUpAdmin(admin.models.Admin)<br>
    class meta:<br>
    models = signup<br><br>
  This creates the from in admin page <br>

#CONTEXT
 CONTEXT is used in the view section<br><br>
  when you pass this context to the template render method, {{ title }} would be replaced with home  in your template. This is a example, but really a Context object is the "Context" in which the template is being rendered.<br>
   COMMAND:
   def home(request):
	title = 'welcome'
	form = SignUpForm(request.GET or None)
	context = {
        "title": title,
	    "form": form
	}
	return render(request, "forms.html", context)
  <br><br>
#IN TEMLATE
    {{ title }}
    {{ form  }}<br><br>  (for making form in view section)
    <br>
<br>
# IN VIEW 
 **saving the data received from user in our admin**
  
  <br><Br><br>
	if form.is_valid():
		form.save()
		
		context = {
		"title": "thank you"
	     }
<br>
<br>
#CONTACT FORM
 so there is another form called contact .it is made with same procedure .first connect with urls. and then in view make a form having class name contact<br><br>
 
   def contact(request):
     	title = 'contact us'
 	     form = ContactForm(request.POST  or None)
        	if form.is_valid():
 	       	for key in form.cleaned_data:
 			     print key
<br><br>

#STATIC FILES
   These files includes static part like images etc. for this we have to define in settings for static files then load on required page. we make the seprete folder for static env and static root for these files.
  <br><br>
  STATIC_URL = '/static/'

STATIC_ROOT = os.path.join(os.path.dirname(BASE_DIR), "static_in_env", "static_root")
<br><br>
STATICFILES_DIRS = [
    os.path.join(BASE_DIR, "static_in_pro", "our_static"),
    #'/var/www/static/',
]
<br><br>
THEN import static files in urls<br><br>
    from django.conf.urls.static import static<br>
    
    <br>
    if settings.DEBUG:
	urlpatterns += static(settings.STATIC_URL, document_root=settings.STATIC_ROOT)
	urlpatterns += static(settings.MEDIA_URL, document_root=settings.MEDIA_ROOT)
<br><br>

#ADDING BOOTSTRAP
    NOW COPY THE TEMPLATE ND MAKE THE SEPRETE FILE CALLED BASE.HTML AND CONNECT WITH VIW INSTED OF HOME.HTML. WE CAN SEE THAT THERE        IS NO STYLING IN THIS PAGE.SO WE HAVE TO ADD BOOTSTRAP FILES FOR THE STYLING.<BR><br>
    <link href="{% static 'css/bootstrap.min.css' %}" rel="stylesheet">

    <br><br>
    <link href="../../assets/css/ie10-viewport-bug-workaround.css" rel="stylesheet">

    <br><br>
    <link href="{% static 'css/navbar-static-top.css' %}" rel="stylesheet">
    <br><br>

#crispy forms
    crispy forms make a stylish forms.first we have to install crispy forms<br>
    For install in cmd write:<br>
    "--upgrade django-crispy-forms"
   <br>
   Then in settings we have to define in INSTALL APPS 
   <br>
   'crispy_forms'
   <br>
   Then we have to make the command on that file in which we want the forms look better.<br><br>
   command:{% load crispy_forms_tags %}<br>
   <br>Then adjust the bootstrap according to it.
   
#inheritannce
   With inheritance we can make the two file inherit as base.html and home.html with this code on both the files.
   <br><br>
   {% block content %}

      {% endblock %}
      <br>
  
#DJANGO REGISTRATION REDUX
   This package uses the basic registration and authentication of users. these packages have forms with connected database of registrtion and login forms.these have various steps<br>
   1. we have to copy the registration files in app folder 
   2. then install tis package by giving the command "pip install django-registration-redux"
   3. then we have to define in settings in INSTALLED APPS 'registration'
 
