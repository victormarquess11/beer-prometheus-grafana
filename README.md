# Fermentation Monitoring with Prometheus, Grafana, and Pushgateway

This repository hosts a Docker Compose stack designed to monitor fermentation data such as temperature, density, and battery levels from a beer fermentation process using an [iSpindel](https://github.com/universam1/iSpindel) device. The stack includes Prometheus for data collection, Grafana for data visualization, and Pushgateway for receiving data from the iSpindel.

## Table of Contents

- [Fermentation Monitoring with Prometheus, Grafana, and Pushgateway](#fermentation-monitoring-with-prometheus-grafana-and-pushgateway)
  - [Table of Contents](#table-of-contents)
  - [Overview](#overview)
  - [Requirements](#requirements)
  - [Installation](#installation)
  - [Configuration](#configuration)
    - [Prometheus](#prometheus)
    - [Grafana](#grafana)
    - [Pushgateway](#pushgateway)
    - [Network Configuration](#network-configuration)
  - [Usage](#usage)
  - [License](#license)

## Overview

This project sets up a robust monitoring system for beer fermentation using Docker Compose. The stack consists of the following components:

-   **Prometheus**: Responsible for scraping and storing time series data from Pushgateway.
-   **Grafana**: Used for visualizing the data stored in Prometheus.
-   **Pushgateway**: Acts as an intermediary for receiving data pushed from the iSpindel device.

This setup provides a cost-effective alternative to subscription-based services like Brewfather, allowing you to monitor your fermentation process without recurring fees. However, it requires that your server (or computer) is running whenever you expect the iSpindel to send data.

## Requirements

-   Docker
-   Docker Compose
-   iSpindel device

## Installation

1. Clone the repository:

    ```sh
    git clone https://github.com/your-username/fermentation-monitoring.git
    cd fermentation-monitoring
    ```

2. Start the Docker Compose stack:

    ```sh
    docker-compose up -d
    ```

3. Access the services:
    - Prometheus: `http://localhost:9090`
    - Grafana: `http://localhost:3001` (default login: `admin` / `admin`)

## Configuration

### Prometheus

Prometheus is pre-configured to scrape metrics from the Pushgateway. The configuration can be found and adjusted in `prometheus/prometheus.yml` as needed.

### Grafana

Grafana is pre-configured with a dashboard to visualize the fermentation data. You can import additional dashboards or modify the existing ones to suit your requirements.

### Pushgateway

Pushgateway is set up to receive data from the iSpindel device and make it available for Prometheus to scrape. Ensure the iSpindel is configured to send data to the Pushgateway's address.

### Network Configuration

Make sure your server has a reserved IP address within your network.

The iSpindel should be configured to send data to this reserved IP on port 9091 (the Pushgateway port).

Alternatively, you can use dynamic DNS services or configure your router to forward the necessary ports to your server's IP address, ensuring consistent communication with the iSpindel device.

## Usage

1. Ensure the iSpindel device is configured to push data to the Pushgateway.
2. Access the Grafana dashboard at `http://localhost:3001` to visualize your fermentation data.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
