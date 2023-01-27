# Tineo-Bryan-M2-Challenge
NETFLIX BOOTCAMP CHALLENGE #2

In this challenge, you will build an API for a new social media app called Chatter Book.
User Stories

The Chatter Book API must fulfill the following user stories:

    As a user, I would like to get a list of all users so I know which users are on Chatter Book.

    As a user, I would like to get information about a specific user to learn more about that user.

    As a user, I would like to get all chatterPosts for a user so I know what they post about.

Instructions

    Open the Spring Initializr 

Links to an external site..

Select the following options:

    Project: Maven

    Language: Java

    Spring Boot: 2.7.7 (SNAPSHOT)

    Project Metadata:

        Group: com.company

        Artifact: chatterbook
    note

    Setting the Artifact value will automatically update the values for Name and Package Name.

        Description: Chatter Book Module Challenge

        Packaging: Jar

        Java: 8

For Dependencies add the Spring Web dependency.

Click the Generate button to generate the project.

Unzip the project file that is generated and open it in IntelliJ.

Open the pom.xml file and add the following dependency in the <dependencies> </dependencies> section of the pom.xml file:

<dependency>
    <groupId>junit</groupId>
    <artifactId>junit</artifactId>
    <version>4.13</version>
    <scope>test</scope>
</dependency>

Add the springdoc-openapi-ui dependency in the <dependencies> </dependencies> section of the pom.xml file:

<dependency>
    <groupId>org.springdoc</groupId>
    <artifactId>springdoc-openapi-ui</artifactId>
    <version>1.6.8</version>
</dependency>

Create the ChatterPost model object.

    The ChatterPost model object should contain one string instance variable named text. This variable will contain the text representing a post by a user.

Create the User model object.

    The User model object should contain the following two instance variables:

        name (string)

        chatterPosts (list of ChatterPost objects)
    note

    The list of ChatterPost objects must be called chatterPosts to match the sample data setup in the controller class.

    It is also important to create a constructor that takes a string for name. This constructor will be used to setup the sample data in the controller class to create new Users.

Create a controller class.

    Note: Don't forget the necessary annotations for Spring Boot to recognize it as a controller.

Add the following code and constructor to your controller class to seed your API with sample data:
note

Depending on what you named your controller class, you might need to rename the constructor. The constructor name must match the name of the controller class.

private List<User> userList;

public ChatterbookController() {
  User luis = new User("Luis");
  User sue = new User("Sue");
  User timothy = new User("Timothy");
  User george = new User("George");
  User arturo = new User("Arturo");
  User mariella = new User("Mariella");
  User paolo = new User("Paolo");
  User tri = new User("Tri");
  User jane = new User("Jane");
  User carol = new User("Carol");
  User carl = new User("Carl");

  luis.setChatterPosts(Arrays.asList(new ChatterPost("Hey! This is my first post!"), new ChatterPost("Anybody want to be friends?")));
  sue.setChatterPosts(Arrays.asList(new ChatterPost("I'm bored"), new ChatterPost("Who wants to hang?")));
  timothy.setChatterPosts(Arrays.asList(new ChatterPost("My life is awesome!"), new ChatterPost("Click here to buy my vegan shakes!")));
  george.setChatterPosts(Arrays.asList(new ChatterPost("I like pigs."), new ChatterPost("I love lamp.")));
  arturo.setChatterPosts(Arrays.asList(new ChatterPost("My cat is so cute"), new ChatterPost("My kitten is purr-fect.")));
  mariella.setChatterPosts(Arrays.asList(new ChatterPost("I'll never post again")));
  paolo.setChatterPosts(Arrays.asList(new ChatterPost("Have you ever heard of the band Nirvana?"), new ChatterPost("Pearl Jam 4 Life")));
  tri.setChatterPosts(Arrays.asList(new ChatterPost("You definitely grew up in the 90s if you get these 10 references."), new ChatterPost("I don't get this generation? Everyone expects a participation trophy.")));
  jane.setChatterPosts(Arrays.asList(new ChatterPost("I just wrecked my dad's car. He's going to kill me!"), new ChatterPost("Grounded.... for 5 months :( ")));
  carol.setChatterPosts(Arrays.asList(new ChatterPost("Does anyone have some imodium?")));
  carl.setChatterPosts(Arrays.asList(new ChatterPost("My roommate is awful!!!!"), new ChatterPost("Anyone know a room for rent in Hyde Park?")));

  userList = Arrays.asList(luis, sue, timothy, george, arturo, mariella, paolo, tri, jane, carol, carl);
}

    Remember, in the real world, data would not be hard-coded into the constructor of the controllers. This sample data is just a stand-in until we learn about databases.

The API needs to provide a GET route for each of the following (remember, each route path must be unique):

    A list of all users

    A single user by username

    A list of chatterPosts for a user by username

