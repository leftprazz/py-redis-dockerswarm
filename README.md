# py-redis-dockerswarm

This is a sample project that demonstrates how to use Docker Swarm to run a Python application using Redis as its backend. This project has a few simple steps to build and run your application within a Docker Swarm cluster.

## Steps

1. **Build Docker Image**

   First, you need to build a Docker image for your application. Open your terminal and run the following command from the project directory:

   ```bash
   docker build -t app:latest .
   ```

   This will build a Docker image with the name "app" and the version "latest" based on the Dockerfile in this project.

2. **Deploy Application to Docker Swarm**

   After successfully building the Docker image, the next step is to deploy your application to the Docker Swarm cluster. Make sure you have initialized Docker Swarm on your machine.

   Run the following command to deploy the application to the Swarm using a Docker Compose file:

   ```bash
   docker stack deploy --compose-file docker-compose.yml app-swarm
   ```

   This will read the `docker-compose.yml` file and deploy all the services defined in it into the Swarm.

3. **View Your Running Application**

   Once deployed, you can check that your application is running within the Swarm cluster. Ensure that your application is running on one of the nodes within the Swarm.

   You can use the `docker service ps` command to check the status of your services:

   ```bash
   docker service ps app-swarm_web
   ```

   Make sure that all tasks within the service have a "Running" status.

4. **Access Your Application**

   Now that your application is running within the Swarm cluster, you can access it through one of the Swarm nodes. If you are running a Flask application on port 8001, you can access it by opening a browser and navigating to one of the nodes with port 8001.

   Example: `http://<NODE_IP>:8001`

   Replace `<NODE_IP>` with the IP address of the node running the Flask application.

5. **Check the Python Program in the Container**

   To check the Python program running in the container, you can use the `curl` command. For example, to access the application running on port 8001, you can run:

   ```bash
   curl <NODE_IP>:8001
   ```

   This should return a response from your Python program in the container.

## Contributions

If you would like to contribute to this project or report issues, please open [Issues](https://github.com/imprazz07/py-redis-dockerswarm/issues) or create a Pull Request.

Thank you!