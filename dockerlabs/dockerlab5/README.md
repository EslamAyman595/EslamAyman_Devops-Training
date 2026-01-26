Lab 5: Multi-Stage Build for a Java Spring Boot Application
Docker Logo

This lab demonstrates how to build and run a Java Spring Boot application using Docker Multi-Stage Build.
Multi-stage builds help reduce the final image size by separating the build stage from the runtime stage

Step 1: Clone the Application Code
Clone the source code from GitHub:

git clone https://github.com/Ibrahim-Adel15/Docker-1.git
cd Docker-1
<img width="1569" height="196" alt="image" src="https://github.com/user-attachments/assets/3ec66773-4dd8-4795-b68f-05c88cf81af0" />

Step 2: Write Multi-Stage Dockerfile
# -------- Stage 1: Build --------
FROM maven:4.0.0-rc-5-eclipse-temurin-17-alpine AS build
WORKDIR /lab5
COPY . .
RUN mvn clean package -DskipTests

# -------- Stage 2: Runtime --------
FROM eclipse-temurin:17.0.17_10-jre-alpine-3.23
WORKDIR /final
COPY --from=build /lab5/target/demo-0.0.1-SNAPSHOT.jar demo-0.0.1-SNAPSHOT.jar
EXPOSE 8080
CMD ["java", "-jar", "demo-0.0.1-SNAPSHOT.jar"]
Stage 1 (Build): Uses Maven + Java 17 to build the application JAR. Stage 2 (Runtime): Uses lightweight JRE image and copies only the JAR to create a smaller final image.
<img width="1382" height="586" alt="image" src="https://github.com/user-attachments/assets/ef16a559-8054-4c0f-8fee-57ebe6379d8e" />

Step 3: Build Docker Image
Create a Dockerfile with the following content:
<img width="1425" height="993" alt="image" src="https://github.com/user-attachments/assets/c624bf1e-387d-48d0-aa35-6550e5b89633" />


docker build -t lab5 .
Build Image
<img width="1347" height="97" alt="image" src="https://github.com/user-attachments/assets/7d903703-9717-4994-aba1-0e1eba70ee86" />


Step 4: Run Container
Run a container named container5 from the lab5 image:

docker run -d -p 8091:8080 --name container5 lab5
Run Container
<img width="1503" height="108" alt="image" src="https://github.com/user-attachments/assets/b19f48fb-fc7c-49bb-a5cd-a291329eb73a" />

Step 5: Test the Application
Test the application by accessing it in your browser or using curl:

curl http://localhost:8091
Or open your browser and navigate to: http://localhost:8091
<img width="1444" height="60" alt="image" src="https://github.com/user-attachments/assets/6e78b73a-673f-428d-af01-217fe35c2810" />


Test App

Step 6: Stop and Delete the Container
Stop and remove the container:

docker stop container4
docker rm container4
<img width="1549" height="147" alt="image" src="https://github.com/user-attachments/assets/f721e62d-013a-4a09-bc40-afb17a366ac9" />

Step 7: Compare Image Sizes
Lab 3: Large image (Maven + source code included) Lab 4: Smaller image (runtime only) Lab 5: Smallest image (multi-stage build, runtime only)

compare App

Summary
The complete Docker workflow for this project:

Clone the Spring Boot application from GitHub
Write a multi-stage Dockerfile
Run and test the container
Stop and delete the container
Compare image sizes with previous labs
