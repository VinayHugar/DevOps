## Software Development Methodologies and Architecture Overview

### Waterfall Methodology (Model)
- Requirement > Design > Implementation > Verification > Maintenance

### Agile Methodology (Model)
- **Sprint One**
  - Plan > Design > Develop > Test
    
- **Sprint Two**
  - Plan > Design > Develop > Test 
    
- **Sprint ∞**
  - Plan > Design > Develop > Test

### Scrum Methodology (Model)
1. Smaller team
2. Need to hire experienced people
3. More expensive

### SDLC (Software Development Life Cycle)
1. **Development Team**
   - Plan, Code, Build, Test, Release
2. **Operational Team**
   - Deploy, Operate, Monitor

### DevOps (2008)
- Plan > Code > Build > Test > Release > Deploy > Operate > Monitor
<img src="https://github.com/VinayHugar/DevOps/blob/master/assets/DevOps.png" width="500" height="300">

### Tools & Services in DevOps
1. **Git**: Source Code Management Tool
2. **Maven**: Build Tool
3. **Jenkins**: Continuous Integration Tool
4. **Ansible**: Configuration Management Tool
5. **Docker**: Containerization Tool
6. **Kubernetes**: Container Orchestration Tool
7. **Nagios**: Monitoring Tool
8. **Terraform**: Infrastructure Creation Tool
9. **Nexus**: Artifact Repository
10. **SonarQube**: Code Quality Check Tool

### AWS Services
1. EC2
2. S3
3. VPC
4. IAM
5. RDS
6. CI/CD
7. SNS
8. SQS
9. EBS
10. Elastic Load Balancer
11. Auto Scaling Group

### Software Architecture
1. **Presentation Layer**
   - **Purpose**: This layer is responsible for displaying the user interface and handling user interactions. It communicates with the application layer to send and retrieve data.
   - **Technologies**: HTML, CSS, JavaScript, React, Angular, Vue.js, Swift (iOS), Kotlin (Android).

2. **Application Layer**  
   - **Purpose**: This layer handles the core functionality and business logic of the application. It processes inputs from the presentation layer and interacts with the database layer.
   - **Technologies**: PHP, Node.js, Java, .NET, Python (Django, Flask), Ruby on Rails.

3. **Database Layer**
   - **Purpose**: This layer is responsible for storing and retrieving data. It ensures data persistence and provides an interface for data manipulation.
   - **Technologies**: MySQL, PostgreSQL, MongoDB, Oracle, SQL Server.

### Architecture Types
- **1-Tier Architecture**: Example: A desktop application like Microsoft Access, where the user interface, business logic, and database are all contained within the same program.
  
- **2-Tier Architecture**: Example: A client-server application where a desktop client interacts directly with a database server. For example, a desktop application using MySQL for data storage.
  
- **3-Tier Architecture**: Example: A web application with a front-end built with Angular (Presentation Layer), a back-end server using Node.js (Application Layer), and a PostgreSQL database (Database Layer).
  
- **N-Tier Architecture (More Than One Server Application)**: Example: A complex enterprise application with multiple layers including Client Layer, Presentation Layer, Application Layer, Business Logic Layer, Data Access Layer, Database Layer, Caching Layer, and Load Balancing Layer.

### Architectural Styles
1. **Monolithic Architecture**: Example: An e-commerce website where the user interface, order processing, inventory management, and payment processing are all built into a single Java application deployed on a single server.

2. **Microservices Architecture**: Example: Modern online travel booking system with separate user, booking, payment, and notification services.
