# Lab 3: Run Java Spring Boot App in a Docker Container

## Objective
Run a Java Spring Boot application inside a Docker container.

## Prerequisites
- Docker installed and running
- Java JDK 17
- Maven
- Git

## Lab Steps

### 1. Clone the Spring Boot Application
git clone https://github.com/Ibrahim-Adel15/Docker-1.git .

### 2. Write Dockerfile

### 3. Build Docker Image
docker build -t app1 .
<img width="1460" height="747" alt="docker-bulid" src="https://github.com/user-attachments/assets/75e315c9-6ee3-421e-ae14-d625e00f71de" />


### 4. Run Container from the Image
docker run -d -p 8080:8080 --name container1 app1
<img width="1441" height="730" alt="image" src="https://github.com/user-attachments/assets/5542ec38-828e-4c63-b13f-aa4ee60b074c" />


### 5. Test the Application

curl http://localhost:8080
<img width="1460" height="747" alt="docker-bulid" src="https://github.com/user-attachments/assets/b43ee79d-741e-479d-8c7a-011f15b976c3" />

 
