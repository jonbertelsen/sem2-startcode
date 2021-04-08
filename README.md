# Template for Java webprojekts

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
- A customer page that can only be accessed by a logged in user with a customer role
- An Employee page that can only be accessed by a logged in user with an employee role
- A layered architecture with frontend, facades, persistence, entities, services and more
- A database and datamapper to handle userlogins
- A skeleton for exceptionhandling and logging
- The ability to handle deep url-linking
- A basic security layer, that protects certain pages based on userlogin and roles
- An easy way to initialize datastructures for the application in first contact
- The JDBC connection is prepared to be initialized from environment variables to avoid
exposing credentials on GitHub.
 
## Dokumentation



