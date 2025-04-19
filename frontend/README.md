# 🚀 Gandiva Extended Security Posture Management (xSPM) - Frontend

This is the frontend application for the Gandiva Extended Security Posture Management (xSPM) tool. It provides a modern, responsive user interface for monitoring and managing cloud security posture across multiple cloud platforms and services.

## 🏗️ Architecture

The frontend is built using:
- React with TypeScript
- React Router for navigation
- Axios for API requests
- Tailwind CSS for styling
- Shadcn UI components
- Lucide React for icons
- React Query for data fetching
- React Flow for graph visualization
- Sonner for toast notifications

## 📁 Project Structure

```
frontend/
├── public/              # Static assets
├── src/
│   ├── assets/          # Images, fonts, etc.
│   ├── components/      # Reusable UI components
│   │   ├── ui/          # Shadcn UI components
│   │   └── ...          # Custom components
│   ├── lib/             # Utility functions
│   ├── pages/           # Page components
│   │   ├── Graph.tsx    # Neo4j graph visualization
│   │   ├── Login.tsx    # Authentication page
│   │   ├── SecurityPage.tsx # Security findings
│   │   ├── AssetInventory.tsx # Asset inventory
│   │   └── ...          # Other pages
│   ├── services/        # API and service integrations
│   ├── types/           # TypeScript type definitions
│   ├── App.tsx          # Main application component
│   └── main.tsx         # Application entry point
├── .env                 # Environment variables
├── package.json         # Dependencies and scripts
├── tailwind.config.ts   # Tailwind configuration
└── vite.config.ts       # Vite configuration
```

## 🔑 Key Components

### 📄 Pages

- **Graph**: Neo4j graph visualization of cloud resources and relationships
- **AssetInventory**: Comprehensive view of cloud resources
- **SecurityPage**: Security findings and compliance status
- **SecurityControls**: Security control management
- **NetworkAssets**: Network resource monitoring
- **DockerVulnerability**: Container vulnerability assessment
- **KnownExploitedVulnerabilities**: CVE and exploit tracking
- **DataSecurity**: Data protection assessment
- **IacScanning**: Infrastructure as Code scanning
- **SecretScanning**: Secret detection in repositories
- **KubernetesAssets**: Kubernetes resource inventory
- **KubernetesSecurity**: Kubernetes security posture
- **Neo4jGraph**: Graph visualization interface
- **AdminDashboard**: Admin panel for system management
- **Login**: User authentication

### 🧩 Components

- **TopNavBar**: Main navigation and user controls
- **GraphVisualizer**: Neo4j graph visualization component
- **GraphControls**: Graph interaction controls (zoom, filter, layout)
- **GraphFilter**: Filtering options for graph data
- **SecurityBanner**: Security status banner
- **AdminPanel**: Administrative controls
- **VulnerabilityScanner**: Interface for vulnerability scanning
- **ProtectedRoute**: Authentication wrapper for protected routes
- **LoginForm**: Form component for user authentication

### 🔌 Services

- **authService**: Authentication and token management
- **graphService**: Neo4j graph data fetching
- **assetService**: Cloud asset inventory APIs
- **securityService**: Security findings and controls
- **scanningService**: Vulnerability scanning operations
- **benchmarkService**: Security benchmark assessment

## ✨ Features

- **Interactive Graph Visualization**: Visualize cloud resources and their relationships
- **Asset Inventory**: Comprehensive view of all cloud resources
- **Multi-Cloud Support**: AWS, Kubernetes, and other providers
- **Security Findings**: Detailed security misconfigurations and compliance violations
- **Vulnerability Management**: Track and manage vulnerabilities
- **Compliance Dashboard**: Monitor compliance with security benchmarks
- **Security Controls**: Implement and track security controls
- **User Management**: Role-based access control
- **Dark/Light Mode**: UI theme support
- **Responsive Design**: Works on desktop and mobile devices

## 💻 Development

### 📋 Prerequisites

- Node.js v18 or later
- npm, yarn, or bun

### ⚙️ Setup

1. Clone the repository
2. Navigate to the frontend directory
3. Install dependencies:
   ```
   npm install
   ```
   or with bun:
   ```
   bun install
   ```
4. Create a `.env` file with the following content:
   ```
   VITE_API_URL=http://localhost:5000/api/v1
   ```

### 🚀 Running Locally

```
npm run dev
```
or with bun:
```
bun run dev
```

This will start the development server at http://localhost:3000.

### 📦 Building for Production

```
npm run build
```

This creates a `dist` directory with production-ready files.

## 🔌 API Integration

The frontend communicates with the backend through REST API endpoints. Key endpoint categories include:

- **/auth**: Authentication endpoints (login, refresh, logout)
- **/assets**: Cloud resource inventory
- **/findings**: Security findings and compliance status
- **/benchmark**: Security benchmarks
- **/neo4j**: Graph visualization data
- **/docker**: Container vulnerabilities
- **/kev**: Known exploited vulnerabilities
- **/github-scanner**: GitHub scanning results
- **/kubernetes**: Kubernetes resources and security

API requests are made using Axios, with authentication handled automatically through interceptors that refresh tokens when needed.

## 🔐 Authentication

This application uses JWT token-based authentication:

- Access tokens are used for API request authorization
- Refresh tokens are used to obtain new access tokens when current ones expire
- Protected routes redirect unauthenticated users to the login page
- User information and roles determine available features

See [README-AUTH.md](./README-AUTH.md) for detailed authentication implementation.

## 🐛 Troubleshooting

- **API Connection Issues**: Ensure the backend server is running and the `VITE_API_URL` is correctly set in the `.env` file.
- **Authentication Problems**: Check if tokens are expired, try clearing local storage and logging in again.
- **Graph Visualization Issues**: Verify Neo4j database connection and data availability.
- **Performance Issues**: Large datasets may cause performance challenges, use filters to limit data.
- **Build Errors**: Make sure all dependencies are installed and compatible versions are being used.
