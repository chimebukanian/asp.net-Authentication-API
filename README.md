# **AuthAPI – ASP.NET Core 8 Authentication & JWT API**  

A simple **user authentication API** built with **ASP.NET Core 8**, **Entity Framework Core**, and **JWT (JSON Web Tokens)** for secure authentication. This API allows user **registration, login, and access to protected routes** using JWT authentication.  

## **Features**  
✅ User Registration (stores user info securely)  
✅ User Login (returns JWT for authentication)  
✅ Protected Endpoint (`/api/user/profile`) – Requires JWT  
✅ Password Hashing (using **BCrypt**)  
✅ Uses **Entity Framework Core + SQLite**  

---

## **📌 Technologies Used**  
- **.NET 8**  
- **ASP.NET Core Web API**  
- **Entity Framework Core** (SQLite)  
- **JWT Authentication**  
- **BCrypt.Net** (for password hashing)  
- **Swagger UI** (for API testing)  

---

## **🚀 Getting Started**  

### **1. Prerequisites**  
Make sure you have the following installed:  
- [.NET 8 SDK](https://dotnet.microsoft.com/en-us/download/dotnet/8.0)  
- Visual Studio Code (or any C# IDE)  

### **2. Clone the Repository**  
```sh
git clone https://github.com/yourusername/AuthAPI.git
cd AuthAPI
### **3. Install Dependencies**  
```
dotnet restore
```

### **4. Apply Migrations & Create Database**  
``` 
dotnet ef migrations add InitialCreate
dotnet ef database update
```

### **5. Run the API**  
```
dotnet run
```
The API will be available at:  
- **Swagger UI** → `http://localhost:5000/swagger`  
- **Base API URL** → `http://localhost:5000/api`  

## **📌 API Endpoints**  

### **1. Register a User**  
- **Endpoint:** `POST /api/auth/register`  
- **Request Body (JSON):**  
    ```json
    {
        "username": "john_doe",
        "passwordHash": "password123"
    }
    ```
- **Response:**  
    ```json
    {
        "message": "User registered successfully"
    }
    ```

### **2. User Login**  
- **Endpoint:** `POST /api/auth/login`  
- **Request Body (JSON):**  
    ```json
    {
        "username": "john_doe",
        "passwordHash": "password123"
    }
    ```
- **Response (JWT Token):**  
    ```json
    {
        "token": "eyJhbGciOiJIUzI1NiIsInR..."
    }
    ```

### **3. Get User Profile (Protected)**  
- **Endpoint:** `GET /api/user/profile`  
- **Headers:**  
    ```yaml
    Authorization: Bearer YOUR_JWT_TOKEN
    ```
- **Response:**  
    ```json
    {
        "message": "Welcome john_doe, this is your profile!"
    }
    ```
- ⛔ **If token is missing or invalid, the API returns:**  
    ```json
    {
        "message": "Unauthorized"
    }
    ```

## **📌 Environment Variables (Optional)**  
To store your JWT secret key securely, create an `appsettings.json` file and add:  
```json
{
    "Jwt": {
        "Key": "SuperSecretKey123456!"
    }
}
```

## **🛠 How to Extend the Project**  
🚀 Here are some ways to improve this project:  
- Add Role-Based Authorization (Admin/User roles)  
- Integrate Refresh Tokens  
- Use PostgreSQL or SQL Server instead of SQLite  
- Deploy to AWS/GCP/Azure  

## **📜 License**  
This project is MIT Licensed – Feel free to use and modify it!  

## **📞 Need Help?**  
For issues or improvements, open an issue on GitHub.  

