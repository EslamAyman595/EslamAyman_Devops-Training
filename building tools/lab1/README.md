# Lab 1: Building and Packaging Java Applications with Gradle

## Objective
Build, test, and package a Java application using Gradle, then run the generated JAR file to verify the application is working correctly.

## Prerequisites
- Java JDK 17
- Gradle 8.5
- Git

## Lab Steps
### 1. Clone the project:
   git clone https://github.com/Ibrahim-Adel15/build1.git
   cd build1
   <img width="1235" height="361" alt="image" src="https://github.com/user-attachments/assets/619c685a-ea46-43b2-a8c6-7202870317c0" />

   <img width="1470" height="304" alt="image" src="https://github.com/user-attachments/assets/d0b7c64c-71f7-496c-88e2-4b86d050bfd5" />


### 2. Run Unit Tests
   gradle test
   <img width="1119" height="195" alt="image" src="https://github.com/user-attachments/assets/fcbca67c-c29c-4be1-8e53-e94de055e00f" />


### 3. Build the Application
   gradle build
   <img width="1312" height="497" alt="image" src="https://github.com/user-attachments/assets/fc220aff-6553-4412-aa43-d002be340771" />


### 4. Run the Application
   java -jar build/libs/ivolve-app.jar
   <img width="1342" height="70" alt="image" src="https://github.com/user-attachments/assets/891d5abd-381c-48a1-8e9e-7eebbf2eb06d" />


### 6. Verify the Application is Working
   ```bash
   Hello Ivolve Trainee
