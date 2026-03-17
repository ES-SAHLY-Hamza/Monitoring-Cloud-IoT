## Solution IoT basée sur une architecture microservices
<img src="https://messungbacd.com/images/solutions/cloud-analysis.jpg" alt="Parc" width="1100" height="400"/>

# Monitoring Cloud and IoT 

Ce projet et son architecture ont été conçus dans le cadre d'une solution IoT basée sur une architecture microservices. Il permet la gestion et la surveillance des dispositifs connectés en temps réel.

## Description
Monitoring Cloud and IoT est une application basée sur une architecture microservices permettant de gérer l'authentification des utilisateurs, l'administration des dispositifs IoT et la surveillance des données transmises par ces derniers. L'objectif est de fournir une plateforme robuste et scalable pour le suivi en temps réel des appareils connectés.


## 🚀 Grafana pour device monitoring 
![Microk8s Pods](https://github.com/Ismail-AABARI/Monitoring-Cloud-IoT/blob/main/Grafana%20monitoring.jpg)

## 📜 Prometheus 
![Microk8s Pods](https://github.com/Ismail-AABARI/Monitoring-Cloud-IoT/blob/main/Promotheus%20.jpg)

## 🌤️ Meteo data monitoring en utilisant le Machine Learning
![Microk8s Pods](https://github.com/Ismail-AABARI/Monitoring-Cloud-IoT/blob/main/Meteo%20Monitoring%20Data%20db%20using%20ML.jpg)

## 📊 Device Page 
![Microk8s Pods](https://github.com/Ismail-AABARI/Monitoring-Cloud-IoT/blob/main/Page%20devices.jpg)

## 🔗 Microk8s Pods Up 
![Microk8s Pods](https://github.com/Ismail-AABARI/Monitoring-Cloud-IoT/blob/main/pods.png)

## 📂 Base de données Postgresql (BD signing et BD devices)
![Microk8s Pods](https://github.com/Ismail-AABARI/Monitoring-Cloud-IoT/blob/main/signingDB.jpg)
![Microk8s Pods](https://github.com/Ismail-AABARI/Monitoring-Cloud-IoT/blob/main/DeviceDB.jpg)

## 📂 Base de données MongoDB 
![Microk8s Pods](https://github.com/Ismail-AABARI/Monitoring-Cloud-IoT/blob/main/mongoDB.jpg)

## RabbitMQ
![Microk8s Pods](https://github.com/Ismail-AABARI/Monitoring-Cloud-IoT/blob/main/RabbitMq%201.jpg)
![Microk8s Pods](https://github.com/Ismail-AABARI/Monitoring-Cloud-IoT/blob/main/RabbitMq%202.jpg)
![Microk8s Pods](https://github.com/Ismail-AABARI/Monitoring-Cloud-IoT/blob/main/RabbitMq%203.jpg)

## 🔗 All pods 
![Microk8s Pods](https://github.com/Ismail-AABARI/Monitoring-Cloud-IoT/blob/main/Pods%20.jpg)

## 📝 Pods microk8s default 
![Microk8s Pods](https://github.com/Ismail-AABARI/Monitoring-Cloud-IoT/blob/main/pods%20default.jpg)

## 🔗 Pods Observability 
![Microk8s Pods](https://github.com/Ismail-AABARI/Monitoring-Cloud-IoT/blob/main/pods%20observability.jpg)

## 🔗 Service Observability 
![Microk8s Pods](https://github.com/Ismail-AABARI/Monitoring-Cloud-IoT/blob/main/Service%20Observability.jpg)

## 🔧 Docker Containers Up 
![Docker Containers](https://github.com/Ismail-AABARI/Monitoring-Cloud-IoT/blob/main/Containers%20de%20docker.png)

## 📜 Test Via Curl
![ Test Via Curl](https://github.com/Ismail-AABARI/Monitoring-Cloud-IoT/blob/main/Les%20Tests%20fonctionnent.png)

## Architecture du projet

L'application est composée de plusieurs microservices communiquant entre eux :

1. **Signing Microservice**
   - Gère l'authentification et l'autorisation des utilisateurs.
   - Technologies : Flask, PostgreSQL, Redis.

2. **Device Management Microservice**
   - Assure l'enregistrement, la configuration et le suivi des appareils IoT.
   - Technologies : Flask, PostgreSQL, Redis.

3. **Monitoring Microservice**
   - Collecte et affiche en temps réel les données envoyées par les dispositifs IoT.
   - Technologies : Flask, MongoDB, Socket.IO.

L'infrastructure repose sur **Docker** et **Kubernetes**, avec **RabbitMQ** pour la communication asynchrone entre les services.

## Communication entre microservices

- **Signing & Device Management** : Communication via API REST.
- **Device Management & Monitoring** : Communication asynchrone via RabbitMQ.
- **Monitoring** : Mise à jour des clients en temps réel avec WebSockets (Socket.IO).

## 🔧 **Technologies utilisées**

- **Backend** : Flask (Microservices)
- **Bases de données** : PostgreSQL (Signing & Device Management), Redis (Cache), MongoDB (Monitoring)
- **Messagerie asynchrone** : RabbitMQ
- **Communication en temps réel** : Socket.IO
- **Orchestration** : Kubernetes (MicroK8s)
- **Containerisation** : Docker
- **API Gateway** : NGINX
- **Surveillance et monitoring** : Prometheus, Grafana
- **Simulation des données IoT** : MQTT, scripts Python

## 📂 **Structure du projet**
```
Monitoring-Cloud-IoT/
│── Microservices/
│   │── device-management/
│   │   │── business/
│   │   │   ├── device_service.py
│   │   │── config/
│   │   │── controllers/
│   │   │   ├── device_controller.py
│   │   │── dal/
│   │   │   ├── device_dal.py
│   │   │── models/
│   │   │── Tests/
│   │   │── app.py
│   │   │── Dockerfile
│   │   │── requirements.txt
│   │
│   │── monitoring/  *(Même structure que device-management)*
│   │── signing/  *(Même structure que device-management)*
│   │── gateway/
│   │── nginx/
│   │   │── conf.d/
│   │   │   ├── default.conf
│   │   │── nginx.conf
│   │── default.conf
│   │── mongodb-deployment.yaml
│   │── mongodb-service.yaml
│   │── monitoring-deployment.yaml
│   │── monitoring-service.yaml
│   │── device-management-deployment.yaml
│   │── device-management-service.yaml
│   │── docker-compose.yml
│   │── nginx-claim0-persistentvolumeclaim.yaml
│   │── nginx-claim1-persistentvolumeclaim.yaml
│   │── nginx-deployment.yaml
│   │── nginx-pv.yaml
│   │── postgres-data-persistentvolumeclaim.yaml
│   │── postgres-deployment.yaml
│   │── postgres-pv.yaml
│   │── postgres-service.yaml
│   │── rabbitmq-deployment.yaml
│   │── rabbitmq-service.yaml
│   │── signing-deployment.yaml
│   │── signing-service.yaml
│
│── front-end/
│   │── build/
│   │── node_modules/
│   │── public/
│   │   ├── data/
│   │   │   ├── weather_data_with_predictions.csv
│   │   ├── favicon.ico
│   │   ├── index.html
│   │   ├── logo192.png
│   │   ├── logo512.png
│   │   ├── manifest.json
│   │   ├── robots.txt
│   │── src/
│   │   │── assets/
│   │   │── components/
│   │   │   ├── Auth/
│   │   │   ├── Dashboard/
│   │   │   │   ├── DashboardStats.jsx
│   │   │   │   ├── Sidebar.jsx
│   │   │   ├── Devices/
│   │   │   ├── Monitoring/
│   │   │   ├── Weather/
│   │   │   │   ├── WeatherCharts.jsx
│   │   │   ├── ProtectedRoute.jsx
│   │   │   ├── styles.css
│   │   │── context/
│   │   │── css/
│   │   │── pages/
│   │   │   ├── DashboardPage.jsx
│   │   │   ├── DevicesPage.jsx
│   │   │   ├── GrafanaDashboard.js
│   │   │   ├── LoginPage.jsx
│   │   │   ├── MonitoringPage.jsx
│   │   │   ├── RegisterPage.jsx
│   │   │   ├── WeatherDashboard.jsx
│   │   │── services/
│   │   │   ├── api.js
│   │   │   ├── authService.js
│   │   │   ├── deviceService.js
│   │   │   ├── monitoringService.js
│   │   │   ├── weatherService.js
│   │   │── App.js
│   │   │── index.js
│   │── .env
│   │── .gitignore
│   │── package-lock.json
│   │── package.json
│   │── README.md


```

## Installation et exécution

### Prérequis

- Python 3.9+
- Docker & Docker Compose
- Kubernetes (MicroK8s ou Minikube)
- PostgreSQL, Redis, MongoDB

### Lancer les services avec Docker Compose

```bash
docker-compose up --build
```

### Déploiement sur Kubernetes

```bash
kubectl apply -f kubernetes/
```

## Auteurs

Projet réalisé ES-SAHLY Hamza.

