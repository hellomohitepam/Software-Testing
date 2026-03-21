

# Software
- means the set of programs, instructions, and data that tell a computer what to do and how to perform tasks.

### Main types of software:
- System software – Runs and manages the computer itself (e.g., operating systems).
- Application software – Programs used by people to do tasks (e.g., Excel, Photoshop).

---
```
# 🔌 What is an API (Application Programming Interface)?
- An API is a set of rules and tools that allows different software programs to communicate with each other in a structured way.
- Instead of building everything from scratch, developers use APIs to request data or services from another system.

## 🌐 Types of APIs
### 1️⃣ Web APIs 
> Used over the internet using HTTP/HTTPS.
- REST APIs
- GraphQL APIs
- SOAP APIs

### 2️⃣ Library APIs 
> Functions provided by programming libraries.

### 3️⃣ Operating System APIs 
> Allow apps to use system features (files, camera, notifications).

## ✅ Rules = HOW to communicate
- Request Format (HTTP method, URL/endpoint to call, headers, data format(JSON, XML))
- Authentication (Header, Bearer Token, OAuth login flow)
- Rate Limit (100 requests per minute)
- Response structure (Status codes, Response structure(JSON, XML), Error messages)

## 🧰 Tools = WHAT helps communication
- SDKs (Many APIs provide ready-made code packages. {Swagger / OpenAPI})
- Documentation (APIs include docs that explain rules.)
- Testing tools (Developers use tools to send API requests manually. {Postman, curl})
- Gateways & Middleware (API Gateway for controls traffic, Load balancer for distributes requests)
```
---

# 🔑 REST API
- A REST API (Representational State Transfer API) is a way to design web services so that different systems can communicate using HTTP in a simple, scalable, and predictable way.

## 🧱 1️⃣ Core Principles of REST API
- ✅ 1. Client–Server Separation {res can be html(if web broswer only) or json }
- ✅ 2. Statelessness
- ✅ 3. Resource-Based Design
- ✅ 4. Uniform Interface (Same HTTP verbs, Same response formats)
- ✅ 5. Layered System (Clients don’t know if they talk directly to server or through: API gateway, Proxy, Load balancer)

## 🔄 2️⃣ HTTP Methods in REST

| Method | Action         | Example    |
| ------ | -------------- | ---------- |
| GET    | Read data      | `/users`   |
| POST   | Create         | `/users`   |
| PUT    | Replace        | `/users/1` |
| PATCH  | Partial update | `/users/1` |
| DELETE | Remove         | `/users/1` |

## 🧩 3️⃣ REST API URL Structure (Best Practices)
`https://api.example.com/v1/users/10/products?category=phone&sort=price`
### Breakdown:
- Base URL → api.example.com
- Version → /v1
- Resource → /users
- Resource ID → /10
- Sub-resource → /products
- Query params → ?category=phone&sort=price

## 📦 4️⃣ Request Structure
- Headers - Metadata about request.
- Body - Used in POST/PUT/PATCH.
- Path Params `/users/10` vs Query Params `/users?role=admin`

## 📤 5️⃣ Response Structure
> Good REST APIs return structured responses: JSON
### Status Codes
| Code | Meaning      |
| ---- | ------------ |
| 200  | Success      |
| 201  | Created      |
| 400  | Bad Request  |
| 401  | Unauthorized |
| 403  | Forbidden    |
| 404  | Not Found    |
| 500  | Server Error |

## 🔐 6️⃣ Authentication in REST APIs
- Bearer Token (JWT)
- OAuth2 Used by: Google login, GitHub login through API integration

## ⚡ 7️⃣ REST API Performance & Scaling
- Pagination `/users?page=2&limit=20`
- Filtering `/orders?status=paid`
- Sorting `/products?sort=price_desc`

---

# 🧼 SOAP API
- SOAP (Simple Object Access Protocol) is a to design strict web service, XML-based protocol used for exchanging structured information between systems over a network.

## 🧱 1️⃣ SOAP Core Concepts
- ✅ XML-Based Messaging
- ✅ REST is a style but SOAP is an actual protocol with defined standards: Message format, Security rules, Error handling, Service contracts
- ✅ Platform Independent (SOAP works with: HTTP, SMTP, TCP, JMS. But REST mainly uses HTTP.)

## 📦 2️⃣ SOAP Message Structure
### A SOAP message has 4 main parts:
- 📨 Envelope (Mandatory)
```
<Envelope>
</Envelope>
```

- 🔐 Header (Optional)
> Contains metadata: Authentication, Tokens, Routing info
```
<Header>
  <AuthToken>XYZ</AuthToken>
</Header>
```

- 📄 Body (Mandatory)
> Actual request or response data.

