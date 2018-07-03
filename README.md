# CMS
This application is a basic CRUD application, which maintain the Contact CRUD operations.
The application is made up of MVC and WEB API 2 under the same project.
The main idea of creating the MVC and WEB API is that: MVC acted as a client and WEB API acted as a server in which MVC client make a call to the 
MVC Controller which calls the API controller and API handle the request accordingly.
MVC Clinnt is a simple Scaffolding application, didn't have much changes. The main focus is to the WEB API side.


#Application Environments<br />
Application Developed in:<br />
Visual studio 2015.<br />
.Net framework 4.6<br />
MVC 5<br />
Web API 2<br />
SQL 2016<br />

# Prerequisites<br />
To run the application<br />
1. Provide initialCatalog and baseApiPath in web.config application Setting.<br />
2. Provide your connectionString settings in web.config file.<br />

# Architecture style / Design pattern / Principles used in the application.
MVC 5 : Acted as a client.<br />
Web API 2 : Acted as a server.<br />
Unity 5 : IOC for Dependency injection.<br />
LogWriter : custom class which log the exception in the .txt file date wise.Very basic(only the concept of exception handling is covered).<br />
EntityFramework 6 : ORM.<br />
Factory Method pattern: used to create a context according to the initialCatalog provid.<br />
Unit test cases: Could not get time to write(I can write if time provided.).<br />

# functionalities covered.<br />
# PhoneNumber should be provide in a proper format(10 digit), otherwie error thrown and redirected to the error page.
# This is to show the handled error, and error will log in the given path .txt file.
# But the phoneNumber is kept non-mandatory, can create the contact without the phoneNumber. 
1. Get the list of Contacts(all contacts: no filter with inactive or acctive).<br />
2. Add contact.<br />
3. Edit contact.<br />
4. Delete(Activate/Deactivate) only soft deletethe contact.<br />

# Known issue.
# The below explanation may help you to understand why the issue is persisting.
The issue is because of enabled of entity-framework code first migration enabled.So that for the first time the table Contacts in created by its own, but if later if application is re started then it re-ccreated the context and tried to get the newly created context.But in code we are pointed to previously created context.
if the below issue occours:
#The model backing the <Database> context has changed since the database was created.
  then please uncomment the code.<br/>
  
          //protected override void OnModelCreating(DbModelBuilder modelBuilder)
        //{
        //    Database.SetInitializer<ContactContext>(null);
        //    base.OnModelCreating(modelBuilder);
        //}<br/>
  
  lies in the path: 
  CMS/CMSApp/CMSApp/Models/DataAccessLayer/ContactContext.cs.
 
 #i need to check on this issue.
