# My Wardrobe - Organize your wardrobe

## 1. About

The aim of our project was to develop an app to create a digital version of our closet to have it always with us and to solve the problem that many people face every moring in front of the closet: "I have nothing to wear !". This app helps the user organize all of the pieces of clothing present in his/hers wardrobe.
The menu bar on the top help to navigate the app, in addition, the filters of the research allow the user to find the exact item he/she is looking for.

### 1.1. Demo

Project presentation: https://youtu.be/JO-LADywFp4

## 2. Authors

This project was created by:

* Avezzù Irene
* Sacchetto Joséphine

## 3. Usage

Describe how to compile, package, and run your project here.

To run our appliction is required Java 17.

To build the project, run:

```shell
mvn package
```

To run the main class, run:

```
mvn clean javafx:run
```

Another option to run the project is to open it with IntelliJ IDEA and directly run the Start class. If the error "JavaFX runtime components are missing, and are required to run this application" is generated a new VM Option must be set as shown in this video (https://www.youtube.com/watch?v=hS_6ek9rTco).

Once the application is running the user can either create a new account or use one of the existing one:
- User1: username: username1 - psw: password1!
- User2: username: josephine - psw: jose1!
- User3: username: irene - psw: irene3!


## 4. Implementation

### 4.1. Architectural Overview

We divided our idea into blocks structuring our application in classes.

FRONT-END:
The Start class represents the starting point for our application, it creates an item of LoginPane which, based on the user actions, can lead to a RegisterPane (where the user can create a new account and then be redirected to the LoginPane) or the HomePane. The HomePane allows the user to filter the items (ItemPane), add new items/outfits (AddPane, AddOutfitPane, AddItemPane) or go to its Profile (ProfilePane).

```mermaid
graph TD;
  Start-->LoginPane;
  LoginPane-->RegistrationPane;
  RegistrationPane-->LoginPane;
  LoginPane-->HomePane;
  HomePane-->ItemPane;
  HomePane-->AddPane;
  AddPane-->AddOutfitPane;
  AddOutfitPane-->HomePane;
  AddPane-->AddItemPane;
  AddItemPane-->HomePane;
  HomePane-->ProfilePane;
  ProfilePane-->HomePane;
  ProfilePane-->LoginPane;
  ItemPane-->AddPane;
  ItemPane-->HomePane;
  ItemPane-->ProfilePane;
  
```

BACK-END:
The Item class represent the base element for the wardrobe. Top, Bottom, Dress and Accessorize classes extend it.
```mermaid
graph TD;
  Item-->Top;
  Item-->Bottom;
  Item-->Dress;
  Item-->Accessorize;
```
The Wardrobe class simulates a user's wardrobe which contains a collection of items and outfits.
```mermaid
graph TD;
  Wardrobe-->items;
  Wardrobe-->outfits;
```
The App class is a collection of wardrobes, it provides methods that support the connection to the GUI.
```mermaid
graph TD;
  App-->Wardrobes;
  Wardrobes-->Wardrobe1;
  Wardrobes-->Wardrobe2;
  Wardrobes-->Wardrobe3;
  Wardrobe1-->items1;
  Wardrobe1-->outfits1;
  Wardrobe2-->items2;
  Wardrobe2-->outfits2;
  Wardrobe3-->items3;
  Wardrobe3-->outfits3;
```

### 4.2. Libraries

We used many libraries to develop our application:


We used GSON to develop serialization and deserialization of objects and JavaFX to develop the GUI.

- java.io.* to read and write .txt file
- javax.swing.* for GUI
- java.awt.* for GUI
- java.util.* for creating arrays and input from console
- java.io.IOException for catching exceptions

- frontend
  - import java.awt.geom.Rectangle2D;
  - import java.awt.image.BufferedImage;
  - import java.util.concurrent.TimeUnit;
  - import javax.imageio.ImageIO;
  - import java.io.IOException;
  - import java.awt.\_;
  - import javax.swing.\_;
  - import java.io.InputStream;

- txt database for users
  - import java.io.File;
  - import java.util.ArrayList;
  - import java.util.Scanner;


### 4.3. Programming Techniques

List and explain how you used the 10 programming techniques required for this project.
1.   **GUI:** We used JavaFX to realize the GUI
2.   **Logging:** each user has its own wardrobe so creating an account was a necessity and to allow more users on the same devices logging become fundamental
3.   **I/O file:** we used a file to obviate the absence of a database, we used external text files to "remember" the past uses of the application. Files are also used to import items in a faster way compared to the manual option. In addition, input files are used to assign to each item and outfit a picture
4.   **Try/catch:** try and catch were necessary when working with I/O file  
5.   **Overriding:** the toString of the class Item and Outfit has been overridden
6.   **Overloading:** we used multiple constructors for the Item obj based on which parameters were passed
7.   **Serialization:** we used serialization to simulate a database, the application is saved in a JSON file and reloaded every time the app is open
8.   **Deserialization:** we used deserialization to allow our application to create items objects from a JSON file and to load the application from its JSON file used to simulate a database
9.   **Varargs:** we used Varargs in the Wardrobe class in its search method because in some cases we pass only one parameter to filter but in other cases, we pass multiples string 
10.  **Custom exceptions:** we used custom exceptions to handle problems in the loginPane, registerPane, addItemPane and addOutifitPane

### 4.4. Tests

To assert all actions of our application work in the correct way we worked on both white-box testing and black-box testing. To make sure the application worked we asked the help of some of our friends (both computer science experts and non-experts) to develop the black-box testing suites to test it and based on their feedback we fixed the portions of the code that were not functioning correctly. The GUI was tested both by us and other people to make sure a complete test suit was created.

## 5. Experience

### 5.1. Overall Experience

The idea for this project came to us pretty easily but the realization did not come as easy. We wanted to create something that could be actually useful. We initially struggled with the impossibility of using a database. The choice between a web app and a desktop took us some time but in the end, we choose a desktop app because it would be easier to upload a picture of items for the users.
Even if we had never collaborated on a project we divided in an optimal way the implementations needed for the app. On the other hand, we did not manage the time given in the best way but by the end, we were able to complete the assigned task.

### 5.2. Division of Responsibilities

Description of the roles and responsibilities that each member had in this project:

- **Irene Avezzù:** I was mainly responsible for the implementation of the backend of the app
- **Josephine Sacchetto:** I was mainly responsible for the implementation of the front end of the app
- We worked separately on the actual realisation of the code but the idea for both the structure of the backend and the illustrations of the front end were discussed and outlined together. We developed together the connection between the front and backend. We also worked together when extra materials were needed, such as images or research on structure (e.g. object of JavaFx). We collaborated on the realization of the test suits.

### 5.3. Main Challenges

Elaborate on the main challenges each group member faced throughout the project and how they were surpassed.

- **Irene Avezzù:** The most difficult aspect of this project for me was to implement the test suits because I still struggle in the creation of a complete suit for testing. In addition, working with Maven was difficult, especially in the realisation of the POM file.
- **Josephine Sacchetto:** The most difficult thing for me was the organization of time. The reason was that I had no clear plan to follow so I had to stop and create a detailed plan with day/week/month goals to work toward. By doing this I was able to work better.

### 5.4. Learning Outcomes

Describe what you learned with this project.

- **Irene Avezzù** I learned with Gson developing serialization and deserialization methods. I also learned that connecting the back and front end take much longer than I expected.
- **Josephine Sacchetto:** I learned how to implement the design pattern and that without communication among those working on the same project, one cannot proceed effectively and efficiently toward the result. 

