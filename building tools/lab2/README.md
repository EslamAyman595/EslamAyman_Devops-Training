Lab 2: Building and Packaging Java Applications with Maven
Objective
Build, test, and package a Java application using Maven, then run the generated JAR file to verify the application is working correctly.

Prerequisites
Java JDK 17
Maven
Git
Lab Steps
1. Clone the project:
git clone https://github.com/Ibrahim-Adel15/build2.git cd build2
<img width="1466" height="585" alt="image" src="https://github.com/user-attachments/assets/273c11f2-4a07-492e-989e-eca663d245ea" />


3. Run Unit tests:
mvn test
![test](https://github.com/user-attachments/assets/be13ada0-fd57-43b6-9ec8-bad87c0c67b3)


5. Build the application:
mvn package
![packeges](https://github.com/user-attachments/assets/5981601d-b8d7-4380-ab76-91216abc8cdf)


7. Run the application:
java -jar target/hello-ivolve-1.0-SNAPSHOT.jar
![run](https://github.com/user-attachments/assets/f12a7b51-fde8-42c9-85b5-31a6e3414917)

8. Verify the application is working
Hello Ivolve Trainee
