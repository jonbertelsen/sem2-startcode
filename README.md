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

## The startcode is:
 
- A client/server multipage application developed in Java, JSP, html, css, and bootstrap.
- Built with Maven
- Maintained in a GitHub repository
- Supposed to be deployed on a Tomcat Webcontainer v. 8 or 9.

## The startcode makes use of several software patterns:

- Model View Controller (MVC pattern)
- Frontcontroller pattern
- Command pattern
- Singleton pattern
- Facade pattern

## The startcode contains these features out of the box:

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
 
## Documentation

### How to install the startcode for development

You need three main steps to get started:

1. Git:
   
   1.1 Clone the project (not fork): [https://github.com/jonbertelsen/sem2-startcode](https://github.com/jonbertelsen/sem2-startcode)
   
   1.2 Rename the project folder if needed (to cupcake, webshop etc)
   
   1.3 Make it your own Git project by first removing the `.git` folder (use `rm -rf .git/`). Then 
        create a fresh repo with `git init`, `git branch -m main`,  `git add .`, `git commit -m "First commit"`
   
   1.4 Create a repo on Github and push project

2. Database:

   2.1 Create a schema/database for the project in MySql. Ex: 'cupcake'

   2.2 Create a test-database for the integration tests in MySql. Ex: 'cupcake_test'

   2.2 Run the `dbInit.sql` script in the persistence folder to populate database with user a table. Observe
   carefully the instructions in the script file if you need renaming.
   
2. Java / IntelliJ:
   
   3.1 Open project in IntelliJ
   
   3.2 Rename the project to your own needs
   
   3.2.1 Right-click the project root in IntelliJ and rename
   
   3.2.2 Change the name sem2-startcode in the pom.xml file where needed

   3.3  Rename the database names in two places:

   3.3.1 In the top of the FrontController.java file: 
   Change `startcode` in the jdbc string `jdbc:mysql://localhost:3306/startcode?serverTimezone=CET`
   
   3.3.2 In the top of the UserMapperTest.java class, change the `startcode_test` in the jdbc string.
   
   3.4 Create a Tomcat configuration by running the project
   

   
  

