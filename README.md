# Mosquitto and Node-RED

## Manual installation steps

1. Set a password for Mosquitto
   ```bash
   sudo touch ./config/pwfile
   sudo chmod 0700 ./config/pwfile
   ```
1. Start Mosquitto using `docker compose mosquitto up -d`
1. Enter the container and set the password
   1. ```bash
      docker compose exec mosquitto sh
      ```
   1. ```bash
      mosquitto_passwd -c /mosquitto/config/pwfile <USERNAME>
      ```
1. Get the UID of the Node-RED container user (e.g. `id -u nodered`)
1. Pre-create the nodered directory and set permissions
   ```bash
   docker network create mqtt
   sudo mkdir nodered
   sudo chown -R 1000:1000 nodered/
   ```
