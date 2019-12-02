## Alten Vehicle Monitor
This is a sample implementation for the problem of monitoring the latest statuses of the customers' vehicles. The source
of the monitoring data is simulated by a faker procedure called by an internal scheduler. The fake data are sent to an
MQTT queue on a message queue broker after generation. There is a configured listener on the same queue that receives 
the data as soon as it is published to the queue. Upon receiving the data it would be saved in the DB. 
GUI gets the vehicles statuses through a RESTful service for the first time and would subscribe to a websocket to get 
the updated data afterwards. Sending updated vehicles data to GUI would be triggered by another internal scheduler. 
The end user has the ability to filter the viewed data by its status or the customer's name.

### Why message queue
The message queue has chosen for the sake of scalability and The MQTT has chosen because it is simple, easy to use and 
mostly used for the IOT projects with low to medium level of channel access security.

### Project Setup 
The backend project is set up using Jhipster 6.1.0 and the frontend is set up using Angular 8 CLI. The project can be 
run with its docker image including all the required services using the composed docker files. Please refer to the
server README.md file for instructions.  

### Backend Technology Stack:
1. Spring Boot
1. Spring Websocket
1. Spring Integration
1. Spring Data
1. JPA
1. H2 DB(for Dev)
1. PostgreSQL DB(for Prod) 
1. Liquibase
1. RabbitMQ(used as the MQTT broker)
1. Docker
