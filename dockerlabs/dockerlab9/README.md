# 🧪 Lab 9: Containerized Node.js & MySQL Stack Using Docker Compose

## 📌 Overview

في هذا اللاب قمنا بعمل Containerization لتطبيق **Node.js** مع **MySQL** باستخدام **Docker Compose**، بحيث يتم تشغيل التطبيق وقاعدة البيانات معًا بطريقة سهلة ومنظمة.

التطبيق يعتمد على قاعدة بيانات MySQL ويشترط وجود Database باسم **ivolve**.

---

## 🎯 Lab Objectives

* Clone كود التطبيق من GitHub
* تشغيل تطبيق Node.js داخل Container
* تشغيل MySQL داخل Container منفصل
* ربط التطبيق بقاعدة البيانات باستخدام Environment Variables
* استخدام Docker Volume لحفظ بيانات MySQL
* التحقق من عمل التطبيق وHealth Checks
* رفع Docker Image على DockerHub

---

## 📂 Project Source Code

تم استخدام الريبو التالي:

```
https://github.com/Ibrahim-Adel15/kubernets-app.git
```

---

## 🛠️ Technologies Used

* Docker
* Docker Compose
* Node.js
* MySQL
* DockerHub

---

## 🚀 Step 1: Clone the Repository

```bash
git clone https://github.com/Ibrahim-Adel15/kubernets-app.git
cd kubernets-app
```

---

## 🐳 Step 2: Docker Compose Configuration

تم إنشاء ملف `docker-compose.yml` لتشغيل التطبيق وقاعدة البيانات.

### docker-compose.yml

```yaml
version: "3.8"

services:
  app:
    build: .
    ports:
      - "3000:3000"
    environment:
      DB_HOST: db
      DB_USER: root
      DB_PASSWORD: root123
    depends_on:
      - db

  db:
    image: mysql:8.0
    environment:
      MYSQL_ROOT_PASSWORD: root123
      MYSQL_DATABASE: ivolve
    volumes:
      - db_data:/var/lib/mysql

volumes:
  db_data:
```

---

## 🔎 Explanation

### App Service (Node.js)

* **build:** بناء Image من Dockerfile المحلي
* **ports:** ربط بورت 3000 داخل الكونتينر مع الجهاز
* **environment:** متغيرات البيئة الخاصة بالاتصال بقاعدة البيانات
* **depends_on:** التأكد من تشغيل MySQL قبل التطبيق

### DB Service (MySQL)

* استخدام Image رسمي MySQL
* تحديد Root Password
* إنشاء Database باسم `ivolve`
* ربط Volume لحفظ البيانات

---

## ▶️ Step 3: Run the Application

```bash
docker-compose up -d
```

التحقق من الكونتينرز:

```bash
docker ps
```

---

## 🌐 Step 4: Verify Application

* فتح التطبيق من المتصفح:

```
http://localhost:3000
```

---

## ❤️ Step 5: Health Checks

```bash
curl http://localhost:3000/health
curl http://localhost:3000/ready
```

---

## 📄 Step 6: Verify Logs

الدخول إلى كونتينر التطبيق:

```bash
docker exec -it <app_container_name> sh
```

عرض ملفات اللوج:

```bash
ls /app/logs
cat /app/logs/access.log
```

---

## 📦 Step 7: Build Docker Image

```bash
docker build -t eslam-node-app .
```

---

## ☁️ Step 8: Push Image to DockerHub

### Login

```bash
docker login
```

### Tag & Push

```bash
docker tag eslam-node-app eslamayman/eslam-node-app:v1
docker push eslamayman/eslam-node-app:v1
```

---

## ✅ Final Result

* تم تشغيل التطبيق وقاعدة البيانات بنجاح باستخدام Docker Compose
* تم التأكد من Health & Readiness
* تم حفظ بيانات MySQL باستخدام Volume
* تم رفع Docker Image على DockerHub

---

## 🖼️ Screenshots

> سيتم إضافة الصور هنا (Containers – App – Health Check – Logs – DockerHub)

---

## ✨ Conclusion

هذا اللاب يوضح قوة Docker Compose في إدارة وتشغيل أكثر من خدمة معًا بطريقة بسيطة ومنظمة، ويعتبر خطوة مهمة قبل الانتقال إلى Kubernetes.
