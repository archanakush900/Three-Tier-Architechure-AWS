Hello World Three-Tier Application
This repository contains a simple "Hello World" application built using a three-tier architecture. The application demonstrates the fundamental concepts of separating frontend, backend, and database components in a web application.

Architecture Overview
The application follows the classic three-tier architecture:

Frontend Tier (Presentation Layer)

HTML/CSS/JavaScript
Served by NGINX web servers
Handles user interface and interactions
Backend Tier (Application Layer)

PHP API
Processes business logic
Communicates with database
Serves data to frontend
Database Tier (Data Layer)

MySQL database
Stores application data
Provides data persistence
Features
Display messages from the database
Add new messages to the database
Basic responsive design
AWS Infrastructure Components
When deployed on AWS, the infrastructure includes:

Web ALB: Load balancer for distributing traffic to web servers
NGINX Servers: EC2 instances in an auto-scaling group
App ALB: Load balancer for distributing traffic to application servers
PHP Servers: EC2 instances in an auto-scaling group
RDS MySQL: Managed relational database service
Directory Structure
three-tier-architecture-aws/
├── frontend/
│   ├── index.html            # Main HTML file
│   ├── styles.css            # CSS styles
│
├── backend/
│   └── api/                  # API endpoints
│       ├── get_messages.php  # API to retrieve messages
│       ├── save_message.php  # API to save new messages
│       └── db_connection.php # Database connection utility
│
├── database/
│   └── database_setup.sql    # SQL schema and initial data
│
└── infrastructure/           # AWS infrastructure configurations
    ├── frontend_server.md     # Frontend server configurations
    ├── backend_server.md     # Backend server configurations
    ├── nginx_config     # Nginx server configurations
Prerequisites
Web server with PHP support (XAMPP, WAMP, MAMP, etc.)
MySQL database
Steps
Create VPC
Create subnets
Web Public 1a, 1b, 1c
Web Private 1a, 1b, 1c
App Private 1a, 1b, 1c
Db Private 1a, 1b, 1c
Create route tables
Web Public
Web Private 1a, 1b, 1c
App Private 1a, 1b, 1c
Db Private 1a, 1b, 1c
Associate route tables with subnet
Create internet Gateway (IGW)
Attach it to VPC
Create NAT gateway (NATGW) in web public subnet
Add IGW and NAT routes in route table
Public -> IGW
Private -> NAT
Create security groups
Frontend ALB
Frontend Servers
Backend ALB
Backend Servers
Db Private Servers
Create database subnet group
Create database server
Create Frontend ALB
Create Frontend ALB target group
Create Backend ALB
Create Backend ALB target group
Create Frontend Server AMI
Install Nginx
Install Git
Create Backend Server AMI
Install PHP, MySQL, Apache
Install Git
Run the database script
Create the Launch Template for Frontend Server
Create the Launch Template for Backend Server
Create the Auto Scaling Group for Frontend Server
Create the Auto Scaling Group for Backend Server
Development
Frontend Development
The frontend is built with plain HTML, CSS, and JavaScript. It uses the Fetch API to communicate with the backend.

To make changes to the frontend:

Modify the HTML/CSS/JavaScript files in the frontend directory
Test the changes locally
Backend Development
The PHP backend provides simple API endpoints for retrieving and saving messages.

To make changes to the backend:

Modify the PHP files in the backend/api directory
Test the changes locally
Security Considerations
This is a demo application and lacks several security features that would be necessary in a production environment:

Input validation and sanitization
Authentication and authorization
HTTPS encryption
Protection against SQL injection (although PDO with prepared statements is used)
CORS configuration
License
This project is released under the MIT License.

Acknowledgements
This sample application was created as a demonstration of AWS three-tier architecture principles.

