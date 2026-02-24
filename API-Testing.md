

# Software
- means the set of programs, instructions, and data that tell a computer what to do and how to perform tasks.

### Main types of software:
- System software – Runs and manages the computer itself (e.g., operating systems).
- Application software – Programs used by people to do tasks (e.g., Excel, Photoshop).

---

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

---

# 🔑 REST API
- A REST API (Representational State Transfer API) is a way to design web services so that different systems can communicate using HTTP in a simple, scalable, and predictable way.

## 🧱 1️⃣ Core Principles of REST API
- ✅ 1. Client–Server Separation
- ✅ 2. Statelessness
- ✅ 3. Resource-Based Design
- ✅ 4. Uniform Interface (Same HTTP verbs, Same response formats)
- ✅ 5. Layered System (Clients don’t know if they talk directly to server or through: API gateway, Proxy, Load balancer)

## 🔄 2️⃣ HTTP Methods in REST (Deep Explanation)

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

# 🧼 SOAP API
- SOAP (Simple Object Access Protocol) is a strict, XML-based protocol used for exchanging structured information between systems over a network.
















