# Skip Checkout 

## Overview

The aim of this project is to provide an exemplary solution on how the checkout process can be skipped using cloud-based mobile shopping and payment for stationary retailers. 

After a registration shoppers can scan the barcode of the products they add to their shopping cart with their mobile phone. They can finalize the purcase and leave the store after scanning the QR code at a skip-checkout counter. 
All successful purchases are persisted in a database. The shop owner has access to this data in a dashboard and can manually intervene if a purchase has been marked for a pending bag check due to fraud detection. 

## Built with

- ReactJS
- Spring Boot
- Google Firebase

## Getting started

Clone / fork this [repository](https://github.com/project-mara/skip-checkout).

## Usage

The monorepo consists of two packages:

The React Frontend in /packages/frontend containing the Web-App with a login page, the home page with the skip-checkout functionality and a shop owner dashboard. Users or shop-owners are routed via frontend according to their role.

The Spring Boot Backend in /packages/backend is responsible for authentification and authorization, the payment and detection of possible frauds. It also provides shop owners the possibility to integrate an existing ERP system and synchronize with it.

### Frontend

To start the Frontend (package: frontend) run:

```
- cd packages/frontend
- yarn
- yarn start
```

To start the frontend using docker run:

```
- cd packages/frontend
- docker build . -t skip-checkout_frontend:v0.1
- docker run -p 8000:80 skip-checkout_frontend
```

### Backend

Java Development Kit (JDK) is required.
To start the Backend (package: backend), do the following steps:

```
- cd packages/backend
- windows: powershell ./mvnw spring-boot:run
- macos: bash ./mvnw spring-boot:run
- check via http://localhost:8080/health
```
You can check the RESTful services via Swagger UI at http://localhost:8080/swagger-ui.html#/

## Pipelines

Pushing to packages/frontend triggers two GitHub Actions workflows. One workflow builds and deploys the frontend to Firebase Hosting. It is available on https://project-mara-acn.web.app/

The other workflow builds a production ready docker image of the frontend available in GitHub Packages.

Pushing to packages/backend triggers the backend-workflow. This workflow creates a production ready backend build and deloys it to Google Cloud Run and GitHub Packages.

## Security

Authentification and authorization are implemented with Spring Security using [JSON Web Tokens](https://jwt.io/).

## Contributing

Thank you for your interest in contributing! Get started [here](https://github.com/serbecker/jahresprojekt/blob/main/CONTRIBUTING.md).

## Get help
In case of a bug report, bugfix or a suggestion, please feel free to open an [issue](https://github.com/serbecker/jahresprojekt/issues) in Git.

## License

This project is licensed under the MIT License ![Github License](https://img.shields.io/badge/license-MIT-green)
