# SOME/IP Protocol (Scalable service-Oriented MiddlewarE over IP)

## Overview
**SOME/IP** is a middleware protocol used in automotive Ethernet communication, mainly within **AUTOSAR systems**.  
It enables communication between automotive ECUs over Ethernet using a **service-oriented architecture (SOA)** model.

---

## SOME/IP Message Structure

Every SOME/IP packet consists of two parts:

| Section | Description |
|----------|-------------|
| **Header** | Contains metadata (who sent it, what type of message it is, how long it is). |
| **Payload** | Contains the actual data (e.g., sensor readings or commands). |

### **Header Fields**

| Field | Size (bytes) | Description |
|--------|---------------|-------------|
| **Message ID** | 4 | Identifies the service and method/event. |
| **Length** | 4 | Total size of the message (header + payload). |
| **Request ID** | 4 | Unique ID to link request and response. |
| **Protocol Version** | 1 | SOME/IP protocol version. |
| **Interface Version** | 1 | Version of the service interface. |
| **Message Type** | 1 | Defines whether it's a Request, Response, or Notification. |
| **Return Code** | 1 | Shows the execution status (e.g., OK, Error). |

---

## Message Types

| Type | Description |
|-------|-------------|
| **REQUEST** | Sent from the client to request a service. |
| **RESPONSE** | Sent from the server as a reply to the request. |
| **NOTIFICATION (EVENT)** | Sent from the server to notify clients of a change. |
| **ERROR** | Sent if there is a failure or invalid operation. |

---

## 🔹 Methods, Events, and Fields

| Concept | Description |
|----------|-------------|
| **Method** | A request/response-based operation (e.g., Get Engine RPM). |
| **Event** | An automatic notification sent by the server when data changes. |
| **Field** | A variable that can be read or written (e.g., volume level). |

---

## SOME/IP-SD (Service Discovery)

**SOME/IP-SD** stands for **Service Discovery**,  
and it’s a critical extension of the SOME/IP protocol used to **announce, find, and manage services dynamically** on the network.

### Purpose
When a vehicle starts up, ECUs don’t initially know which services are available.  
**SOME/IP-SD** allows them to:
- **Announce** the services they provide.  
- **Discover** available services on the network.  
- **Establish communication** automatically between clients and servers.

### 🔹 How It Works
1. **Service Announcement:**  
   The server (service provider) broadcasts its presence using multicast messages.  
   → Example: “I offer Service ID 0x1234 on IP 192.168.0.10, port 30509.”

2. **Service Discovery:**  
   A client listens for these announcements or sends queries to find the services it needs.

3. **Connection Establishment:**  
   Once the client finds the service, it starts regular SOME/IP communication (Request/Response/Event).

---

