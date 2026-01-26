Lab 8: Custom Docker Network for Microservices 🌐
📝 Lab Description
In this lab, I implemented Docker Networking to connect microservices. I demonstrated how a custom bridge network allows containers to communicate using their Container Names (DNS Resolution) and how containers on different networks remain isolated for security.

🚀 Implementation Steps
1. Cloned the Repository & Prepared Dockerfiles
2. <img width="1552" height="279" alt="image" src="https://github.com/user-attachments/assets/b8ffb5f7-eae6-489c-8a14-0a13d6c67f65" />

I cloned the microservices code and created two optimized Dockerfiles using python:3.9-slim:

Frontend Dockerfile: Installed packages from requirements.txt and exposed port 5000.
Backend Dockerfile: Installed flask and exposed port 5000.
<img width="1561" height="379" alt="image" src="https://github.com/user-attachments/assets/c42c45fe-70c7-4470-b28f-5e9612cc7160" />

2. Network and Image Setup
I created a custom bridge network called ivolve-network and built the images for both the frontend and backend services.

Commands:
docker network create ivolve-network
docker build -t frontend-img ./frontend
docker build -t backend-img ./backend
Network Setup
<img width="1457" height="241" alt="image" src="https://github.com/user-attachments/assets/b4e56c40-a3b6-4c53-8e98-941aaae6fab5" />

3. Running the Containers
I deployed three containers with different network configurations:

backend: Connected to ivolve-network.

frontend1: Connected to ivolve-network (to verify successful communication).

frontend2: Connected to the default bridge (to verify network isolation).

Command

docker run -d --name backend --network ivolve-network backend-img
docker run -d --name frontend1 --network ivolve-network -p 5001:5000 frontend-img
docker run -d --name frontend2 -p 5002:5000 frontend-img
Running Containers
<img width="1435" height="193" alt="image" src="https://github.com/user-attachments/assets/80095cfd-b81c-437f-bd13-e069f8f738e3" />
<img width="1364" height="158" alt="image" src="https://github.com/user-attachments/assets/8af20d26-ce71-4264-9b9c-5b7d99332d05" />
<img width="1439" height="157" alt="image" src="https://github.com/user-attachments/assets/dc38f5ff-fdda-4288-93ff-ce66ad88e6bd" />


4. Communication Verification (The Proof)
I used Python's urllib to test the connectivity between the containers:

Frontend1 (Success): Successfully communicated with the backend and received an HTTP 200 status.

Frontend2 (Failure): Failed to connect with a Temporary failure in name resolution error because it was not on the same network. Success Verification Failure Verification
<img width="1888" height="972" alt="image" src="https://github.com/user-attachments/assets/09988a7b-b42f-4105-8cab-240bb9455427" />

5. Cleanup & Persistence
Finally, I verified the isolation, then stopped and removed all containers and the custom network to clean up the environment.

Command
docker stop frontend1 frontend2 backend
docker rm frontend1 frontend2 backend
docker network rm ivolve-network


