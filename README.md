# Fermentation Monitoring with Prometheus, Grafana, and Pushgateway

This repository hosts a Docker Compose stack designed to monitor data such as temperature, density, and battery levels from a beer fermentation process using an [iSpindel](https://github.com/universam1/iSpindel) device. The stack includes Prometheus for data collection, Grafana for data visualization, and Pushgateway for receiving data from the iSpindel.

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
  - [Usage](#usage)
  - [License](#license)

## Overview

This project sets up a monitoring system for beer fermentation using Docker Compose. It includes the following components:

-   **Prometheus**: For scraping and storing time series data from Pushgateway.
-   **Grafana**: For visualizing the data stored in Prometheus.
-   **Pushgateway**: For receiving data pushed from the iSpindel device.

This setup is an alternative to paid services like Brewfather or similar services. It allows you to monitor your fermentation data without any subscription fees. However, you need to have a server (in this case, your own computer) running whenever you expect the iSpindel to send data.

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

Prometheus is configured to scrape metrics from the Pushgateway. You can find and edit the configuration in `prometheus/prometheus.yml` if needed.

### Grafana

Grafana is pre-configured with a dashboard to visualize the fermentation data. You can import and modify dashboards as required.

### Pushgateway

Pushgateway receives the data from the iSpindel device and makes it available for Prometheus to scrape. Ensure that the iSpindel is configured to send data to the Pushgateway's address.

## Usage

1. Ensure the iSpindel device is configured to push data to the Pushgateway.
2. Access the Grafana dashboard at `http://localhost:3001` to visualize your fermentation data.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
