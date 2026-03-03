# 📘Employee Portal CI/CD Pipeline Repository
This repository defines and manages a hybrid CI/CD pipeline for deploying the emp‑portal application across multiple environments (staging and production) on Google Kubernetes Engine (GKE). It integrates Skaffold for manifest orchestration, Cloud Deploy for release management, and Kubernetes manifests for service exposure.

 ## **Key Components**
*  	Skaffold Config ()
*  	Defines profiles for staging and production.
*  	Uses  deployer to apply Kubernetes manifests.
*  	Provides environment‑specific manifest references (, ).
*  	Deployment Manifests
*  	 and .
*  	Specify replicas, container images, labels, and ports.
*  	Ensure pods are labeled consistently ( / ) for Service selectors.
*  	Service Manifests
*  	 and .
*  	Expose the application via GKE LoadBalancer services.
*  	Forward external traffic on port 80 to the correct container port (e.g., 8080 for Flask).
• 	Cloud Deploy Integration
• 	Pipelines defined to manage staged rollouts.
• 	Artifacts stored in GCS buckets ().
• 	Skaffold invoked automatically during release execution.

## Workflow
1. 	Code Commit → triggers Cloud Build.
2. 	Build Step → container image built and pushed to Artifact Registry.
3. 	Cloud Deploy Release → Skaffold applies manifests to target cluster.
4. 	Deployment → pods scheduled in GKE, Services expose external IPs.
5. 	Verification → health checks confirm app availability.

### Purpose
* 	Provides consistent, reproducible deployments across staging and production.
* 	Ensures environment‑specific configuration while reusing shared Skaffold logic.
* 	Integrates with GCP’s Cloud Deploy for controlled rollouts and artifact tracking.
* 	Supports scalable, maintainable CI/CD for containerized applications.

