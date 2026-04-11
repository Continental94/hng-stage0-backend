# HNG Stage 0 Backend Task – Name Classification API

## 📌 Overview

This project is a simple backend API built as part of the HNG Internship Stage 0 task.
It integrates with the Genderize API to classify a name by gender and returns a processed response.

---

## 🚀 Live API

Base URL:

```
https://your-app.up.railway.app
```

Example Endpoint:

```
GET /api/classify?name=john
```

Full Example:

```
https://your-app.up.railway.app/api/classify?name=john
```

---

## 🧰 Tech Stack

* Node.js
* Express.js
* Axios
* CORS

---

## ⚙️ Features

* Accepts a name as query parameter
* Calls external API (Genderize.io)
* Processes response data
* Returns structured JSON
* Handles errors and edge cases
* Adds timestamp for each request

---

## 📥 Request

### Endpoint:

```
GET /api/classify
```

### Query Parameter:

| Parameter | Type   | Required | Description      |
| --------- | ------ | -------- | ---------------- |
| name      | string | Yes      | Name to classify |

---

## 📤 Response Format

### ✅ Success (200 OK)

```json
{
  "status": "success",
  "data": {
    "name": "john",
    "gender": "male",
    "probability": 0.99,
    "sample_size": 1234,
    "is_confident": true,
    "processed_at": "2026-04-10T12:00:00.000Z"
  }
}
```

---

### ❌ Error Responses

#### 400 Bad Request

```json
{
  "status": "error",
  "message": "name parameter is required"
}
```

#### 422 Unprocessable Entity

```json
{
  "status": "error",
  "message": "name must be a string"
}
```

#### 404 No Prediction

```json
{
  "status": "error",
  "message": "No prediction available for the provided name"
}
```

#### 500 Server Error

```json
{
  "status": "error",
  "message": "Server or upstream failure"
}
```

---

## 🧠 Logic Implemented

* Renamed `count` → `sample_size`
* Computed `is_confident`:

  * `true` if:

    * probability ≥ 0.7
    * sample_size ≥ 100
* Added `processed_at` timestamp (UTC, ISO 8601)

---

## 🧪 Testing

You can test the API using:

* Browser
* Postman
* cURL

Example:

```
curl https://hng-stage0-backend-production-21ba.up.railway.app/api/classify?name=john
```

---

## 📦 Installation (Local Setup)

```bash
git clone https://github.com/Continental94/hng-stage0-backend.git
cd hng-stage0-backend
npm install
node index.js
```

---

## 📤 Deployment

The API is deployed on Railway and publicly accessible.

---

## 👤 Author

* Name: Onabanjo Ayoola Olamilekan
* Email: onabanjoayoolaolamilekan@gmail.com
* Stack: Node.js (Express)
