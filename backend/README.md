# 🚀 Gandiva Extended Security Posture Management (xSPM) - Backend

This is the Flask backend application for the Gandiva Extended Security Posture Management (xSPM) tool. It provides comprehensive API endpoints for the frontend application and integrates with Steampipe for cloud resource scanning, Neo4j for relationship visualization, and various security assessment capabilities.

## 🏗️ Architecture

The backend is built using:
- Flask for the web framework
- Flask-RESTful for RESTful API resources
- Flask-JWT-Extended for JWT authentication
- Neo4j for graph database visualization
- Steampipe for cloud resource scanning and security assessments
- MongoDB for data storage

## 📁 Project Structure

```
backend/
├── app.py                             # Main application entry point
├── config.py                          # Configuration settings
├── models.py                          # Database models
├── resources.py                       # Core API resources and endpoints
├── auth.py                            # Authentication logic
├── neo4j_config.py                    # Neo4j database configuration
├── neo4j_asset_resource.py            # Neo4j asset visualization resources 
├── neo4j_relationship_resource.py     # Neo4j relationship builder resources
├── steampipe_api.py                   # Steampipe API client
├── steampipe_manager.py               # Steampipe process management
├── benchmark_resource.py              # Security benchmark assessment endpoints
├── kubernetes_benchmark_resource.py   # Kubernetes security benchmarks
├── docker_resource.py                 # Docker vulnerability scanning
├── kev_resource.py                    # Known Exploited Vulnerabilities resources
├── correlated_kev_resource.py         # Correlated vulnerability resources
├── database_credentials_resource.py   # Database credential management
├── database_scanner_resource.py       # Database security scanning
├── s3_scanner_resource.py             # S3 bucket security scanning
├── github_credentials_resource.py     # GitHub credential management
├── github_scanner_resource.py         # GitHub repository scanning
├── github_secret_scanner_resource.py  # GitHub secrets scanning 
├── kubernetes_asset_resource.py       # Kubernetes asset inventory
├── sync_script.py                     # Sync script for Steampipe data
├── create_admin.py                    # Script for creating admin user
└── requirements.txt                   # Python dependencies
```

## 🔑 Key Components

### 🛠️ Core Functionality

- **Authentication**: JWT-based authentication with role-based access control
- **Asset Inventory**: Comprehensive inventory of AWS, Kubernetes, and other cloud resources
- **Security Scanning**: Identify misconfigurations and compliance violations across cloud providers
- **Relationship Visualization**: Neo4j-based visualization of resource relationships
- **Compliance Assessments**: Integration with security benchmarks like CIS

### 📦 Resource Types

- **AWS Resources**: EC2, S3, VPC, and other AWS services
- **Kubernetes Resources**: Clusters, nodes, pods, and deployments
- **Docker Images**: Vulnerability scanning for container images
- **Databases**: Security scanning for database services
- **GitHub**: Repository scanning and secret detection

### 🛡️ Security Features

- **Benchmarks**: CIS compliance checks for AWS, Kubernetes, and more
- **Known Exploited Vulnerabilities**: Integration with KEV database
- **Secret Scanning**: Detection of secrets in code repositories
- **Compliance Reporting**: Security findings aggregation and reporting

## 🔌 API Endpoints

### 🔐 Authentication

- **POST /api/v1/auth/register**: Register a new user
- **POST /api/v1/auth/login**: Log in and get JWT tokens
- **POST /api/v1/auth/refresh**: Refresh access token
- **POST /api/v1/auth/logout**: Log out and invalidate tokens

### 👥 Users

- **GET /api/v1/users**: Get list of users (admin only)
- **POST /api/v1/users**: Create a new user (admin only)
- **GET /api/v1/users/me**: Get current user info

### 📦 Assets

- **GET /api/v1/assets/summary**: Get summary of cloud resources
- **GET /api/v1/assets**: Get all assets
- **GET /api/v1/assets/export**: Export assets data
- **GET /api/v1/ec2**: Get EC2 instances
- **GET /api/v1/s3**: Get S3 buckets
- **GET /api/v1/vpc**: Get VPC resources
- **GET /api/v1/kubernetes/assets**: Get Kubernetes resources

### 🔍 Security Findings

