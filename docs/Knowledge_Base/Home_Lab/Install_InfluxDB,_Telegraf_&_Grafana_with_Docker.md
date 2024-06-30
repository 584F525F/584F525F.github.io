!!! info ""

    ### Resources

    - [github tig-stack](https://github.com/huntabyte/tig-stack)
    - [Youtube video](https://www.youtube.com/watch?v=QGG_76OmRnA)
    - [Yaml Validator](https://www.yamllint.com/)
    - [Telegraf best practices]([https://www.influxdata.com/blog/telegraf-best-practices/](https://www.influxdata.com/blog/telegraf-best-practices/))


!!! info ""

    ### docker-compose.yml

    ```yaml
    version: "3"

    services:
    influxdb:
    image: influxdb:latest
    volumes:
        - influxdb-storage:/var/lib/influxdb2:rw
    env_file:
        - .env
    entrypoint: ["./entrypoint.sh"]
    restart: on-failure:10
    ports:
        - ${DOCKER_INFLUXDB_INIT_PORT}:8086

    telegraf:
    image: telegraf:latest
    volumes:
        - ${TELEGRAF_CFG_PATH}:/etc/telegraf/telegraf.conf:rw
    env_file:
        - .env
    depends_on:
        - influxdb

    grafana:
    image: grafana/grafana-oss:latest
    volumes:
        - grafana-storage:/var/lib/grafana:rw
    depends_on:
        - influxdb
    ports:
        - ${GRAFANA_PORT}:3000

    volumes:
    grafana-storage:
    influxdb-storage:
    ```


!!! info ""

    ### .env

    ```shell
    DOCKER_INFLUXDB_INIT_MODE=setup

    ## Environment variables used during the setup and operation of the stack
    #

    # Primary InfluxDB admin/superuser credentials
    #
    DOCKER_INFLUXDB_INIT_USERNAME=shgs7XashjdgjksxPPWQ
    DOCKER_INFLUXDB_INIT_PASSWORD=5No4*ada7yasEd2k
    DOCKER_INFLUXDB_INIT_ADMIN_TOKEN=E04wVRvTBo7RxLs87ts65WjQb53Hu2DhiJn_89MqKWbnXNrKhNs78shdsWyG6QyS-JGKqtvAcm9F8zFmc78yxhxwQ==

    # Primary InfluxDB organization & bucket definitions
    #
    DOCKER_INFLUXDB_INIT_ORG=Homelab
    DOCKER_INFLUXDB_INIT_BUCKET=telegraf

    # Primary InfluxDB bucket retention period
    #
    # NOTE: Valid units are nanoseconds (ns), microseconds(us), milliseconds (ms)
    # seconds (s), minutes (m), houwrs (h), days (d), and weeks (w).
    DOCKER_INFLUXDB_INIT_RETENTION=8w


    # InfluxDB port & hostname definitions
    #
    DOCKER_INFLUXDB_INIT_PORT=8086
    DOCKER_INFLUXDB_INIT_HOST=influxdb

    # Telegraf configuration file
    #
    # Will be mounted to container and used as telegraf configuration
    TELEGRAF_CFG_PATH=./telegraf/telegraf.conf

    # Grafana port definition
    GRAFANA_PORT=3000
    ```
