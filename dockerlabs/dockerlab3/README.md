Lab 3: Run Java Spring Boot App in a Docker Container
Objective
Run a Java Spring Boot application inside a Docker container.

Prerequisites
Docker installed and running
Java JDK 17
Maven
Git
Lab Steps
1. Clone the Spring Boot Application
git clone https://github.com/Ibrahim-Adel15/Docker-1.git .
<img width="1516" height="250" alt="image" src="https://github.com/user-attachments/assets/2c9f5e94-0369-4cf8-9b93-87e632206a7f" />


3. Write Dockerfile
<img width="1461" height="419" alt="image" src="https://github.com/user-attachments/assets/c03e6b95-318a-45ab-a2f7-814d25182dc4" />

5. Build Docker Image
docker build -t app1 .
<img width="1367" height="133" alt="image" src="https://github.com/user-attachments/assets/316a03cc-bdcf-4490-b388-f3f1d52911b7" />
<img width="1600" height="888" alt="image" src="https://github.com/user-attachments/assets/2106accd-99e6-473f-9e0c-19493f4577f1" />


7. Run Container from the Image
docker run -d -p 8080:8080 --name container1 app1
<img width="1333" height="151" alt="image" src="https://github.com/user-attachments/assets/5a25122a-a085-4ed7-8414-327bcc761df3" />


9. Test the Application
curl http://localhost:8080
 <img width="1600" height="115" alt="image" src="https://github.com/user-attachments/assets/e1d379c4-ff91-445e-b494-0a79f6705085" />
