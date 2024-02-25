---
mermaid: true
---

# Grails In a Nutshell

--------------------
**An Over Simplified Diagram**

<div class="mermaid"> 

sequenceDiagram
    participant DB as Database
    participant D as Domain
    participant S as Service
    participant CO as Command Object
    participant C as Controller
    participant I as Interceptor
    participant V as View (.gsp/.gson)
    
    V->>I: Request Preprocessing
    I->>C: Good Request Data
    C->>CO: Validate Data For Service
    CO->>S: Validated Data
    S->>D: Data Packaging
    D->>DB: Packaged Data
    I-->>V: Redirect
    C-->>V: Data or New View
    D-->>C: Unpacked Data
    DB-->>D: Data Unpacking

</div>

## Relationships Overview:

----------------------------

- **GSP (Groovy Server Pages):** 
> - The view layer where the UI is generated. 
> - GSPs can dynamically render HTML based on the data passed from controllers.

- *Ex.*

{% highlight html %}

<!DOCTYPE html>
<html>
<head>
    <meta name="layout" content="main"/> <!-- Use the main layout for this GSP -->
    <title>Add New Book</title>
</head>
<body>

<h1>Add New Book</h1>

<!-- Form to create a new book, posting to the save action of the BookController -->
<g:form action="save">
    <!-- Input fields for the book's title, author, and release date, bound to the properties of the BookCommand object -->
    <g:textField name="title" value="${bookCmd?.title}" placeholder="Title"/>
    <g:textField name="author" value="${bookCmd?.author}" placeholder="Author"/>
    <g:datePicker name="releaseDate" value="${bookCmd?.releaseDate}" precision="day"/>
    <!-- Submit button for the form -->
    <g:submitButton name="add" value="Add Book"/>
</g:form>

</body>
</html>

{% endhighlight %}

- **Interceptor:**
> - Intercepts all requests to Controllers, logging an informational message before processing each request.
> - This can be expanded to include more complex logic like authentication, logging, or preprocessing input data.

- *Ex.*

{% highlight java %}

class BookLoggingInterceptor {

    // Constructor for the interceptor, specifying that it should apply to the BookController
    BookLoggingInterceptor() {
        match(controller: "book")
    }

    // Before method that logs an informational message before any action of the BookController is executed
    boolean before() {
        log.info "Accessing BookController at ${new Date()}"
        true // Return true to continue processing the request
    }

    // After method to perform logic after the action executes, but before the view renders
    boolean after() { true }

    // AfterView method to perform logic after the view is rendered
    void afterView() {
        // Post-view rendering logic can be added here
    }
}

{% endhighlight %}

- **Controllers:**
> - Handle HTTP requests, interact with domain classes and services to process business logic, and decide which view to render.


- *Ex.*

{% highlight java %}

class BookController {

    // Dependency injection of BookService
    BookService bookService

    // Action to display a book's details
    def show(Long id) {
        // Retrieve book details for the given id
        def book = bookService.getBookDetails(id)
        // If no book is found, redirect to the list action with a flash message
        if (!book) {
            flash.message = "Book not found"
            redirect(action: "list")
            return
        }
        // Pass the book to the view to be rendered
        [book: book]
    }

    // Action to save a new book
    def save(BookCommand cmd) {
        // Check for validation errors in the command object
        if (cmd.hasErrors()) {
            // If errors exist, render the create view again with the command object
            render(view: "create", model: [bookCmd: cmd])
            return
        }

        // If validation passes, use the service to add the book and then redirect to the list action
        bookService.addBook(cmd)
        redirect(action: "list")
    }
}

{% endhighlight %}

- **Command Object:**
> Encapsulates data for creation, including validation rules.
> It's used in things like save actions of Controllers to validate the input data before passing it to a Service.

- *Ex.*

{% highlight java %}

import grails.validation.Validateable

