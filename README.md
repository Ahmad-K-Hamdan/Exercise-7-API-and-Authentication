# 🔐 Exercise 7 – API and Authentication

A minimal **ASP.NET Core Web API** project that demonstrates **JWT (JSON Web Token)** authentication.  
This exercise focuses on secure API design — including token generation, validation, and protecting endpoints with authorization middleware.

---

## 🚀 Overview
This project provides a simple example of using **JWT authentication** in ASP.NET Core 9 Minimal APIs.  
Users can request a token using their username and email, then use that token to access protected endpoints.

The project also includes integrated **Swagger UI authentication**, allowing you to test endpoints directly in your browser.

---

## 🗂️ Project Files

| File | Description |
|------|--------------|
| **Program.cs** | Configures the web app, adds JWT authentication, authorization, and Swagger. |
| **JwtTokenGenerator.cs** | Handles creation and validation of JWT tokens using `SymmetricSecurityKey` and HMAC SHA256. |
| **TokenRequest.cs** | Defines the model for token requests (username and email). |
| **appsettings.json** | Stores JWT configuration (key, issuer, audience) and app settings. |
| **appsettings.Development.json** | Development environment configuration file. |

---

## ⚙️ How It Works

### 🔑 1. Token Generation
Send a **POST** request to `/tokens` with the following JSON body:
```json
{
  "username": "ahmad",
  "email": "ahmad@example.com"
}
```

The API will return a JWT token:
```json
{
  "token": "<your_generated_token_here>"
}
```

---

### 🧾 2. Access Protected Routes
Use the token in your **Authorization** header as:
```
Bearer <your_generated_token_here>
```

Then call:
```
GET /messages
```

✅ You’ll receive the message `"Hello there"` if authorized.  
🚫 If the token is missing or invalid, you’ll get `401 Unauthorized`.

---

## 🧩 Features
- ✅ Minimal API design using ASP.NET Core 9  
- ✅ JWT authentication and validation  
- ✅ Configurable issuer, audience, and secret key  
- ✅ Integrated Swagger UI with JWT support  
- ✅ Simple, extensible structure for learning and experimentation  

---

## 🧠 Technologies Used
- **.NET 9 / ASP.NET Core**
- **C#**
- **JWT (JSON Web Token)**
- **Swagger / OpenAPI**
- **Dependency Injection**

---

## 🧰 Setup Instructions

1. Clone the repository:
   ```bash
   git clone https://github.com/<your-username>/Exercise-7-API-and-Authentication.git
   cd Exercise-7-API-and-Authentication
   ```

2. Open the project in **Visual Studio** or **VS Code**.

3. Restore dependencies and run:
   ```bash
   dotnet restore
   dotnet run
   ```

4. Open your browser at:
   ```
   https://localhost:7227/swagger
   ```

5. Use the `/tokens` endpoint to get a JWT, then test the protected `/messages` route by authorizing through Swagger’s “Authorize” button.

---

## 🔧 Configuration

Update your `appsettings.json` file with your own secret key:
```json
"Jwt": {
  "Key": "your_secret_key_here",
  "Issuer": "https://localhost:7227",
  "Audience": "https://localhost:7227"
}
```

💡 *Keep your JWT key private and never commit it to public repositories.*
