# Voice-Agent---Backend

## Setting Up a Python Virtual Environment

To create and activate a Python virtual environment for the project, follow these steps:

1. **Ensure Python 3 is installed**  
   Check your Python version:
   ```bash
   python3 --version
   ```

2. **Create a virtual environment**  
   In your project directory, run:
   ```bash
   python3 -m venv venv
   ```
   This creates a folder named `venv` containing the virtual environment.

3. **Activate the virtual environment**  
   - On **macOS/Linux**:
     ```bash
     source venv/bin/activate
     ```

4. **Install project dependencies**  
   Once activated, install dependencies with:
   ```bash
   pip install -r requirements.txt
   ```

5. **Deactivate the virtual environment (when done)**  
   ```bash
   deactivate


   ## Running with Docker

   You can build and run this project using Docker for isolated and reproducible deployments.

   1. **Build the Docker image**

      From your project root, run:
      ```bash
      docker build -t voice-agent .
      ```

   2. **Run the Docker container**

      Once the image is built, start a container and map port 5001 (as defined in the Dockerfile):

      ```bash
      docker run -p 5001:5001 voice-agent
      ```

      - This will start the Flask app inside the container, accessible at [http://localhost:5001](http://localhost:5001).
      - You can stop the container using `Ctrl+C` or by finding the container ID and running `docker stop <container_id>`.


   ```

   ## Starting Jenkins and SonarQube Containers

   If you have already set up Jenkins and SonarQube containers previously but stopped them, you can easily restart them without rebuilding using Docker:

   ```bash
   docker start jenkins sonarqube
   ```

   - This command will start both the `jenkins` and `sonarqube` containers in the background, resuming their previous state.
   - After starting, you can access Jenkins at [http://localhost:8080](http://localhost:8080) and SonarQube at [http://localhost:9000](http://localhost:9000), provided you have mapped these ports as shown in their respective documentation.

   If you have not yet created these containers, refer to the setup steps in `Jenkins.md` and `Sonarqube.md`.