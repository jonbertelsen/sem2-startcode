# Template for Java webprojects

This startcode is for 2. semester on Computer Science in Lyngby and Bornholm. It has been
developed by the teachers over the past 3-4 years. Java webprojects can obviously be
organized in numerous ways. The purpose of this project is first and foremost to demonstrate
a number of foundational techniques and principles, that can help a software team to keep 
the codebase organized, when developing larger webprojects. The architecture and some of the
details are also serving pedagogical purposes. By saying this, we would like to emphasize
that there is not such a thing as a universal "best practice" when it comes to developing 
systems. It all depends on the scope of the project, the team, and the context. And since
we are on an educational track, we need to keep in mind, that we are here to learn a lot of
basic skills and techniques. Step by step.

### The startcode is:
 
- A client/server multipage application developed in Java, JSP, html, css, and bootstrap.
- Built with Maven
- Maintained in a GitHub repository
- Supposed to be deployed on a Tomcat Webcontainer v. 8 or 9.

### The startcode makes use of several design patterns:

- Model View Controller (MVC pattern)
- Frontcontroller pattern
- Command pattern
- Singleton pattern
- Facade pattern
- Dependency injection

### The startcode contains these features out of the box:

- A frontpage with a header, body, footer, main menu, and links to login and sign up page
- A basic design template with html, css, and bootstrap
- A login page
- A registration / sign up page
- A logout method
- A customer page that can only be accessed by a logged-in user with a customer role
- An Employee page that can only be accessed by a logged-in user with an employee role
- A layered architecture with a frontend, facades, persistence, entities, services and more
- A database and datamapper to handle user logins
- A skeleton for exception handling and logging
- The ability to handle deep url-linking
- A basic security layer, that protects certain pages based on user login and roles
- An easy way to initialize datastructures for the application in first contact
- The JDBC connection is prepared to be initialized from environment variables to avoid
exposing credentials on GitHub.
 
# Documentation

## How to install the startcode for development

You need three main steps to get started:

1. Git:
    1. Clone the project (not fork): [https://github.com/jonbertelsen/sem2-startcode](https://github.com/jonbertelsen/sem2-startcode)
    2. Rename the project folder if needed (to cupcake, webshop etc)
    3. Make it your own Git project by first removing the `.git` folder (use `rm -rf .git/`). Then 
        create a fresh repo with `git init`, `git branch -m main`,  `git add .`, `git commit -m "First commit"`
    4. Create a repo on Github and push project
2. Database:
    1. Create a schema/database for the project in MySql. Ex: 'cupcake'
    2. Create a test-database for the integration tests in MySql. Ex: 'cupcake_test'
    3. Run the `dbInit.sql` script in the persistence folder to populate database with user a table. Observe
   carefully the instructions in the script file if you need renaming.
3. Java / IntelliJ:
    1. Open project in IntelliJ
    2. Rename the project to your own needs 
        1. Right-click the project root in IntelliJ and rename
        2. Change the name sem2-startcode in the pom.xml file where needed
    3.  Rename the database names in two places:
        1. In the top of the FrontController.java file: Change `startcode` in the jdbc string `jdbc:mysql://localhost:3306/startcode?serverTimezone=CET`
        2. In the top of the UserMapperTest.java class, change the `startcode_test` in the jdbc string.
    4. Create a Tomcat configuration by running the project
   
## Architecture

The project uses a layered architecture. The layering is not strict, but in general, the principle
is that no layer should reference other than one layer below itself. We have also tried to
build the architecture around the MVC design pattern.

![architecture](documentation/images/architecture.jpg)
   
### The Client
Is typically a web-browser that `requests` resources on a webserver through the `http protocol`. 
A static html page, an image, a css-file, a javascript file or the result from a dynamic jsp page.

Note that

-  Everything that happens on the client-side is usually related to `frontend programming`
-  The request is typically a `GET-request` or a `POST-request`.
-  It is possible to send parameters along with the request. With `GET` is happens over the uri, like
   `http://localhost:8080/user.jsp?id=23`. With `POST` as form parameters.

### The (web)server
Application code running on a web server is usually called the `backend`.
On the 2. semester we use Tomcat as our web server. Technically speaking Tomcat is called a 
servlet container, because its primary purpose is to process java servlets. However, Tomcat
is also able to act as a webserver, serving static content. The web application deployed on
Tomcat can be organized in various ways. The startcode backend architecture is divided into a
web layer and a business layer. 

#### The Web layer
Everything in the web layer is closely related to receiving a request, getting stuff done in the
business layer, and then sending a response to the desired receiver. We are relying heavily on
a `Frontcontroller` to organize the flow of the application. Before the request hits the 
frontcontroller, an `authorization filter` will check that the client making the request has the
necessary credentials to view the requested resource. This means that a basic security check is done
up front. If the user is allowed into the frontcontroller, the frontcontroller interprets the
uri as a command. Depending on the command, a corresponding java method 
is executed on the server, and a response is sent back to the client. 

*This cycle of client/server request/response is the most foundational thing to understand about
web programming. In this architecture it can be summed up as:*

- A request is sent to the webserver. Ex: http://localhost:8080/customers
- The authorization filter checks for access rights
- The frontcontroller uses `customers` as a command and executes a designated method. Let's call it
  the `customer command`
- The `customer command` returns a name of a target page, that should be sent back to the client. 
  The page is generated on the server (jsp) and returned.
  
That's it. This is a concrete example to make easier to understand:

- We want to view a list of all customers in the browser and requests http://localhost:8080/customers
- The frontcontroller takes the command `customers`, and executes a piece of code:
    - We want to pull a list of customers from the database
    - A method is called in the `service layer`. Let's call it `getAllCustomers`. In our
      architecture we use a number of so-called facade classes to wrap the `datamappers` in the 
      `persistence layer`. The facades are used to decouple the layers, so it will be easier one day
      to swap the persistence layer with a total new implementation without affecting the 
      service layer and beyond.
    - The `getAllCustomers method` in the `customerMapper class` in the `persistence layer` fetches
      all customers and return them to the facade layer.
    - The `getAllCustomers method` in the facade layer returns an arraylist of customers 
      to the `customer command` method.
    - The `customer command` method attatches the list of customers to the request and sends it
        back to the frontcontroller
    - The frontcontroller forwards the flow to the customer.jsp page, that generates the final page
      that is sent back to the client.
      
This can also be visualized as this:

![architecture](documentation/images/lifecycle.gif)


#### The Business layer
Everything in the `business layer` is closely related to the business domain, and core 
functionality of the application.







