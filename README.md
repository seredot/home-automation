# README
Basic home automation using Home Assistant, MQTT broker, and Zigbee2MQTT running on Docker Compose.

## Installation
1. Clone this repo.
    ```sh
    git clone git@github.com:seredot/home-automation.git
    ```
2. Install docker -and if compose not part of docker installation- docker-compose.
3. Create configuration files using the example files in data folder:
    ```sh
    cp data/zigbee2mqtt/configuration.yaml.example data/zigbee2mqtt/configuration.yaml
    cp data/mqtt/mosquitto.conf.example data/mqtt/mosquitto.conf
    ```
4. Run compose
    ```sh
    sudo docker compose up -d
    ```
5. Create Home Assistant login at http://localhost:8123.
6. Shut down compose
    ```sh
    sudo docker compose down
    ```
7. Add below lines into newly created Home Assistant configuration file `data/home-assistant/configuration.yaml`:
    ```yaml
    mqtt:
      broker: mqtt
      discovery: true
      birth_message:
        topic: 'hass/status'
        payload: 'online'
      will_message:
        topic: 'hass/status'
        payload: 'offline'
    ```
8. Run compose
    ```sh
    sudo docker compose up -d
    ```
9. Check tooling
    - Home Assistant: http://localhost:8123
    - Zigbee2MQTT: http://localhost:8080

## Troubleshooting
To view the logs, run
```sh
sudo docker compose logs
```
To check the processes, run
```sh
sudo docker compose ps
```

## Backups
The full state resides in `data` folder. Please consider setting up daily automated backups.
