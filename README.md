# Kaiburr_Task1
Task 1. Java backend and REST API example.
# Java Backend REST API - Task Management

This project is a **Spring Boot-based REST API** for managing "Task" objects. Each task represents a shell command that can be executed within a Kubernetes pod. Tasks are stored in a **MongoDB database** and have properties like `id`, `name`, `owner`, `command`, and a list of executions (`taskExecutions`).

## Features
- **Create, Retrieve, Delete, and Search Tasks**
- **Execute a Task's Command and Store Execution History**
- **MongoDB Integration for Persistent Storage**
- **Spring Boot Framework for REST API Development**

## Prerequisites
Ensure the following software is installed on your system:

1. **Java Development Kit (JDK 17+)**  
   Install OpenJDK:
   ```sh
   sudo apt update
   sudo apt install openjdk-17-jdk
   ```
   Verify installation:
   ```sh
   java -version
   ```

2. **Maven (Build Tool)**  
   Install Maven:
   ```sh
   sudo apt install maven
   ```
   Verify installation:
   ```sh
   mvn -version
   ```

3. **MongoDB (Database)**  
   Install MongoDB:
   ```sh
   sudo apt install mongodb
   ```
   Start MongoDB service:
   ```sh
   sudo systemctl start mongod
   ```
   Verify MongoDB is running:
   ```sh
   mongo --eval 'db.runCommand({ connectionStatus: 1 })'
   ```

4. **VS Code (Recommended for Development)**  
   Install [VS Code](https://code.visualstudio.com/).

5. **Spring Boot Extensions in VS Code** (Install from Marketplace)
   - Java Extension Pack
   - Spring Boot Extension Pack
   - MongoDB for VS Code (Optional)

## Project Setup
### Clone the Repository
```sh
git clone https://github.com/Neevan10/Kaiburr_Task1/java-backend-api.git
cd java-backend-api
```

### Project Structure
```
java-backend-api/
│── src/
│   ├── main/
│   │   ├── java/com/example/taskapi/
│   │   │   ├── controllers/TaskController.java
│   │   │   ├── models/Task.java
│   │   │   ├── models/TaskExecution.java
│   │   │   ├── repositories/TaskRepository.java
│   │   │   ├── services/TaskService.java
│   ├── resources/
│   │   ├── application.properties
│── pom.xml
│── README.md
```

### Configure MongoDB Connection
Modify `src/main/resources/application.properties`:
```
spring.data.mongodb.uri=mongodb://localhost:27017/taskdb
server.port=8080
```

### Build and Run the Application
```sh
mvn spring-boot:run
```

## API Endpoints
### 1. **Get All Tasks**
```sh
GET http://localhost:8080/tasks
```
#### cURL Command:
```sh
curl -X GET http://localhost:8080/tasks
```

### 2. **Create a Task**
```sh
PUT http://localhost:8080/tasks
```
#### Example Request Body:
```json
{
    "id": "123",
    "name": "Print Hello",
    "owner": "John Smith",
    "command": "echo Hello World!"
}
```
#### cURL Command:
```sh
curl -X PUT http://localhost:8080/tasks -H "Content-Type: application/json" -d '{
    "id": "123",
    "name": "Print Hello",
    "owner": "John Smith",
    "command": "echo Hello World!"
}'
```

### 3. **Find Task by Name**
```sh
GET http://localhost:8080/tasks/search?name=Print
```
#### cURL Command:
```sh
curl -X GET "http://localhost:8080/tasks/search?name=Print"
```

### 4. **Delete a Task by ID**
```sh
DELETE http://localhost:8080/tasks/123
```
#### cURL Command:
```sh
curl -X DELETE http://localhost:8080/tasks/123
```

## Testing with Postman
- **Import the API collection in Postman**
- **Use the endpoints as described above**

## Additional Notes
- **Security Consideration:** Ensure that shell commands do not allow arbitrary code execution.
- **Further Enhancements:** Implement authentication, Kubernetes integration, and better error handling.

## Contributing
Feel free to fork the repo, raise issues, or submit pull requests.

## License
This project is licensed under the MIT License.

