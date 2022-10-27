# Metropolitan Convention Center - Client

This repository is 1 of 3 microservices that make up the mock MCC Event Registration Application.
It provides an ReactJS Client for its adjacent HyperSQLDB service - [mcc-data](https://github.com/jaydajayda/mcc-data.git) and authentication service - [mcc-auth](https://github.com/jaydajayda/mcc-auth.git).

## Getting Started

`git clone git@github.com:jaydajayda/mcc-client.git`

`cd mcc-client`

`npm install`

`npm start`

*Note: MCC-Data and MCC-Auth APIs must be running for full client functionality.*

## Getting Started with Docker

**Docker instructions located in the [mcc-data README.md](https://github.com/jaydajayda/mcc-data/blob/main/README.md) and [mcc-auth README.md](https://github.com/jaydajayda/mcc-auth/blob/main/README.md) must be completed PRIOR to completing Docker instructions below.**

**Updating Client Configuration:**

`cd mcc-client/src/setupProxy.js`

* Replace `localhost` with the respective IP Addresses of the Data API (/api) and Authentication API (/account), save the file.

`cd mcc-client/default.conf`

* Modify the proxy IP Addresses of the Data API (/api) and Authentication API (/account) to reflect the correct IP Addresses, save the file.  

**Build Client Image:**

`docker build --tag <IMAGE NAME>:v1.0 .`

**Run Container Using Client Image:**

`docker run --name <CONTAINER NAME> -it -p 3000:80 <IMAGE NAME>:v1.0`
*Running the Client container will occupy the terminal, you'll need to open a new terminal to continue.*

**Add Client Container to Docker Network:**

`docker network connect <NETWORK NAME> <CONTAINER NAME>`

**Locating IP Address of Client:**

`docker network inspect <NETWORK NAME>`