# MS_Lab
# Spring Boot Project with Frontend

## Overview
This README provides step-by-step instructions to execute a Java Spring Boot project with a frontend. The project consists of a backend (Spring Boot) and a frontend (e.g., Angular, React, or any other framework).

---

## Prerequisites
Before starting, ensure you have the following installed:

### **Backend (Spring Boot)**
1. **Java Development Kit (JDK):**
   - Version: 11 or later
   - [Download JDK](https://www.oracle.com/java/technologies/javase-downloads.html)
2. **Maven:**
   - Version: 3.6+.
   - [Download Maven](https://maven.apache.org/download.cgi)
3. **IDE:** (Optional but recommended)
   - IntelliJ IDEA, Eclipse, or VS Code.

### **Frontend**
1. **Node.js and npm:**
   - Version: Node.js 14+.
   - [Download Node.js](https://nodejs.org/)
2. **Frontend Framework CLI:**
   - Angular CLI, React CLI, or similar based on the framework.
3. **IDE/Text Editor:**
   - VS Code, WebStorm, or any preferred editor.

---

## Running the Backend (Spring Boot)

1. **Clone the Repository:**
   ```bash
   git clone <repository-url>
   cd <backend-folder>
   ```

2. **Build the Project:**
   - Run the following Maven command to download dependencies and build the project:
     ```bash
     mvn clean install
     ```

3. **Run the Backend:**
   - Use Maven to start the Spring Boot application:
     ```bash
     mvn spring-boot:run
     ```
   - Alternatively, run the `main()` method in your Spring Boot application class (e.g., `Application.java`) using an IDE.

4. **Verify the Backend:**
   - Open your browser or Postman and navigate to the backend URL:
     ```
     http://localhost:8080
     ```
   - You should see the backend running or the default Spring Boot landing page.

---

## Running the Frontend

1. **Navigate to the Frontend Directory:**
   ```bash
   cd <frontend-folder>
   ```

2. **Install Dependencies:**
   - Install required npm packages:
     ```bash
     npm install
     ```

3. **Run the Frontend:**
   - Start the frontend development server:
     ```bash
     npm start
     ```
   - This will typically start the frontend server at:
     ```
     http://localhost:4200 (Angular)
     http://localhost:3000 (React)
     ```

4. **Verify the Frontend:**
   - Open your browser and navigate to the frontend URL (e.g., `http://localhost:4200`).
   - Ensure the frontend is successfully fetching data from the backend.

---

## Configuring Frontend and Backend Integration
1. **API Endpoint Configuration:**
   - Update the frontend's environment configuration file (e.g., `environment.ts` for Angular or `.env` for React) to point to the backend API URL:
     ```json
     API_URL: "http://localhost:8080/api"
     ```

2. **CORS (Cross-Origin Resource Sharing):**
   - Ensure the Spring Boot backend allows requests from the frontend.
   - Add the following configuration to a `@Configuration` class:
     ```java
     import org.springframework.context.annotation.Bean;
     import org.springframework.context.annotation.Configuration;
     import org.springframework.web.servlet.config.annotation.CorsRegistry;
     import org.springframework.web.servlet.config.annotation.WebMvcConfigurer;

     @Configuration
     public class CorsConfig {
         @Bean
         public WebMvcConfigurer corsConfigurer() {
             return new WebMvcConfigurer() {
                 @Override
                 public void addCorsMappings(CorsRegistry registry) {
                     registry.addMapping("/**").allowedOrigins("http://localhost:4200");
                 }
             };
         }
     }
     ```

---

## Additional Notes
1. **Build and Package (Optional):**
   - To package the backend and frontend for deployment:
     - Build the frontend:
       ```bash
       npm run build
       ```
       This creates a `dist` folder containing static files.
     - Copy the `dist` folder into the backend's `src/main/resources/static` directory.
     - Rebuild the Spring Boot project.

2. **Access the Application After Deployment:**
   - Once deployed, the backend will serve the frontend on the same port (e.g., `http://localhost:8080`).

---

## Troubleshooting
1. **Port Conflicts:**
   - If the backend or frontend port is already in use, update the port:
     - Backend: Update `application.properties`:
       ```properties
       server.port=8081
       ```
     - Frontend: Update the frontend development server port (e.g., in `angular.json` or `package.json`).

2. **Dependency Issues:**
   - If dependencies fail to download, ensure you have internet access and the correct versions of Node.js, npm, JDK, and Maven.

---

Congratulations! You have successfully executed a Spring Boot project with a frontend. Let me know if you need further assistance.