- **GET /api/v1/findings**: Get security findings
- **GET /api/v1/benchmark**: Get benchmark findings
- **GET /api/v1/kubernetes-benchmark**: Get Kubernetes benchmark findings
- **GET /api/v1/kev**: Get known exploited vulnerabilities
- **GET /api/v1/correlated-kev**: Get correlated known exploits
- **GET /api/v1/docker/vulnerabilities**: Get Docker image vulnerabilities

### 🕸️ Neo4j Integration

- **POST /api/v1/neo4j/relationships**: Build relationships in Neo4j graph database
- **GET /api/v1/neo4j/relationships**: Get summary of relationships in Neo4j
- **POST /api/v1/neo4j/assets**: Process and store assets in Neo4j
- **GET /api/v1/neo4j/query**: Run custom Cypher queries against Neo4j
- **GET /api/v1/neo4j/docker-vulnerabilities**: Get Docker vulnerabilities in Neo4j
- **GET /api/v1/neo4j/known-exploited-vulnerabilities**: Get KEVs in Neo4j
- **GET /api/v1/neo4j/s3-compliance**: Get S3 compliance data in Neo4j
- **GET /api/v1/neo4j/database-compliance**: Get database compliance in Neo4j

### 🔍 Scanning and Credentials

- **GET /POST /api/v1/database-credentials**: Manage database credentials
- **GET /POST /api/v1/database-scanner**: Run database security scans
- **GET /POST /api/v1/s3-scanner**: Run S3 bucket scans
- **GET /POST /api/v1/github-credentials**: Manage GitHub credentials
- **GET /POST /api/v1/github-scanner**: Run GitHub repository scans
- **GET /POST /api/v1/github-secret-scan**: Run GitHub secret scans

### 🚀 Steampipe

- **POST /api/v1/steampipe/sync**: Trigger a Steampipe sync
- **GET /api/v1/steampipe/status**: Get Steampipe service status
- **POST /api/v1/steampipe/query**: Run custom Steampipe queries

## 💻 Development

### 📋 Prerequisites

- Python 3.8+
- MongoDB database
- Neo4j database
- Steampipe with appropriate plugins (AWS, Kubernetes, etc.)

### ⚙️ Setup

1. Create a virtual environment:
   ```
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

2. Install dependencies:
   ```
   pip install -r requirements.txt
   ```

3. Configure environment variables:
   ```
   # Copy the sample environment file
   cp .env.sample .env
   
   # Generate a secure encryption key
   ./generate_encryption_key.py
   
   # Edit the .env file with your secure credentials
   nano .env
   ```
   
   Make sure to set the following variables in your .env file:
   ```
   SECRET_KEY=your_secure_secret_key
   JWT_SECRET_KEY=your_secure_jwt_secret
   MONGO_URI=mongodb://gandiva-mongo:27017/
   DB_NAME=xspm
   NEO4J_URI=bolt://gandiva-neo4j:7687
   NEO4J_USER=neo4j
   NEO4J_PASSWORD=your_secure_password
   DB_ENCRYPTION_KEY=your_secure_encryption_key  # Use the generated key
   ```
   
   **IMPORTANT: Never commit the .env file to version control. It contains sensitive credentials.**

4. Create an admin user:
   ```
   python create_admin.py
   ```

### 🚀 Running Locally

```
flask run
```

This will start the development server at http://localhost:5000.

## 🔒 Security Considerations

- JWT tokens are used for authentication with appropriate expiration
- Role-based access control for API endpoints
- Secure credential storage for scanning integrations
- Comprehensive logging for security events
- Environment variables for sensitive configuration instead of hardcoded values
- Encryption of sensitive credentials stored in the database

## 🐛 Troubleshooting

### ❌ Common Issues

1. **Database connection errors**:
   - Check MongoDB connection string
   - Verify Neo4j credentials and availability

2. **Steampipe integration issues**:
   - Ensure Steampipe is installed and available
   - Check that required plugins are installed
   - Verify AWS credentials are properly configured

3. **Neo4j connectivity**:
   - Verify Neo4j database is running
   - Check credentials in configuration

4. **Scanning failures**:
   - Check credential validity
   - Verify sufficient permissions for scanning targets
   - Check network connectivity to target systems

### 📝 Logs

Application logs can be found in the console when running in development mode. In production, logs should be configured according to your deployment environment. 