// @Validateable makes this class capable of being validated according to the constraints defined
// This is especially useful for classes that are not domain classes but still need validation logic
@Validateable
class BookCommand {
    // Define properties that will be bound and validated
    String title       // Title of the book
    String author      // Author of the book
    Date releaseDate   // Release date of the book, can be null

    // Constraints block to enforce validation rules
    static constraints = {
        title blank: false, size: 1..255  // Title cannot be blank and must be within 1 to 255 characters
        author blank: false, size: 1..255 // Author cannot be blank and must be within 1 to 255 characters
        releaseDate nullable: true        // Release date can be null, indicating it's optional
    }
}

{% endhighlight %}

- **Services:**
> - Encapsulate the business logic of the application, providing a layer where complex operations, transactions, and domain class interactions are defined.
> - Services in Grails are transactional by default and can be injected into controllers and other services.

- *Ex.*

{% highlight java %}

import grails.transaction.Transactional

// @Transactional annotation ensures that the methods within the service
// are executed within a transactional context, which means that
// any changes to the database will be committed only if the whole
// method executes successfully, and will be rolled back if an exception occurs
@Transactional
class BookService {

    // Method to fetch book details by id
    def getBookDetails(Long id) {
        Book.get(id) // Retrieves the Book instance for the given id, if exists
    }

    // Method to add a new book using the data from BookCommand
    def addBook(BookCommand cmd) {
        // Creates a new Book instance and saves it to the database
        // with flush:true to ensure immediate persistence
        new Book(title: cmd.title, author: cmd.author, releaseDate: cmd.releaseDate).save(flush: true)
    }
}

{% endhighlight %}

- **Domain Classes:**
> - Represent the application's data model, directly mapping to the database tables. 
> - They define the properties (fields) and constraints for the data.

- *Ex.*

{% highlight java %}

class Book {
    // Define properties of the Book domain class
    String title       // Title of the book
    String author      // Author of the book
    Date releaseDate   // Release date of the book

    // Constraints block to enforce validation rules
    static constraints = {
        title blank: false  // Title cannot be blank
        author blank: false // Author cannot be blank
    }
}

{% endhighlight %}

## Annotations

---------------

> In summary:
> - Annotations in Grails are a powerful mechanism for adding behavior, configuration, and information to various parts of a Grails application, simplifying development and enabling a wide range of functionalities with minimal intrusion into the actual business logic code.

### How Annotations Work

- Annotations work by being processed by the Groovy and Grails runtime, as well as by various compile-time tools.
- When the Grails application starts up or when the application is being compiled, these annotations are read, and the corresponding behavior is applied to the annotated element. For example, the @Transactional annotation tells the Grails framework to proxy the annotated service to handle transaction boundaries transparently.

### Benefits of Using Annotations

> - **Simplicity:**
> > - Annotations keep the code cleaner and more readable by reducing boilerplate configuration.
> - **Configuration by Convention:**
> > - They adhere to the Grails philosophy of convention over configuration, allowing developers to achieve complex functionalities with minimal explicit configuration.
> - **Compile-Time Safety:**
> > - Some annotations enable compile-time checks, which can catch errors early in the development process.
> - **Aspect-Oriented Programming (AOP):**
> > - Annotations like @Transactional facilitate AOP by allowing cross-cutting concerns such as transactions and logging to be applied declaratively, without cluttering the business logic code.

**Custom Annotations**

- Grails and Groovy also support the creation of custom annotations. Developers can define their annotations in Groovy or Java and then process them using AST transformations (Abstract Syntax Tree transformations) or at runtime, allowing for the creation of powerful, reusable components and behaviors.

