# 🚀 Restful Booker API Automation Framework

> **Industry-style API Automation Testing Framework** built with **Postman, Newman, JavaScript, CSV Data-Driven Testing, JSON Schema Validation & GitHub Actions CI/CD**.

![Postman](https://img.shields.io/badge/Postman-API%20Testing-FF6C37?logo=postman\&logoColor=white)
![Newman](https://img.shields.io/badge/Newman-Automation-0A7B83)
![JavaScript](https://img.shields.io/badge/JavaScript-ES6-F7DF1E?logo=javascript\&logoColor=black)
![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-CI%2FCD-2088FF?logo=githubactions\&logoColor=white)
![Status](https://img.shields.io/badge/Tests-Passing-brightgreen)

---

## 📌 Project Overview

This project demonstrates an **end-to-end REST API Automation Framework** following industry practices.

It covers:

* ✅ CRUD API Testing
* ✅ Authentication
* ✅ Environment Variables
* ✅ API Chaining
* ✅ Positive & Negative Testing
* ✅ CSV Data-Driven Testing
* ✅ Pre-request Script
* ✅ JSON Schema Validation
* ✅ Newman HTML Reporting
* ✅ GitHub Actions CI/CD

---

## 🛠 Tech Stack

| Tool                    | Purpose                   |
| ----------------------- | ------------------------- |
| **Postman**             | API Development & Testing |
| **Newman**              | Command Line Automation   |
| **JavaScript**          | Test Scripts              |
| **CSV**                 | Data-Driven Testing       |
| **JSON Schema**         | Response Validation       |
| **GitHub Actions**      | Continuous Integration    |
| **HTML Extra Reporter** | Test Report               |

---

## 📂 Project Structure

```text
restful-booker-api/
│
├── .github/
│   └── workflows/
│       └── api-test.yml
│
├── Restful Booker API Framework Copy.postman_collection.json
├── QA.postman_environment.json
├── booking-data.csv
└── README.md
```

---

## 🔄 API Test Flow

```text
Health Check
      │
      ▼
Authentication
      │
      ▼
Create Booking
      │
      ▼
Save Booking ID
      │
      ▼
Get Booking
      │
      ▼
Update Booking
      │
      ▼
Delete Booking
      │
      ▼
Negative Tests
```

---

## ✅ Test Coverage

### Positive Scenarios

* Health Check
* Generate Authentication Token
* Create Booking
* Get Booking
* Update Booking
* Delete Booking

### Negative Scenarios

* Invalid Booking ID → **404**
* Update Without Token → **403**

---

## 🌍 Environment Variables

| Variable    | Description              |
| ----------- | ------------------------ |
| `base_url`  | API Base URL             |
| `token`     | Authentication Token     |
| `bookingid` | Dynamic Booking ID       |
| `firstname` | Generated Before Request |
| `lastname`  | Generated Before Request |

---

## 📊 Data-Driven Testing

The framework uses **CSV** to execute the same collection with multiple datasets.

### booking-data.csv

```csv
firstname,lastname,totalprice,depositpaid,additionalneeds
Shafiur,Rahman,5000,true,Breakfast
Karim,Hasan,7000,false,Lunch
Nayeem,Islam,6500,true,Dinner
```

### Execution

| Iteration | Customer |
| --------- | -------- |
| 1         | Shafiur  |
| 2         | Karim    |
| 3         | Nayeem   |

---

## ⚡ Pre-request Script

Dynamic data is generated before sending the Create Booking request.

```javascript
const id = Math.floor(Math.random() * 10000);

pm.environment.set("firstname", `User${id}`);
pm.environment.set("lastname", "Rahman");
```

**Example Output**

| Run | Generated Name |
| --- | -------------- |
| 1   | User4821       |
| 2   | User1930       |
| 3   | User7755       |

---

## 🔗 API Chaining

The booking ID returned from **Create Booking** is automatically reused by subsequent requests.

```javascript
const response = pm.response.json();
pm.environment.set("bookingid", response.bookingid);
```

This enables:

* Create → Get
* Get → Update
* Update → Delete

without manually changing IDs.

---

## 🧩 JSON Schema Validation

Response structure is validated to ensure backend changes do not break consumers.

```javascript
pm.test("Response matches JSON Schema", () => {
    pm.expect(tv4.validate(pm.response.json(), schema)).to.be.true;
});
```

### Validated Fields

* `bookingid`
* `firstname`
* `lastname`
* `totalprice`
* `depositpaid`
* `bookingdates`
* `additionalneeds`

---

## ▶️ Run Locally

### Install Newman

```bash
sudo npm install -g newman newman-reporter-htmlextra
```

### Execute Collection

```bash
newman run "Restful Booker API Framework Copy.postman_collection.json" \
-e "QA.postman_environment.json" \
-d "booking-data.csv" \
-r cli,htmlextra \
--reporter-htmlextra-export newman-report.html
```

---

## 📈 Test Results

| Metric              | Result |
| ------------------- | -----: |
| Iterations          |  **3** |
| Requests            | **24** |
| Test Scripts        | **24** |
| Pre-request Scripts |  **3** |
| Assertions          | **36** |
| Failed Tests        |  **0** |

---

## 🤖 GitHub Actions CI/CD

Every **git push** automatically triggers the API regression suite.

### Workflow

```yaml
on:
  push:
    branches: [main]
  workflow_dispatch:
```

### CI Pipeline

```text
Git Push
    │
    ▼
GitHub Actions
    │
    ▼
Install Newman
    │
    ▼
Run Collection
    │
    ▼
Generate HTML Report
    │
    ▼
Upload Artifact
```

---

## 📄 HTML Report

The automated report includes:

* Total Requests
* Assertions
* Pass / Fail Summary
* Response Time
* Request & Response Details
* Execution Statistics

---

## 💡 Skills Demonstrated

* REST API Testing
* API Automation Framework Design
* JavaScript Test Scripting
* Environment Variable Management
* API Chaining
* CSV Data-Driven Testing
* JSON Schema Validation
* Newman CLI
* HTML Reporting
* GitHub Actions CI/CD

---

## 👨‍💻 Author

**Md. Shafiur Rahman**

* GitHub: https://github.com/MdShafiurRahman0
* LinkedIn: https://www.linkedin.com/in/mdshafiur/

---

> ⭐ If you found this project useful, consider giving the repository a **Star**.
