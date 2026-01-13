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
<img width="1004" height="275" alt="image" src="https://github.com/user-attachments/assets/f8e7f542-58dc-4b98-814b-6555c704b580" />
<img width="1466" height="585" alt="image" src="https://github.com/user-attachments/assets/d527022e-fd20-4ff7-8c2d-777f1c714840" />



3. Run Unit tests:
mvn test
<img width="1365" height="71" alt="image" src="https://github.com/user-attachments/assets/9bdb5da4-1f1c-4d9b-a95e-85f6790e7e52" />


5. Build the application:
mvn package
<img width="1452" height="941" alt="image" src="https://github.com/user-attachments/assets/6e34eff2-d916-46d3-aeac-bf6816cac1a2" />


7. Run the application:
java -jar target/hello-ivolve-1.0-SNAPSHOT.jar
<img width="1459" height="928" alt="image" src="https://github.com/user-attachments/assets/223afe01-9b03-4489-a55b-fb99e8a4efe2" />

8. Verify the application is working
Hello Ivolve Trainee