> **Common Annotations in Grails**
> - **@Transactional:** 
> > - This annotation is used at the service layer to define the transactional behavior of a service class or specific methods within it. 
> > - When you annotate a service class or method as @Transactional, Grails wraps calls to that class or method in a database transaction.
> > - This ensures that all database operations within the transaction boundary either complete successfully or roll back in case of an error, maintaining data integrity.
> - **@GrailsCompileStatic:** 
> > - This annotation is used to indicate that a Grails artifact (like a controller or service) should be statically compiled.
> > - It leverages the Groovy compiler's static compilation capabilities, leading to potential performance improvements and compile-time checking, which can catch errors that might otherwise only be found at runtime.
> - **@Validateable:** 
> > - Typically used with command objects and POGOs (Plain Old Groovy Objects) that need validation logic similar to domain classes but aren't persisted to the database.
> > - This annotation enables these objects to use Grails' validation capabilities, including constraint declarations and error handling.
> - **@Mock:** 
> > - Used in testing, this annotation is applied to a test class to indicate that certain domain classes should be mocked in the Grails application context when the test runs.
> > - This is essential for unit testing, where you need to isolate the class under test and avoid database interactions.
> - **@Profile:** 
> > - Used to indicate that a class is a profile component. 
> > - Profiles in Grails define a set of application features and plugins suitable for a specific type of application. 
> > - For example, a web profile might include configurations and dependencies tailored for web application development.
> - **@Slf4j:** 
> > - This annotation is used to inject a Slf4j logging instance into a Grails artifact, enabling logging without the need to manually create a logger instance. 
> > - This simplifies logging across different components of a Grails application.




### GSP Tags

---------------


GSP allows you to generate dynamic web content using:


- Loops
- Variables
- Conditions
- Groovy code
- and more...

All from within the browser.


**Variables:**
- in GSP can be defined using the ${} syntax.
- These variables can be passed from the controller and accessed directly in the GSP.

{% highlight html %}

<!-- Assume 'message' is a variable passed from the controller -->
<html>
<body>
    <h1>${message}</h1> <!-- Displays the value of 'message' -->
</body>
</html>

{% endhighlight %}

**The <g:set>** tag. 
- This tag allows you to define a variable and assign it a value within the GSP itself.
- The variable can then be used throughout the GSP file.

{% highlight html %}

<%@ page contentType="text/html;charset=UTF-8" %>
<html>
<head>
    <title>Example GSP</title>
</head>
<body>

    <!-- Define a new variable 'greeting' with the value 'WHATUP' -->
    <g:set var="greeting" value="'WHATUP!'" />

    <!-- Use the variable -->
    <h1>${greeting}</h1>

</body>
</html>

{% endhighlight %}

**Conditions:** 
- in GSP can be handled using the <g:if> and <g:else> tags.
- These tags allow you to perform conditional checks and render content accordingly.

{% highlight html %}

<g:if test="${message == 'HAPPY'}">
    <div>This content is displayed if 'someCondition' is true or in this case message equals HAPPY.</div>
</g:if>
<g:else>
    <div>This content is displayed if 'someCondition' is false.</div>
</g:else>

{% endhighlight %}

**Loops**
- in GSP can be created using the <g:each> tag.
- This tag allows you to iterate over collections, such as lists or arrays, and render content for each item.


{% highlight html %}

<ul>
    <g:each var="item" in="${itemList}">
        <li>${item}</li> <!-- Displays each item in 'itemList' -->
    </g:each>
</ul>

{% endhighlight %}

### Params

-------------------

> A quick and dirty understanding of params:
> - You can create params in your gsp
> - You can access and use the params you create in your gsp throughout grails:
> > - In controllers, services, interceptors and command objects

*A working example:*
> Starting from the GSP
> - Create a name and an id attribute in any html element.

{% highlight html %}

<div>
    <input type="hidden" id="keepExistingFile" name="keepExistingFile" value="true" />
</div>

{% endhighlight %}

> These attributes become the params that are accessible within Grails
> - The html **value** attribute can be checked from within the Grails framework and is associated with params.

*A working example continued..*

> GSP

{% highlight html %}

