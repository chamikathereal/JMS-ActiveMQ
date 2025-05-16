# 🚀 JMS-ActiveMQ

This repository contains two integrated Java projects demonstrating how to use **Java Message Service (JMS)** with **Apache ActiveMQ** to implement reliable asynchronous communication between components using **Topics** and **Queues**.

---

## 📽️ Demo Video
[![JMS ActiveMQ Project Demo](https://github.com/chamikathereal/JMS-ActiveMQ/blob/main/JMS-ActiveMQ.png)](https://youtu.be/pc15pltfXDs)

---

## 📦 Projects Overview

### 1. ActiveMQClient (Java SE)
A simple Java console application that:
- Sends a message to a JMS Topic using ActiveMQ.
- Receives messages from the same Topic in another standalone consumer.
- Uses `org.apache.activemq` library.

📁 Project Structure:
```

ActiveMQClient/
├── src/main/java/lk.ijiat.ee.activemq/
│   ├── MessageSender.java
│   └── MessageReceiver.java
└── pom.xml

```

### 2. JMS-WEB (Java EE / Jakarta EE)
A Jakarta EE web application that:
- Contains a `Message Driven Bean (MDB)` to listen to an ActiveMQ Topic (`activeMqTopic`).
- Has a Servlet (`/home`) that sends multiple messages to a Queue (`MyQueue`) via `QueueSender`.

📁 Project Structure:
```

JMS-WEB/
├── src/main/java/lk.ijiat.ee.jms.web/
│   ├── message/MessageReceiver.java (MDB)
│   └── servlet/Home.java (Servlet)
└── pom.xml

````

---

## 🔗 How the Projects Connect

| Sender                        | Receiver                             | Message Type | Destination    |
|------------------------------|--------------------------------------|--------------|----------------|
| `ActiveMQClient` (Topic: News) | `ActiveMQClient` MessageReceiver     | TextMessage  | `News`         |
| `ActiveMQClient` (Topic: activeMqTopic) | `JMS-WEB` MDB `MessageReceiver`     | TextMessage  | `activeMqTopic` |
| `JMS-WEB` Servlet (`/home`)   | (Queue not shown here)               | TextMessage  | `MyQueue`      |

> Changing the topic name in `MessageSender.java` changes where the message is received.

---

## ✅ Prerequisites

- Java 11+
- Maven 3.x
- Apache ActiveMQ (e.g., version 5.18.6)
- GlassFish or any Jakarta EE 10 compatible server

---

## 🚀 How to Run

### 🔧 Step 1: Start ActiveMQ Broker
Download and run ActiveMQ:
```bash
./activemq start
````

Broker URL: `tcp://localhost:61616`

---

### 📤 Run ActiveMQClient

```bash
# To send a message
Run: MessageSender.java

# To receive a message
Run: MessageReceiver.java
```

---

### 🌐 Deploy JMS-WEB

1. Deploy to GlassFish or another Jakarta EE server.
2. Ensure ActiveMQ RAR adapter is configured properly (`activemq-rar-6.1.6`).
3. Access:

   ```
   http://localhost:8080/jms-web/home
   ```

---

## 🧰 Technologies Used

* Java SE & Jakarta EE 10
* Apache ActiveMQ
* JMS (Java Message Service)
* Maven
* Servlets, MDBs

---

## 📁 Repository Structure

```
JMS-ActiveMQ/
├── ActiveMQClient/
└── JMS-WEB/
```

---

## 📜 License

This project is licensed under the [MIT License](LICENSE).

---

## 🤝 Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

---

## 🧑‍💻 Author

**Chamika Gayashan**  
Undergraduate Software Engineer | Sri Lanka  
Linkedin: [@chamikathereal](https://www.linkedin.com/in/chamikathereal/)

