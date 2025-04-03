# 🏰 Deploying MySQL in a Docker Container with an Initialization Script 🐬

## 🔹 Prerequisites
✔ Install Docker on your system.
✔ Ensure Docker is running.
✔ Create an SQL initialization script (`Gurleen.sql`) with database and table definitions.

## 💂️ Project Structure
```
MySql/
│── Dockerfile
│── Gurleen.sql
│── README.md
```
This structure keeps all necessary files well-organized.

## 🔧 Step 1: Create a Dockerfile
Create a `Dockerfile` inside the `MySql/` directory:

```dockerfile
# Use MySQL as the base image
FROM mysql:latest

# Copy the SQL script to the container
COPY Gurleen.sql /docker-entrypoint-initdb.d/

# Expose MySQL default port
EXPOSE 3306
```

## 📛 Step 2: Create an SQL Initialization Script
Create a file named `Gurleen.sql` with:

```sql
CREATE DATABASE Gurleen;
USE Gurleen;

CREATE TABLE students (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100),
    age INT
);

INSERT INTO students (name, age) VALUES ('Alice', 20), ('Bob', 24);
```

## 🏰 Step 3: Build the Docker Image
Run the command:

```sh
docker build -t mysql-custom .
```
💡 This creates a custom MySQL image named `mysql-custom`.

## 🚀 Step 4: Run MySQL Container
Start a MySQL container using:

```sh
docker run --name mysql-container -e MYSQL_ROOT_PASSWORD=root -d mysql-custom
```
**Breakdown:**
- 🏷 Creates a container named `mysql-container`.
- 🔑 Sets the root password to `root`.
- 🏃 Runs in detached mode (`-d`).
- 🔧 Uses the `mysql-custom` image.

## 🖥 Step 5: Access the Running Container
To enter the container shell:

```sh
docker exec -it mysql-container bash
```

## 💻 Step 6: Connect to MySQL
Once inside, connect to MySQL:

```sh
mysql -u root -p
```
🔑 Enter the password `root`.

## 🏰 Step 7: Verify Database and Tables
Check available databases:

```sql
SHOW DATABASES;
```

Switch to the `Gurleen` database:

```sql
USE Gurleen;
```

Query the `students` table:

```sql
SELECT * FROM students;
```

## 🎯 Conclusion
✅ You have successfully set up MySQL in a Docker container with an initialization script. Now your database initializes automatically when the container starts! 🚢

---

## 📄 Pushing to GitHub

### Step 1: Create a Repository on GitHub
1. Log in to GitHub.
2. Click on **New repository**.
3. **Repository Name**: `Docker` (or any preferred name).
4. **Visibility**: Choose Public or Private.
5. Click **Create Repository**.

### Step 2: Set Up Git Locally
Initialize Git:

```sh
cd D:\Full Docker
mkdir Docker
cd Docker
git init
```

Clone the empty repository:

```sh
git clone https://github.com/Gurleen-31/Docker.git
cd Docker
```

### Step 3: Add the MySQL Experiment
Create a directory:

```sh
mkdir MySql
cd MySql
```

Copy `Dockerfile`, `Gurleen.sql`, and `README.md` into `MySql/`.

### Step 4: Commit and Push to GitHub
Go back to the main repo:

```sh
cd ..
```

Add all files to Git tracking:

```sh
git add .
```

Commit the changes:

```sh
git commit -m "Added MySQL Docker setup experiment"
```

Push to GitHub:

```sh
git branch -M main
git remote add origin https://github.com/Gurleen-31/Docker.git
git push -u origin main
```

🚀 Your project is now successfully pushed to GitHub! 🌟

