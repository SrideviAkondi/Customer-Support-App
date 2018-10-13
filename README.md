# Customer Support Application
A customer support application built using J2EE

Once you set up and launch the application. Login and navigate into the application and explore the functionalities mentioned below:

- Login: To login into the system. You can login into the application using the details belowUser Name: NicholasPassword: password
- Creating a ticket: The system allows the user to create a   ticket. Enter the subject, body and an attachment click submit to create a ticket.
- List Tickets: Clicking on that option lists the tickets you created. 
- List Sessions: List the number of sessions in the application. 
- Logout: Exits from the application and returns to the login page  

## Understanding the Application Flow

- Login Functionality:
Navigate to web-> Web-INF-> view -> login.jsp 
Related Files:login.jsp, LoginServlet.java
You can find the login page code over there. Observe the form tag in the .jsp page. It has an attribute action which contains value “/login” and the method is post. This means that it’s mapped to a controller with the url pattern “/login” and the doPost method under that controller is going to get invoked. Now open the login controller under com.wrox package. Try to understand the doPost method. Under doPost method you could find a section of code which checks whether the user-name and password you specified is valid.Now you could see that they are checking the username & password from a   set of hardcoded values in HashTable. You can login into the application with any of those user id and passwordNow you got an idea how the control is transferred from the jsp page to the controller class.

- Create Ticket:
Now the understand the create ticket functionality and explain your understanding how the
control is    transferred and saved into the java objects Related Files:ticketForm.jsp, TicketServlet.javaWhen create ticket link is    clicked, goGet() of TicketServlet is    invoked because of the highlighted code snippet below. /tickets is    mapped to TicketServlet.java using @Webservlet annotation in TicketServlet.java

```
<a href="<c:url value="/tickets">
<c:param name="action" value="create" /></c:url>">Create a   Ticket</a>   

```
- Now the ticketForm.jsp is rendered. Once you input the information and then click submit. It invokes the the doPost() method which in-turn invokes the create ticket method. This method gets all the data from create ticket form and then puts it   into the map. 
```
private Map<Integer, Ticket> ticketDatabase =   new LinkedHashMap<>();
```
- All the ticket information is stored in this map as of now. This map is used to render data in list ticket and view ticket screens.
