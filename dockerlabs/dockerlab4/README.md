Run Java Spring Boot App in a Container
This lab demonstrates how to containerize and run a Java Spring Boot application using Docker with Java 17.

Step 1: Clone the Application Code
Clone the source code from GitHub:

git clone https://github.com/Ibrahim-Adel15/Docker-1.git
cd Docker-1
<img width="1516" height="250" alt="image" src="https://github.com/user-attachments/assets/ed896be9-b08e-45ec-9a0b-3a389aaca5a2" />

clone Image

Step 2: Build the Application
mvn package
Build Image
<img width="1521" height="584" alt="image" src="https://github.com/user-attachments/assets/15214317-9865-49d9-a1d1-6dae520634f3" />


Step 3: Write Dockerfile
Create a Dockerfile with the following content:

FROM eclipse-temurin:17.0.17_10-jre-alpine-3.23
WORKDIR /lab4
COPY target/demo-0.0.1-SNAPSHOT.jar
CMD ["java", "-jar", "demo-0.0.1-SNAPSHOT.jar"]
EXPOSE 8080
Step 4: Build Docker Image
Build the Docker image with the tag lab4:

docker build -t lab4 .
<img width="1367" height="133" alt="image" src="https://github.com/user-attachments/assets/24fc0358-001a-4e95-a843-f1fa7f529346" />

Image Size Comparison (Lab 3 vs Lab 4)
compare
<img width="1600" height="115" alt="image" src="https://github.com/user-attachments/assets/d7fe0ae9-ea7e-41fd-a505-50d25f99412c" />


Lab 4 image is smaller and more efficient, as it avoids Maven and source code inside the container.

Step 4: Run Container
Run a container named container4 from the lab4 image:

docker run -d -p 8090:8080 --name container4 lab4
Run Container
<img width="1600" height="888" alt="image" src="https://github.com/user-attachments/assets/3e1800fa-d60b-4cbc-aead-4951dd61981f" />


Step 5: Test the Application
Test the application by accessing it in your browser or using curl:

curl http://localhost:8090
Or open your browser and navigate to: http://localhost:8090

Test App

Step 6: Stop and Delete the Container
Stop and remove the container:

docker stop container4
docker rm container4
<img width="1333" height="151" alt="image" src="https://github.com/user-attachments/assets/0ce1b507-970e-4665-8b1b-f4b958de625f" />

Summary
The complete Docker workflow for this project:

Clone the Spring Boot application from GitHub
Successfully containerized Spring Boot app using Java 17
Built optimized Docker image
Ran and tested the application
Managed container lifecycle
