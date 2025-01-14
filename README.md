# Flask App with MySQL - Dockerized  
This repository contains a Dockerized Flask application integrated with a MySQL database. The app allows users to submit messages that are stored in the database and displayed on the frontend.  
## Features  
- **Flask Backend:** Handles requests and interacts with the MySQL database.  
- **MySQL Database:** Stores user-submitted messages.  
- **Dockerized Deployment:** Simplifies setup and ensures a consistent environment.  
- **Frontend:** Displays messages and includes a form for submitting new ones.  
## Prerequisites  
Before starting, ensure you have the following installed:  
- **Docker**: For containerization.  
- **Git** (optional): For cloning the repository.  
## Project Structure  
├── eks-manifests/ # Kubernetes manifests for EKS deployment
├── k8s/ # Additional Kubernetes configuration
├── templates/ # Templates for Flask application
├── app.py # Main application file
├── Dockerfile # Dockerfile for building the app image
├── Dockerfile-multistage # Multi-stage build Dockerfile
├── docker-compose.yml # Docker Compose file for multi-container setup
├── Jenkinsfile # Jenkins pipeline configuration
├── Makefile # Build automation instructions
├── message.sql # SQL schema for the messages table
├── requirements.txt # Python dependencies
└── README.md # Project documentation




### 1. Clone the Repository  
```bash  
https://github.com/ramha-ch/flaskapp.git
cd your-repo-name  
2. Configure Environment Variables
Create a .env file in the project directory:
2. bash
Copy code
touch .env  
Add the following variables to the .env file:
env
Copy code
MYSQL_HOST=mysql  
MYSQL_USER=your_username  
MYSQL_PASSWORD=your_password  
MYSQL_DB=your_database  
3. Build and Run the Containers
Use Docker Compose to build and start the application:
bash
Copy code
docker-compose up --build  
Database Setup
To create the messages table in your MySQL database, use a MySQL client or tool and execute the following SQL commands:



SQL
Copy code
CREATE TABLE messages (  
    id INT AUTO_INCREMENT PRIMARY KEY,  
    message TEXT  
);  
Usage
Access the Application
•	Frontend: Open http://localhost in your web browser.
•	Backend: Access http://localhost:5000 for API endpoints.
Interact with the App
1.	Submit new messages through the form on the frontend.
2.	Use the /insert_sql endpoint to directly insert messages into the database via SQL queries.

Docker-compose up --build  
Database Setup
To create the messages table in your MySQL database, use a MySQL client or tool and execute the following SQL commands:
SQL
Copy code
CREATE TABLE messages (  
    id INT AUTO_INCREMENT PRIMARY KEY,  
    message TEXT  
);  

Usage
Access the Application
Frontend: Open http://localhost in your web browser.
Backend: Access http://localhost:5000 for API endpoints.
Interact with the App
Submit new messages through the form on the frontend.
Use the /insert_sql endpoint to directly insert messages into the database via SQL queries.

To push your Dockerized Flask app with MySQL to Docker Hub, follow these steps:
1. Build the Docker Image
Ensure your Dockerfile and application are correctly set up. Navigate to your project directory containing the Dockerfile. Then build the Docker image:
bash
Copy code
docker build -t your-dockerhub-username/flask-mysql-app:latest .  
•	Replace your-dockerhub-username with your Docker Hub username.
•	latest can be replaced with a specific tag if needed.
2. Run Tests and Verify
Before pushing, make sure everything works as expected:
bash
Copy code
docker run -d -p 5000:5000 your-dockerhub-username/flask-mysql-app:latest  
3. Tag the Image
Tag the Docker image with your Docker Hub username and repository name:
bash
Copy code
docker tag your-dockerhub-username/flask-mysql-app:latest your-dockerhub-username/flask-mysql-app:version1.0  
4. Push the Image to Docker Hub
Push the tagged image to Docker Hub:
bash
Copy code
docker push your-dockerhub-username/flask-mysql-app:version1.0  
This will upload the Docker image to your Docker Hub repository under the specified tag (version1.0).
________________________________________
Ensure that you have logged into Docker Hub by running:
bash
Copy code
docker login  
Use your Docker Hub username and password to authenticate.

