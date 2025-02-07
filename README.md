# Employee Management Full-Stack Application

## Table of Contents

- [Overview](#overview)
- [Key Technologies](#key-technologies)
- [User Interface](#user-interface)
- [File Structure](#file-structure)
- [Backend Setup](#backend-setup)
- [Frontend Setup](#frontend-setup)
- [Detailed Component Instructions](#detailed-component-instructions)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

## Overview

The Employee Management System is a dynamic full-stack application that seamlessly combines cutting-edge and traditional technologies. By integrating a modern **React** frontend with a classic **Spring Boot** backend, this project demonstrates how new and established technologies can harmoniously work together to create a robust and efficient application for managing employee and department data!

## Key Technologies

- **React (Frontend)**: A modern JavaScript library for building user interfaces, providing a responsive and interactive experience.
  - **React Router**: A routing library for React that enables navigation and URL handling in single-page applications.
  - **Chart.js**: A JavaScript library for creating responsive and customizable charts and graphs.
  - **Axios**: A promise-based HTTP client for making API requests.
  - **Tailwind CSS**: A utility-first CSS framework for creating custom designs with minimal CSS.
  - **Redux**: A predictable state container for managing application state.
- **Java Spring Boot (Backend)**: A powerful, established Java framework for building production-ready applications with Java, offering robust backend support and data management.
  - **Spring Data JPA**: A part of the Spring Data project that makes it easy to implement JPA-based repositories.
  - **Spring Boot Actuator**: A set of production-ready features that help monitor and manage the application.
  - **Spring Boot DevTools**: Tools that improve the development experience with automatic restarts and live reload.
  - **Spring Boot Starter Web**: A starter for building web applications, including RESTful, application, and WebSocket services.
  - **Spring Boot Starter Data JPA**: A starter for using Spring Data JPA with Hibernate.
  - **RESTful APIs**: Representational state transfer (REST) APIs for communication between the frontend and backend.
- **MySQL**: A reliable relational database for structured data storage.
- **MongoDB**: A flexible NoSQL database for non-relational data.

## User Interface

The frontend of the Employee Management System provides a user-friendly interface for managing employees and departments. It includes features for viewing, adding, editing, and deleting employees and departments. The app also includes visualizations for employee metrics such as growth over time and distribution by age range.

**Dashboard Page:**

<p align="center" style="cursor: pointer">
  <img src="img/dashboard.png" alt="Dashboard Page" style="border-radius: 10px" width="100%"/>
</p>

**Employee List Page:**

<p align="center" style="cursor: pointer">
  <img src="img/employees-page.png" alt="Employee List Page" style="border-radius: 10px" width="100%"/>
</p>

**Department List Page:**

<p align="center" style="cursor: pointer">
  <img src="img/departments-page.png" alt="Department List Page" style="border-radius: 10px" width="100%"/>
</p>

## File Structure

```
employee-management-app
│
├── backend
│   ├── src
│   │   ├── main
│   │   │   ├── java
│   │   │   │   └── com
│   │   │   │       └── example
│   │   │   │           └── employeemanagement
│   │   │   │               ├── EmployeeManagementApplication.java
│   │   │   │               ├── config
│   │   │   │               │   └── CorsConfig.java
│   │   │   │               │   └── DataInitializer.java
│   │   │   │               ├── controller
│   │   │   │               │   ├── DepartmentController.java
│   │   │   │               │   └── EmployeeController.java
│   │   │   │               ├── model
│   │   │   │               │   ├── Department.java
│   │   │   │               │   └── Employee.java
│   │   │   │               ├── repository
│   │   │   │               │   ├── DepartmentRepository.java
│   │   │   │               │   └── EmployeeRepository.java
│   │   │   │               ├── service
│   │   │   │               │   └── DataInitializer.java
│   │   │   │               └── exception
│   │   │   │                   └── ResourceNotFoundException.java
│   │   │   └── resources
│   │   │       ├── application.properties
│   │   │       └── data.sql
│   └── pom.xml
│   └── compose.yaml
│
└── frontend
    ├── public
    │   ├── index.html
    │   └── favicon.ico
    │   └── manifest.json
    ├── src
    │   ├── components
    │   │   ├── Dashboard.js
    │   │   ├── EmployeeList.js
    │   │   ├── EmployeeForm.js
    │   │   ├── DepartmentList.js
    │   │   ├── DepartmentForm.js
    │   │   └── Navbar.js
    │   ├── services
    │   │   ├── employeeService.js
    │   │   └── departmentService.js
    │   ├── App.js
    │   ├── index.js
    │   ├── index.css
    │   ├── reportWebVitals.js
    │   └── App.css
    └── package.json
```

## Backend Setup

### 1. Clone the Repository

```bash
git clone <repository-url>
cd backend
```

### 2. Install Dependencies

Ensure you have [Maven](https://maven.apache.org/) and [Java JDK](https://www.oracle.com/java/technologies/javase-jdk11-downloads.html) installed. Run the following command to install them:

- For MacOS:
    ```bash
    brew install maven
    ```
- For Windows: Download Maven from [https://maven.apache.org/download.cgi](https://maven.apache.org/download.cgi) and follow the installation instructions.

Next, install the project dependencies:

```bash
mvn install
```

### 3. Configure the Application

Update `src/main/resources/application.properties` with your MySQL and MongoDB configuration:

```properties
# MySQL Configuration
spring.datasource.url=jdbc:mysql://localhost:3306/employee_management
spring.datasource.username=root
spring.datasource.password=password
spring.jpa.hibernate.ddl-auto=update

# MongoDB Configuration
spring.data.mongodb.uri=mongodb://localhost:27017/employee_management
```

Feel free to change the database name, username, and password, and even add more configurations as needed.

### 4. Start the Backend Server

Run the following command to start the Spring Boot application:

```bash
mvn spring-boot:run
```

The backend will be available at [http://localhost:8080](http://localhost:8080).

### 5. Access the API Endpoints

- **Get All Employees:**
  ```bash
  curl -X GET http://localhost:8080/api/employees
  ```

- **Get Employee by ID:**
  ```bash
  curl -X GET http://localhost:8080/api/employees/1
  ```

- **Get All Departments:**
  ```bash
  curl -X GET http://localhost:8080/api/departments
  ```

- **Get Department by ID:**
  ```bash
  curl -X GET http://localhost:8080/api/departments/1
  ```
  
- Feel free to add more API endpoints as needed...

## Frontend Setup

### 1. Clone the Repository

```bash
git clone <repository-url>
cd frontend
```

### 2. Install Dependencies

Ensure you have [Node.js](https://nodejs.org/) and [npm](https://www.npmjs.com/) installed. Run the following command to install the required dependencies:

```bash
npm install
```

### 3. Set Up Environment Variables

Create a `.env` file in the root of your project if it doesn't already exist. Add the following environment variable:

```env
REACT_APP_API_URL=http://localhost:8080/api
```

### 4. Start the Development Server

Run the following command to start the React development server:

```bash
npm start
```

The frontend will be available at [http://localhost:3000](http://localhost:3000).

### 5. Build for Production

To create a production build of your application, run:

```bash
npm run build
```

The build files will be generated in the `build` directory. You can deploy these files to your production server.

### 6. Running Tests

To run tests, use:

```bash
npm test
```

## Detailed Component Instructions

### `Dashboard.js`

Displays various metrics related to employees, such as total employee count, average age, employee growth over time, and distribution by age range. It uses `react-chartjs-2` to render bar charts.

### `EmployeeList.js`

Shows a list of employees with options to search, paginate, and delete entries. Includes a link to add a new employee and edit existing employees.

### `EmployeeForm.js`

Provides a form for adding or editing employee details. Fetches departments to populate the department dropdown. Uses `useParams` to determine if it's in edit mode or add mode.

### `DepartmentList.js`

Displays a list of departments with options to search, paginate, and delete entries. Includes a link to add a new department and edit existing departments.

### `DepartmentForm.js`

Provides a form for adding or editing department details.

### `Navbar.js`

The navigation bar component that includes links to various pages such as Dashboard, Employees, and Departments. Highlights the currently active page.

## Troubleshooting

### Backend Issues

- **`Could not autowire` Errors**: Ensure that all dependencies are correctly defined in the `pom.xml` and that the repository interfaces are located in the correct package structure.

- **`Exception opening socket` for MongoDB**: Verify that MongoDB is running and accessible at `localhost:27017`. Check MongoDB logs for any connection issues.

### Frontend Issues

- **Error: Cannot read properties of undefined (reading 'id')**: Ensure that the `employee` object in `EmployeeForm` is correctly initialized and that the `id` parameter is correctly passed. Check the `getEmployeeById` and `updateEmployee` functions for proper handling of data.

- **Chart Issues**: Ensure `Chart.js` and `react-chartjs-2` are correctly installed and configured. Verify that the chart data passed to components is in the correct format.

## Contributing

If you'd like to contribute to the project, please fork the repository and submit a pull request with your changes. Ensure that you follow the project's coding standards and include relevant tests for new features.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Contact

For any questions or issues, please contact [hoangson091104@gmail.com](mailto:hoangson091104@gmail.com).

---

Thank you for visiting today! ❤️
