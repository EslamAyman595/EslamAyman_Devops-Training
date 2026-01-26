Lab 7: Docker Volume and Bind Mount with Nginx 🐳
📝 Lab Description
In this lab, I implemented Data Persistence techniques using Docker. I practiced using Named Volumes to persist system logs and Bind Mounts to serve custom content from the host machine. This ensures that important data (like logs) is not lost when the container is deleted, and allows for real-time updates to the web content.

🚀 Implementation Steps
1. Creating the Named Volume
I started by creating a dedicated volume called nginx_logs. This volume is managed by Docker and is used to store Nginx access and error logs safely on the host system.

Command: docker volume create nginx_logs
Verify: docker volume ls
Volume Creation
<img width="1483" height="494" alt="image" src="https://github.com/user-attachments/assets/7abc20a1-17d0-4ab8-82fb-00b812557ce5" />


2. Setting Up the Bind Mount
I created a local directory nginx-bind/html and an index.html file. This file is "mounted" directly into the container, allowing me to update the website content instantly from my local machine.

Path: ~/devops-internship/docker/lab5/nginx-bind/html
<img width="1385" height="44" alt="image" src="https://github.com/user-attachments/assets/526455b6-6684-46e5-9eb8-ea7392b6ae65" />

3. Running the Nginx Container
I launched the Nginx container, connecting both the persistent volume and the bind mount to their respective paths inside the container.

Command: docker run -d -p 8085:80
--name nginx-container
-v nginx_logs:/var/log/nginx
-v $(pwd)/nginx-bind/html:/usr/share/nginx/html:ro
nginx
<img width="1410" height="172" alt="image" src="https://github.com/user-attachments/assets/31cb65cc-11ff-4ad5-8e28-719f35e4ba3f" />

4. Verification & Live Updates
I verified the initial page via curl. Then, I modified the index.html file on my host and confirmed that Nginx served the updated content immediately without a container restart.
<img width="1377" height="56" alt="image" src="https://github.com/user-attachments/assets/4d24af06-d6b0-494f-8501-af6ef0659f38" />

Initial Verify: curl localhost:8085
Update Command: echo "<h1>Hello , After change!</h1>" > nginx-bind/html/index.html
<img width="1392" height="78" alt="image" src="https://github.com/user-attachments/assets/ce9fae48-0542-48c3-a633-9fb6a0af85b4" />

After Update: curl localhost:8085 Verification
5. Log Persistence & Cleanup
I verified that the logs were successfully written to the volume path on the host. Finally, I cleaned up the environment by removing the container and the volume.

Log Path: sudo ls /var/lib/docker/volumes/nginx_logs/_data
<img width="1381" height="101" alt="image" src="https://github.com/user-attachments/assets/bbba1d71-6d16-4e3e-9e44-a11c21cb04ff" />

Cleanup: docker stop nginx-container && docker rm nginx-container docker volume rm nginx_logs
<img width="1287" height="73" alt="image" src="https://github.com/user-attachments/assets/f0c3d597-92aa-4054-8bf5-8d12e0a7f818" />