<div>
    <div>
        <label class="form-label">Current Document:</label>
        <span class="form-control disabled">${customItem.customOrderItem.fileUpload.fileName}</span>
    </div>
    <br>
    <div>
        <input type="hidden" id="keepExistingFile" name="keepExistingFile" value="true" />
    </div>
    <br>
    <label class="form-label">To Replace Document:</label>
    <input type="file"
           data-parsley-error-message="Document is Required"
           class="form-control"
           id="replaceDocument"
           name="replaceDocument">
</div>

<!-- JavaScript to Update the Hidden Element Value if File is Uploaded -->
<script>
    document.addEventListener('DOMContentLoaded', function() {
        var replaceDocumentInput = document.getElementById('replaceDocument');
        replaceDocumentInput.addEventListener('change', function() {
            // Check if a file is selected
            var fileSelected = this.files.length > 0;
            console.log('File selected:', fileSelected);

            // Update the hidden input based on file selection
            var keepExistingFileInput = document.getElementById('keepExistingFile');
            keepExistingFileInput.value = fileSelected ? "false" : "true";
            console.log('Keep existing file value:', keepExistingFileInput.value);
        });
    });
</script>

{% endhighlight %}

> The concept:
> - If a new document is uploaded use javascript to listen for the change and update the associated html elements **value** attribute.
> - The javascript is essentially going to just change true to false if a new file is uploaded


> In the Controller:

{% highlight java %}

@Transactional
// Marks the method as transactional, ensuring database operations within this method are part of a single transaction.

def update(Long id){
    // Defines the 'update' action method that takes an ID (of type Long) as a parameter.

    CustomItem customItem = CustomItem.get(id)
    // Retrieves the 'CustomItem' entity from the database using the provided 'id'. If not found, 'customItem' will be null.

    if(!customItem){
        notFound()
        // If 'customItem' is null (meaning the item with the given ID doesn't exist), call the 'notFound()' method which typically sends a 404 response.
        return
    }

    FileItem fileItem = customItem.customOrderItem
    // Retrieves the 'FileItem' associated with the 'CustomItem'. This is presumably an entity related to the document/file handling.

    bindData(customItem, params, [exclude: ['customOrderItem', 'customOrderItemType']])
    // Updates the 'customItem' entity with data from the request parameters ('params'), excluding the 'customOrderItem' and 'customOrderItemType' fields.

    customItem.shippingNote = params.shippingNote
    // Explicitly sets the 'shippingNote' property of 'customItem' to the value provided in the request parameters.

    if (params.keepExistingFile == "false"){
        // Checks if the request parameter 'keepExistingFile' is explicitly set to "false", indicating the user wants to replace the existing file.

        def document = params.replaceDocument
        // Retrieves the new document uploaded by the user from the request parameters.

        FileUpload fileUpload = fileItem.fileUpload
        // Retrieves the 'FileUpload' entity associated with the 'FileItem'. This represents the current document/file.

        fileUpload.fileBytes = document.bytes
        // Updates the byte content of the 'fileUpload' with the byte content of the new document.

        fileUpload.contentType= document.contentType
        // Sets the content type of the 'fileUpload' to the content type of the new document.

        fileUpload.fileName = document.originalFilename
        // Updates the file name of the 'fileUpload' with the original file name of the new document.
    }
    else {
        customItem.customOrderItem.fileUpload.refresh()
        // If 'keepExistingFile' is not "false", refreshes the 'fileUpload' entity to ensure it's up-to-date with the database state. This could be a safety measure or to ensure any lazy-loaded fields are populated.
    }

    customItem.save(flush: true, failOnError: true)
    // Saves the 'customItem' entity to the database, ensuring immediate persistence ('flush: true') and throwing an exception on any validation or persistence errors ('failOnError: true').

    redirect action: "show", id: customItem.id
    // Redirects the user to the 'show' action, passing the ID of the 'customItem', likely to display the updated item details.
}

{% endhighlight %}