```
<Body>
  <GetOrder>
    <id>100</id>
  </GetOrder>
</Body>
```

- ⚠️ Fault (Error Handling)
```
<Fault>
  <faultcode>Client</faultcode>
  <faultstring>Invalid Request</faultstring>
</Fault>
```

## 📜 3️⃣ WSDL — The Brain of SOAP
- WSDL (Web Services Description Language) is an XML file describing:
1. Available methods
2. Request format
3. Response format
4. Endpoint URL
> 👉 Think of WSDL as a contract between client and server.
```
<operation name="GetUser">
</operation>
```

## 🔐 4️⃣ SOAP Security (Why Enterprises Use It)
> SOAP has built-in enterprise security standards: WS-Security
### Supports:
- XML Encryption
- XML Signature
- Security tokens
- Message integrity
> This is more advanced than typical REST token auth.

## ⚙️ 5️⃣ SOAP vs REST

| Feature        | SOAP                 | REST               |
| -------------- | -------------------- | ------------------ |
| Type           | Protocol             | Architecture style |
| Data format    | XML only             | JSON/XML/etc       |
| Strictness     | Very strict          | Flexible           |
| Speed          | Slower (heavy XML)   | Faster             |
| Security       | Built-in WS-Security | External auth      |
| Contract       | WSDL                 | OpenAPI optional   |
| Enterprise use | High                 | High (modern)      |

## 🔄 6️⃣ SOAP Communication Flow

- SOAP is an application communication protocol used for sending and receiving messages
- SOAP is platform independent

### A SOAP message is an ordinary XML document containing the following elements:
- An Envelope element that identifies the XML document as a SOAP message
- Header element that contains header information
- A Body element that contains call and response information
- A Fault element containing errors and status information
> All the elements above are declared in the default namespace for the SOAP envelop

```
<?xml version="1.0"?>

<soap:Envelope
xmlns:soap="http://www.w3.org/2003/05/soap-envelope"
soap:encodingStyle="http://www.w3.org/2003/05/soap-encoding">

<soap:Header>
...
</soap:Header>

<soap:Body>
...
  <soap:Fault>
  ...
  </soap:Fault>
</soap:Body>

</soap:Envelope>
```

## 🧱 1️⃣ SOAP Core Concepts
- ✅ XML-Based Messaging
- ✅ REST is a style — but SOAP is an actual protocol with defined standards:
1. Message format
2. Security rules
3. Error handling
4. Service contracts
- ✅ Platform Independent

## 📦 2️⃣ SOAP Message Structure
> A SOAP message has 4 main parts:
- 📨 Envelope (Mandatory)
- 🔐 Header (Optional) - Contains metadata: Authentication, Tokens, Routing info
- 📄 Body (Mandatory) - Actual request or response data.
- ⚠️ Fault (Error Handling) 

## 📜 3️⃣ WSDL — The Brain of SOAP
### WSDL (Web Services Description Language) is an XML file describing:
- Available methods
- Request format
- Response format
- Endpoint URL
> 👉 Think of WSDL as a contract between client and server.

## 🔐 4️⃣ SOAP Security
> SOAP has built-in enterprise security standards: WS-Security
> Supports:
> XML Encryption
> XML Signature
> Security tokens
> Message integrity

## ⚙️ 5️⃣ SOAP vs REST
| Feature        | SOAP                 | REST               |
| -------------- | -------------------- | ------------------ |
| Type           | Protocol             | Architecture style |
| Data format    | XML only             | JSON/XML/etc       |
| Strictness     | Very strict          | Flexible           |
| Speed          | Slower (heavy XML)   | Faster             |
| Security       | Built-in WS-Security | External auth      |
| Contract       | WSDL                 | OpenAPI optional   |
| Enterprise use | High                 | High (modern)      |

## 🔄 6️⃣ SOAP Communication Flow
### Step-by-step:
- Client reads WSDL
- Client builds XML SOAP request
- Sends via HTTP POST
- Server processes request
- Server returns SOAP XML response

## 🧩 7️⃣ Example SOAP Request & Response
```
// Req
<soap:Envelope>
  <soap:Body>
    <AddNumbers>
      <a>5</a>
      <b>10</b>
    </AddNumbers>
  </soap:Body>
</soap:Envelope>
```
```
// res
<soap:Envelope>
  <soap:Body>
    <AddNumbersResponse>
      <result>15</result>
    </AddNumbersResponse>
  </soap:Body>
</soap:Envelope>
```
## 🏗️ 8️⃣ When SOAP is Used Today
### Even though REST is popular, SOAP is still used in:
- ✅ Banking systems
-  Airline booking systems
- ✅ Legacy corporate APIs













