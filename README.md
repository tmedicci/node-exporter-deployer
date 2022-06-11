# Node-Exporter Deployer for Raspberry Pi-based Devices

This code snippet is a prototype of an automated deployer of Prometheus' Node Exporter for devices based on the Raspberry Pi.
It tries to access the device through Secure Shell (SSH), transfer the `docker-compose.yml` file which contains the Node-Exporter's application and tests the metrics available for scrapping on `http://[ip_addres]:9100/metrics`.

## General Considerations & Requirements
- Enable public-key authentication for Secure Shell (SSH) for the device to be deployed, assuring the device to be deployed is accessible through SSH without asking for a password.
- Consider using a VPN tunnel for production-ready environments.
- This snippet considers the Raspberry Pi's default "pi" user
- Assure docker and docker-compose are properly installed.

## Usage

Run `./node-exporter-deployer` with IP addresses as parameters; e.g:
`./node-exporter-deployer 192.168.2.13 192.168.2.14 192.168.2.12`. This will deploy node-exporter (or update it, if newer version is available) and check for metrics.

Run with `--only-validate` parameter to check for the availability of the metrics (without deploying node-exporter application).