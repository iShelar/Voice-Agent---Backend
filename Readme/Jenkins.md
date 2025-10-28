# Jenkins Setup Guide

This guide helps you to set up a Jenkins instance using Docker.

## 1. Run Jenkins in Docker

Run the following command to start Jenkins in a detached container:

```bash
docker run -d --name jenkins \
  -u root \
  -p 8080:8080 -p 50000:50000 \
  -v jenkins_home:/var/jenkins_home \
  -v /var/run/docker.sock:/var/run/docker.sock \
  jenkins/jenkins:lts
```

- `-u root`: Runs Jenkins as root (sometimes needed for Docker socket access).
- `-p 8080:8080`: Maps Jenkins web UI to port 8080.
- `-p 50000:50000`: Maps Jenkins agent connection port.
- `-v jenkins_home:/var/jenkins_home`: Persists Jenkins data.
- `-v /var/run/docker.sock:/var/run/docker.sock`: Allows Jenkins to run Docker commands inside jobs.

## 2. Get the Initial Admin Password

After Jenkins starts, retrieve the initial admin password using:

```bash
docker exec jenkins cat /var/jenkins_home/secrets/initialAdminPassword
```

Copy the password and use it to unlock Jenkins by navigating to [http://localhost:8080](http://localhost:8080).

## 3. Complete Jenkins Setup

1. Open [http://localhost:8080](http://localhost:8080) in your browser.
2. Paste the initial admin password when prompted.
3. Install suggested plugins or select plugins as needed.
4. Create your initial admin user account.
5. Jenkins is now ready for use!

## 4. Stopping and Removing Jenkins

To stop Jenkins:

```bash
docker stop jenkins
```

To remove the container:

```bash
docker rm jenkins
```

The Jenkins home directory is persisted in the `jenkins_home` Docker volume; data will not be lost unless you remove the volume with:

```bash
docker volume rm jenkins_home
```

## 5. Jenkins Credentials

Your Jenkins credentials are stored in the `.env` file in the project root:
- Username: stored in `JENKINS_USERNAME`
- Password: stored in `JENKINS_PASSWORD`
- Initial Pass: stored in `JENKINS_PASS`