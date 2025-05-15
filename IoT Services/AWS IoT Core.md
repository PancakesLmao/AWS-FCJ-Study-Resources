#services #iot

AWS IoT Core is a fully managed cloud service that lets you connect IoT devices to AWS services and other devices securely, reliably, and at scale. It enables bi-directional communication between internet-connected devices (e.g., sensors, microcontrollers) and the cloud.

# Features

| **Feature**                          | **Description**                                                                                                                                            |
| ------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **AWS IoT Device SDK**               | SDKs for C, JavaScript, and Arduino that help devices connect, authenticate, and communicate over MQTT, HTTP, or WebSockets. Open-source and customizable. |
| **Device Advisor**                   | Cloud-based test suite for validating IoT devices during development. Helps ensure secure and reliable connectivity to AWS IoT Core.                       |
| **Device Gateway**                   | Entry point that supports MQTT, WebSockets, and HTTPS. Manages long-lived, low-latency connections.                                                        |
| **Message Broker**                   | A high-throughput, fully managed MQTT broker supporting MQTT 5.0 and scalable to millions of devices.                                                      |
| **CoAP Protocol (via partners)**     | Support for UDP-based CoAP through partner platforms (e.g., 1NCE, Aeris) for low-power, cellular IoT devices.                                              |
| **Authentication & Authorization**   | Supports X.509 certs, SigV4, custom tokens, IAM policies, and fine-grained topic-level access control.                                                     |
| **Registry**                         | Stores device metadata (attributes, capabilities, identities) consistently across all devices.                                                             |
| **Device Shadow**                    | Virtual representation of device state — stores desired and reported state, even when devices are offline.                                                 |
| **Rules Engine**                     | Allows filtering, transformation, and routing of device messages to over 20 AWS services like Lambda, DynamoDB, and S3.                                    |
| **AWS IoT Core for LoRaWAN**         | Lets you connect and manage LoRaWAN devices without deploying your own LNS infrastructure.                                                                 |
| **Device Location**                  | Provides device location data without the need for GPS hardware, supporting location-aware applications.                                                   |
| **AWS IoT Core for Amazon Sidewalk** | Allows onboarding and managing Sidewalk-enabled devices to AWS IoT Core for scalable IoT use cases.                                                        |
# What problem does it solve
IoT Core addresses common IoT challenges:
- Secure device connectivity over the internet
- Scalable data ingestion and real-time processing
- Device state management (online/offline)
- Cloud integration with AWS services (AI, ML, Storage, Databases)
- Reduces time-to-market by handling heavy-lifting infrastructure

# Benefits
- **Scalability**: Handles millions of devices and messages per second.
- **Security**: Fine-grained access control and encryption via mutual TLS.
- **Real-time Data Processing**: Stream data into Lambda, Kinesis, or S3 for processing.
- **Serverless Integration**: No need to manage infrastructure.
- **Offline State Management**: Device Shadow lets apps interact with devices even when they’re offline.
- **Cost-Effective**: Pay only for what you use (no upfront infrastructure cost).

# How to work with IoT Core
### 1. Set up a Thing
- Register a device (called a _Thing_) in the IoT Core console
- Attach a certificate and policy to authenticate it
### 2. Establish Communication
- Use MQTT to publish/subscribe to topics
- Use `iot:Connect`, `iot:Publish`, `iot:Subscribe` policies
### 3. Use the Rules Engine
- Define SQL-like rules for routing data:
    `SELECT temperature, humidity FROM 'sensors/room1'`
- Set actions like sending data to DynamoDB, SNS, or triggering Lambda
### 4. Set up a Thing
- Register a device (called a _Thing_) in the IoT Core console
- Attach a certificate and policy to authenticate it
### 2. Establish Communication
- Use MQTT to publish/subscribe to topics
- Use `iot:Connect`, `iot:Publish`, `iot:Subscribe` policies
### 3. Use the Rules Engine
- Define SQL-like rules for routing data:
    `SELECT temperature, humidity FROM 'sensors/room1'`
- Set actions like sending data to DynamoDB, SNS, or triggering Lambda
### 4. Monitor Devices
- Use AWS IoT Device Defender for audits and metrics
- View logs via **CloudWatch**
- Use AWS IoT Device Defender for audits and metrics
- View logs via CloudWatch
# What need to be keep in mind
- **Security**: Always use mutual TLS for secure comms. Rotate certificates and audit policies.
- **Topic Design**: Use structured MQTT topics (e.g., `building/room1/temperature`)
- **Payload Size**: MQTT messages are typically limited to 128KB
- **Latency**: Minimize device latency by choosing the closest AWS region
- **Offline Handling**: Use Device Shadow if devices may go offline
- **Cost Control**: Use filters and batching in Rules Engine to reduce Lambda invocations
# Cost
AWS IoT Core pricing is **usage-based**, with key components:

| **Service**         | **Pricing (as of 2024)**                                |
| ------------------- | ------------------------------------------------------- |
| **Messaging**       | $1.00 per million messages (each up to 512 bytes)       |
| **Device Shadow**   | $1.25 per million operations                            |
| **Rules Engine**    | $0.15 per million rule evaluations                      |
| **Device Defender** | Starting at $0.10 per device/month for security metrics |
| **Fleet Indexing**  | $0.25 per million indexing operations                   |
