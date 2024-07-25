!!! info ""

    Self-hosted photo and video management solution [immich](https://immich.app/)

	### immich installation

	!!! info ""

		### Docker

		#### Install Docker Compose

        ```bash
        sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-linux-$(uname -m)" -o /usr/local/bin/docker-compose
		sudo chmod +x /usr/local/bin/docker-compose
        ```

		#### Set up Docker's apt repository & Add Docker's official GPG key

		```bash
		sudo apt-get update
		sudo apt-get install ca-certificates curl
		sudo install -m 0755 -d /etc/apt/keyrings
		sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
		sudo chmod a+r /etc/apt/keyrings/docker.asc
		```

		#### Add the repository to apt sources

		```bash
		echo \
		"deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
		$(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
		sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
		sudo apt-get update
		```

		#### Install the Docker packages

		```bash
		sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

		```

		#### Create the docker group

		```bash
		sudo groupadd docker
		```

		#### Add your user to the docker group

		```bash
		sudo usermod -aG docker $USER
		```

		#### activate the changes to groups

		```bash
		newgrp docker
		```

		#### TO ENABLE DOCKER START ON BOOT

		```bash
		sudo systemctl enable docker.service
		sudo systemctl enable containerd.service
		```

	!!! info ""

		### Install Immich with Docker

		Immich directory and configuration files

		```bash
		mkdir immich
		cd immich
		```

		#### create a “docker-compose.yaml” file

		```bash
		nano docker-compose.yaml
		```

		#### docker-compose.yaml configuration

		Update the `DB_PASSWORD` variable, enter a randomly created string that will serve as the password for your PostgreSQL user during the initial deployment.

		```yaml
		name: immich

		services:
		  immich-server:
			container_name: immich_server
			image: ghcr.io/immich-app/immich-server:${IMMICH_VERSION:-release}
			command: [ "start.sh", "immich" ]
			volumes:
			  - ${UPLOAD_LOCATION}:/usr/src/app/upload
			  - /etc/localtime:/etc/localtime:ro
			env_file:
			  - .env
			ports:
			  - 2283:3001
			depends_on:
			  - redis
			  - database
			restart: always

		  immich-microservices:
			container_name: immich_microservices
			image: ghcr.io/immich-app/immich-server:${IMMICH_VERSION:-release}
			command: [ "start.sh", "microservices" ]
			volumes:
			  - ${UPLOAD_LOCATION}:/usr/src/app/upload
			  - /etc/localtime:/etc/localtime:ro
			env_file:
			  - .env
			depends_on:
			  - redis
			  - database
			restart: always

		  immich-machine-learning:
			container_name: immich_machine_learning
			image: ghcr.io/immich-app/immich-machine-learning:${IMMICH_VERSION:-release}
			volumes:
			  - model-cache:/cache
			env_file:
			  - .env
			restart: always

		  redis:
			container_name: immich_redis
			image: registry.hub.docker.com/library/redis:6.2-alpine@sha256:51d6c56749a4243096327e3fb964a48ed92254357108449cb6e23999c37773c5
			restart: always

		  database:
			container_name: immich_postgres
			image: registry.hub.docker.com/tensorchord/pgvecto-rs:pg14-v0.2.0@sha256:90724186f0a3517cf6914295b5ab410db9ce23190a2d9d0b9dd6463e3fa298f0
			environment:
			  POSTGRES_PASSWORD: ${DB_PASSWORD}
			  POSTGRES_USER: ${DB_USERNAME}
			  POSTGRES_DB: ${DB_DATABASE_NAME}
			volumes:
			  - pgdata:/var/lib/postgresql/data
			restart: always

		volumes:
		  pgdata:
		  model-cache:
		```

		#### create a “.env” file

		```bash
		nano .env
		```

		#### `.env` file configuration

		`openssl rand -base64 128` to generate random JWT Secret

		Make sure to update the location of where your files will be saved `UPLOAD_LOCATION=<directory_path>.`, for example, “UPLOAD_LOCATION=/mystorage/images.”

		```bash
		UPLOAD_LOCATION=./library
		IMMICH_VERSION=release
		DB_PASSWORD=postgres87s_bkxgnx_pass
		JWT_SECRET=HWrEf6blkaajUtcvMASepa0iDn12+ppYccHIDz4dRI2X/g8Dp1XsceltqGvamvt0
k1vsCyJPC1Cs/oUHZYY/E6PWKkga34TgyPFUVj5iFK9UGsdP/xCB1/jmwqVFyazm
e8jz1Huk2siwvGKYDpmEHGeegDYXp4Zf1imUVcUpKFk=

		# The values below this line do not need to be changed
		######################################################
		DB_HOSTNAME=immich_postgress_x8n7xigxes
		DB_USERNAME=posss78y9hstgres
		DB_DATABASE_NAME=immichs6g7s
		REDIS_HOSTNAME=immich_redis_76sbfjsv
		IMMICH_WEB_URL=http://10.10.10.31:3000
		IMMICH_SERVER_URL=http://10.10.10.31:3001
		DISABLE_REVERSE_GEOCODING=false
		REVERSE_GEOCODING_PERCISION=3
		LOG_LEVEL=log
		```

    Open your browser to [http://127.0.0.1:2283](http://127.0.0.1:2283) and continue your setup.

    In order to recreate the container using docker compose, run `docker compose up -d`. In most cases docker will recognize that the .env file has changed and recreate the affected containers. If this should not work, try running `docker compose up -d --force-recreate`
