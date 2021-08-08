# DRF_third_assignment
Django Rest Framework
CRUD functionality with Django REST Framework
Four main API requests are GET, POST, PUT, DELETE.

GET —This request is made when we wanna request some data from the server. Eg: Fetching weather forecast from the weather API.
POST — This request is made when we wanna add data to the server. Eg: User Registration and Login.
PUT — This request is for changing any Existing information in the server. Eg: Updating User Profile.
DELETE — As the name indicates, this request is made where we wanna delete any existing information.
Note: str() ->in every model you should define the standard Python class method str() to return a human-readable string for each object.

Steps for creating a DRF Project

Create a Django Project
Install Django Rest Framework
Create a model and add str as a good practice to return human-readable string
Create API Class
Create API View
List API view
Update API View
Delete API view:
Create Serializer class
Map your APi class with Url in urls.py
Code is ready. Just run your server
Assignment:
Create a Backend of Hospital Management system using DRF. App name should be patient

Patient Data(Models) which needs to be stored
Patient registration number -> patient_reg_no (CharField) -> This should be Unique but should not be a primary key
Patient name -> patient_name (CharField) ->
Patient Email -> patient_email (EmailField)
Patient Mobile Number -> patient_mobile (CharField)
admitted at -> DateTimeField (Text field)(default : current time)
Urls.py
Name in Django URL -> name is used for accessing that URL from your Django / Python code.
For example you have this in 'patient/urls.py
url(r'^main/', views.main, name='main')
In point 2, "main" is the name of this URL
URL namespaces -> URL namespaces allow you to uniquely reverse named URL patterns even if different applications use the same URL names. At Line 21 in hospital/urls.py, path('patient/', include(('patient.urls', 'patient'), namespace='patient')),
namespace='patient is set. Remember, Both Name and Namespace are important for the assignment
For this assignment's test cases we have used some predefined names and namespace
Those names are defined below in the problem statement describes as "Django Url name"
Please make sure you use those names in Django URLs or else your assignment's test will fail Summary: Namespace is "'patient" set in hospital/urls.py file and name is to be set for each URL in 'patient/urls which is stated in the problem statement
Views
You have to use class based views for this assignment
Part 1: GET and POST request for fetching Patients

Django URL name: patient_list_create

Actions:

GET - get list of all patients
POST - Add a new patient
1. GET
Response Format:
[{"id":id,"patient_regNo":patient_regNo,"patient_name":patient_name,"patient_email":patient_email,"patient_mobile":patient_mobile,"admitted_at":admitted_at},   {"id":id,"patient_regNo":patient_regNo,"patient_name":patient_name,"patient_email":patient_email,"patient_mobile":patient_mobile,"admitted_at":admitted_at}]
  
Request: /patient/

Response: [{"id":2,"patient_regNo":"123","patient_name":"rahul","patient_email":"rahul123@gmail.com","patient_mobile":"0000000000","admitted_at":"2021-03-24T21:30:19.667926Z"},{"id":3,"patient_regNo":"1234","patient_name":"argo","patient_email":"argo@gmail.com","patient_mobile":"999999999","admitted_at":"2021-03-24T21:30:57.277179Z"}]

Response Code : 200
2. POST
Response Format:
{"id":id,"patient_regNo":patient_regNo,"patient_name":patient_name,"patient_email":patient_email,"patient_mobile":patient_mobile,"admitted_at":admitted_at}

Request: /patient/

Response: {"id":4,"patient_regNo":"12345","patient_name":"Tarun","patient_email":"Tarun@gmail.com","patient_mobile":"777777777","admitted_at":"2021-03-24T21:39:11.495442Z"}

Response code: 201
Part 2: Retrieve, Update and Delete

Django URL name: patient_update_delete

GET - Retrive information of each patient
PUT - Update any patient information
DELETE - Remove patient from the record
1.GET
Response Format:
{"id":id,"patient_regNo":patient_regNo,"patient_name":patient_name,"patient_email":patient_email,"patient_mobile":patient_mobile,"admitted_at":admitted_at}

Request: /patient/2

Response: {"id":2,"patient_regNo":"123","patient_name":"rahul","patient_email":"rahul123@gmail.com","patient_mobile":"0000000000","admitted_at":"2021-03-24T21:30:19.667926Z"}

Response code: 200
2. PUT
Response Format: 
{"id":id,"patient_regNo":patient_regNo,"patient_name":patient_name,"patient_email":patient_email,"patient_mobile":patient_mobile,"admitted_at":admitted_at}

Request: patient/2" -d "patient_name=rahul1&patient_regNo=123&patient_email=test@gmail.com"

Response
{"id":2,"patient_regNo":"123","patient_name":"rahul1","patient_email":"test@gmail.com","patient_mobile":"0000000000","admitted_at":"2021-03-25T15:48:40.125929Z"}
Response code: 200
3. DELETE
No Response

Request: /patient/2

Response code: 204
Note: id is the primary key which is being passed in the url

Reference: https://www.django-rest-framework.org/api-guide/generic-views/

Installation Steps
Open up your Terminal / Command Line
git clone the repository
cd into the directory of the step (the one you just git cloned)
make sure you have python3 installed
Install virtualenv by following the steps
Mac
python3 -m pip install --user virtualenv
python3 -m venv env
source env/bin/activate

Windows
py -m pip install --user virtualenv
py -m venv env
.\env\Scripts\activate
Run
python -m pip install -r requirements/requirements.txt
No Database setup needs to be done. Do not edit Database settings in settings.py

If everything runs fine till here, create the application using the command

python manage.py startapp patient
Now uncomment the following lines
Line 21 in hospital/urls.py -> path('patient/', include(('patient.urls', 'patient'), namespace='patient')),
Line 41 in hospital/settings.py -> 'patient',
Now Create File hospital/urls.py and add lines

from django.urls import path

from . import views
urlpatterns = []
Run
python manage.py makemigrations
Now Run the Server using command
python manage.py runserver
Great! Start Coding the assignment for above usecase
After Finishing the assignment, you can test them locally using command
coverage run --source='.' manage.py test --no-input
Push the code into the repo using git, Check Pull Requests Tab. Open PR #1
Check if all the tests are Passed
Contact TA for the review
