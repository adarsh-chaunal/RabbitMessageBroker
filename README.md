# RabbitMessageBroker
In this project we have implemented RabbitMQ with .NET 8.

# Introduction
RabbitMQ is an open-source message-broker software that originally implemented the Advanced Message Queuing Protocol and has since been extended with a plug-in architecture to support Streaming Text Oriented Messaging Protocol, MQ Telemetry Transport, and other protocols

# History and Version
RabbitMQ was first released in 2007, with version 1.0.0 released on July 1, 2007 and version 2.0.0 released on August 24, 2010. The latest release, 3.12, was released on June 1, 2023. 

# Setup

Run Docker Desktop.

To setup the RabbitMQ server:
```bash
docker run -d --hostname rmq --name rabbit-server -p 8080:15672 -p 5672:5672 rabbitmq:3-management
```

This will create a Docker container that will be running a RabbitMQ server with the management package attached. 8080 will be the external port and 15672 will be the internal port for management services that can be accessed in the browser. PORT 5672 RabbitMQ main port (AMQP) PORT 5671 TLS-encrypted AMQP (if enabled).

Run the RabbitMQ Server in the Docker

To Manage the RabitMQ server go to http://localhost:8080/
You can make use of the default login credentials, Username: guest Password: guest

# Ports

PORT 4369: Erlang makes use of a Port Mapper Daemon (epmd) for resolution of node names in a cluster. Nodes must be able to reach each other and the port mapper daemon for clustering to work.

PORT 35197 set by inet_dist_listen_min/max Firewalls must permit traffic in this range to pass between clustered nodes

RabbitMQ Management console:

PORT 15672 for RabbitMQ version 3.x
PORT 55672 for RabbitMQ pre 3.x
Make sure that the [rabbitmq_management plugin](https://www.rabbitmq.com/management.html#getting-started) is enabled, otherwise you won't be able to access management console on those ports.

PORT 5672 RabbitMQ main port (AMQP)
PORT 5671 TLS-encrypted AMQP (if enabled)
For a cluster of nodes, they must be open to each other on 35197, 4369 and 5672.

For any servers that want to use the message queue, only 5672 (or possibly 5671) is required.