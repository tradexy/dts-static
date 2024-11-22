# Digital Transport Service (DTS)

## Overview
The **Digital Transport Service (DTS)** is a platform designed to streamline the logistics process by connecting businesses with professional drivers for efficient package deliveries. It aims to simplify the process of posting, accepting, and managing transport jobs between companies and drivers. The platform consists of two main components:

1. **Static Site**: This is the public-facing website that provides information about DTS, its services, and how potential users can get involved. It includes basic content such as "About Us", "Services", "Contact", and other business-related information.

2. **Backend Application**: This is the core of the DTS functionality, enabling users to register, log in, and access the platform's features. The backend manages interactions between companies and drivers, such as posting jobs, accepting jobs, and tracking deliveries.

## Project Aims
The primary aim of DTS is to create a seamless connection between companies needing transport services and professional drivers willing to offer those services. The objectives include:
- Providing a simple and efficient delivery service platform.
- Ensuring transparency and security through features such as real-time tracking and secure payments.
- Building a platform that can scale easily, with infrastructure that allows smooth migration between different cloud providers.

The backend is containerized and deployed to AWS EKS but has been developed in a manner that allows easy migration to other managed Kubernetes services, such as Azure AKS or Google GKE.

## Static Site
The **static site** serves as the entry point for new and potential users. It is a simple, informative website providing details about DTS's mission, services, and contact options.

### Why a Static Site?
The static site serves multiple purposes:
- **SEO & Marketing**: A static site is a simple and effective way to create an online presence, which helps in SEO and marketing the platform to potential users.
- **Compliance**: Platforms such as Stripe require a proper business website to ensure credibility.
- **User Awareness**: The static site offers all the essential information, encouraging users to register for the main platform.

The static site is hosted on **Cloudflare Pages**, leveraging Cloudflare's free plan to provide a cost-effective, fast, and secure way to serve static content.

### Technologies Used
- **HTML, CSS, JavaScript**: Core technologies used for building the static pages.
- **Bootstrap**: Used for consistent, responsive styling to ensure a good user experience across different devices.
- **Cloudflare Pages**: Hosting solution for static files, providing free SSL and global distribution for fast page loads.
- **Formspree**: Formspree is used to handle form submissions for contact forms without the need for server-side code.

## Backend Application
The backend application provides the actual functionality that connects companies with drivers. Users can register, post jobs, accept jobs, and track deliveries in real time. The backend is containerized using **Docker** and orchestrated via **Kubernetes**.

### Current Deployment
- The backend is deployed on **AWS EKS (Elastic Kubernetes Service)** and uses services like **AWS RDS** for data persistence.
- The application also utilizes **NGINX Ingress** for routing and **Cloudflare** for SSL/TLS termination.
- All configuration and infrastructure are managed using **Terraform** for Infrastructure as Code (IaC), making the platform highly modular and infrastructure-agnostic.

### Migratability
The application is designed to be infrastructure-agnostic, meaning it can be migrated to different cloud providers, such as Azure AKS, Google GKE, or even on-premises Kubernetes clusters. This flexibility helps prevent vendor lock-in and makes the infrastructure easily scalable.

## Development and Deployment Guide
### Local Development
- **Static Site**: The static pages can be edited locally and previewed using a simple HTTP server. No complex backend setup is needed for development.
- **Backend**: The backend application requires Docker to build and run the services locally. Kubernetes manifests and Helm charts are used to spin up the required services.

### Running the Static Site Locally
1. **Navigate to the static site directory**:
   ```sh
   cd dts-static
   ```
2. **Run a local HTTP server** (e.g., using Python):
   ```sh
   python -m http.server 5500
   ```
3. **Open the static site** in the browser:
   ```
   http://127.0.0.1:5500/
   ```

### Backend Deployment
The backend is managed via **Terraform** for IaC and utilizes Kubernetes for orchestration.
1. **Terraform**: Use Terraform files to deploy the infrastructure needed for the backend.
2. **Docker & Kubernetes**: Build the Docker images, deploy them to Kubernetes, and manage their lifecycle.

## Keeping the Platform Running
### Static Site
- **Cloudflare Pages** is responsible for hosting the static content. Changes can be made to the static files and pushed to the Git repository linked with Cloudflare Pages for automatic redeployment.

### Backend
- **Monitoring**: Use tools like **Prometheus** and **Grafana** or **Datadog** for monitoring and ensuring the availability of the services.
- **Scaling**: Kubernetes auto-scaling can be set up to handle increased loads.
- **Updates**: When making changes to the backend, update the Docker images and redeploy using the Kubernetes manifests. Terraform may be used for infrastructure updates.

## Technologies Overview
- **Frontend (Static Site)**: HTML, CSS, JavaScript, Bootstrap, Cloudflare Pages.
- **Backend**: Python, Flask, Docker, Kubernetes, AWS EKS, AWS RDS, NGINX.
- **Infrastructure as Code**: Terraform.
- **SSL/TLS**: Managed through **Cloudflare** for both static and backend services.
- **Email Handling**: Formspree integrated with the contact form to handle submissions.

## Future Plans
1. **Advanced Features**: Add features such as in-app messaging between companies and drivers.
2. **Improved Tracking**: Integrate more advanced real-time tracking functionalities.
3. **Payment Integration**: Continue refining the Stripe integration to make payments seamless.
4. **Scalability Improvements**: Expand infrastructure using managed Kubernetes services like AKS or GKE.

## Contribution Guidelines
- **Branching Strategy**: Use `feature`, `bugfix`, and `hotfix` branches for respective tasks.
- **Code Reviews**: All code should be peer-reviewed before merging into the `main` branch.
- **Issues**: Report issues via the GitHub repository to keep track of bugs, enhancements, and questions.

## Contact Information
If you have any questions about the platform or wish to contribute, you can reach out via email: [john@jjmh.site](mailto:john@jjmh.site).
