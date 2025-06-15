# 📦 Run Nexus on Droplet and Publish Artifact to Nexus

This project demonstrates how to install and configure Sonatype Nexus on a cloud server and publish artifacts using both a Java Gradle project and a Java Maven project.

---

## 🛠️ Technologies Used

- Nexus Repository Manager OSS
- DigitalOcean (Ubuntu Droplet)
- Linux CLI
- Java
- Gradle
- Maven

---

## 📌 Project Description

### 🔐 Step 1: Install & Configure Nexus on DigitalOcean

- Create a droplet (Ubuntu, 2–4 GB RAM)
- SSH into it: `ssh root@<your-ip>`
- Install Docker and run Nexus via:
  ```bash
  docker volume create --name nexus-data
  docker run -d -p 8081:8081 --name nexus -v nexus-data:/nexus-data sonatype/nexus3
  ```

### 👤 Step 2: Create User on Nexus

- Access Nexus UI at http://<your-ip>:8081
- Create a user with deployment role
- Create private hosted Maven and Gradle repositories

### ⚙️ Step 3: Java Gradle Project

- Configure build.gradle to use Nexus repository
- Build and publish .jar:
  ```bash
  ./gradlew build
  ./gradlew publish
  ```

### ⚙️ Step 4: Java Maven Project

- Configure pom.xml to use Nexus repository
- Build and deploy .jar:
  ```bash
  mvn clean install
  mvn deploy
  ```

## 🗂️ Project Structure

```text
nexus-artifact-publish-demo/
├── java-app/ # Gradle project
├── java-maven-app/ # Maven project
└── README.md
```

## ✅ Outcome

Both projects successfully built and published .jar files to Nexus repositories hosted on DigitalOcean.
