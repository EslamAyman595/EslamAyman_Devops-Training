Lab 1: Building and Packaging Java Applications with Gradle
Objective
Build, test, and package a Java application using Gradle, then run the generated JAR file to verify the application is working correctly.

Prerequisites
Java JDK 17
Gradle 8.5
Git
Lab Steps
1. Clone the project:
git clone https://github.com/Ibrahim-Adel15/build1.git cd build1
<img width="1314" height="272" alt="image" src="https://github.com/user-attachments/assets/f60cb160-da4e-4891-9d36-0aebe8419eff" />


3. Run Unit Tests
gradle test
<img width="1119" height="195" alt="image" src="https://github.com/user-attachments/assets/744779b6-6393-46d5-b64b-ea8f554d2913" />


5. Build the Application
gradle build
<img width="1342" height="70" alt="image" src="https://github.com/user-attachments/assets/758b00e3-b9c3-4191-b466-a6db7522b2b5" />


7. Run the Application
java -jar build/libs/ivolve-app.jar
<img width="1312" height="497" alt="image" src="https://github.com/user-attachments/assets/a5fb7d9e-4463-4556-9637-071cfa1cf3d5" />


9. Verify the Application is Working
Hello Ivolve Trainee
