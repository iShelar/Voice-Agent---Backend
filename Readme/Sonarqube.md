## Running SonarQube with Docker

To quickly start a SonarQube server using Docker, run the following command:

```bash
docker run -d --name sonarqube \
  -p 9000:9000 \
  sonarqube:latest
```

- `-d`: Runs the container in detached mode (in the background).
- `--name sonarqube`: Names the running container "sonarqube".
- `-p 9000:9000`: Maps the container's SonarQube port to your host.
- `sonarqube:latest`: Uses the latest SonarQube image from Docker Hub.

Once the container is running, you can access the SonarQube web interface at [http://localhost:9000](http://localhost:9000).

To stop and remove the container:

```bash
docker stop sonarqube
docker rm sonarqube
```

## Default SonarQube Admin Credentials

When you first start SonarQube, log in at [http://localhost:9000](http://localhost:9000) using the default credentials:

- **Username:** `admin`
- **Password:** `admin`

> **Note:** You will be prompted to change the default password on first login. After changing the password, update the `SONARQUBE_ADMIN_PASSWORD` value in your `.env` file.
>

## SonarQube Authentication Tokens

Your SonarQube credentials and tokens are stored in the `.env` file in the project root:
- Admin Username: stored in `SONARQUBE_ADMIN_USERNAME`
- Admin Password: stored in `SONARQUBE_ADMIN_PASSWORD`
- SonarQube Token: stored in `SONARQUBE_TOKEN`
- User Token: stored in `SONARQUBE_TOKEN_USR`
- Project Key: stored in `SONARQUBE_PROJECT`




