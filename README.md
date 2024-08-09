Project Objective
This project focuses on securely setting up Docker containers for an application called "todo-app" by configuring it to run with a non-root user. Running containers without root privileges is an essential security practice. It reduces the risk of the container gaining excessive permissions that could be misused by attackers if vulnerabilities are found. By running the application with limited user rights, we ensure that even in the event of a breach, the attacker's capabilities are restricted.

Environment Setup
1. Modify the Environment Variables
Locate the .env file at the root of your project.
Update the MY_user variable to reflect the non-root user that will run within the container. For example, to use the username myuser, set the variable like so:
env
Copiar código
MY_user=myuser
2. Update Configuration in sqlite.js
Open the sqlite.js file in the src/persistence/ directory.
Make sure the configurations here align with the username set in the .env file.
Pay special attention to the SQLite database file path, which is defined on line 3. The path should be updated to correspond with the specified username. For example, if your user is newuser, update the path to:
js
Copiar código
/home/newuser/app/todos/todo.db
Building and Running Containers
To build and deploy the Docker containers, execute the following command:

bash
Copiar código
docker-compose up --build
This command will initiate the Docker image build process as per the instructions in the Dockerfile and then start the containers as outlined in the docker-compose.yml file.

Accessing the Application
Once the containers are operational, open a web browser and navigate to:

url
Copiar código
http://localhost:3000
Here, you will be able to access the "todo-app" running inside the Docker containers.

Additional Considerations
Verify that all file paths and environment variables are set correctly to avoid configuration issues.
Regularly check for updates to Docker and Docker Compose to utilize the latest features and security updates.
Consider implementing further security practices like network isolation and container vulnerability scanning to enhance the security of your application and infrastructure.
By following these steps, you create a secure and functional environment for running your application within Docker containers, adhering to best practices for containerized applications.
