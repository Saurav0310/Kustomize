# Kubernetes Configuration Management with Kustomize 🛠️

Simplify Kubernetes deployments across environments using **Kustomize**! This repository demonstrates how to manage configurations for different environments (e.g., development, production) without duplicating YAML files. 

---

## 📦 What's Inside?
- **Base configuration**: Common Kubernetes resources (deployment, service).
- **Overlays**: Environment-specific customizations (e.g., production, staging).
- **Kustomize examples**: Ready-to-use patches and generators.

---

## ✨ Features
- **No duplicate YAML files** – Reuse configurations with overlays.
- **Declarative management** – All changes are tracked in YAML.
- **Built into `kubectl`** – No extra tools needed!
- **Git-friendly** – Easy to version control and collaborate.

---

## 📂 Directory Structure
```
my-kustomize-demo/
├── base/ # Base configuration
│ ├── deployment.yaml # Common deployment
│ ├── service.yaml # Common service
│ └── kustomization.yaml # Lists base resources
└── overlays/
├── production/ # Production-specific changes
│ ├── replica-patch.yaml
│ └── kustomization.yaml
└── staging/ # Staging-specific changes
├── label-patch.yaml
└── kustomization.yaml
```
---

## 🚀 Getting Started

### 1. Clone the Repository
```bash
git clone https://github.com/your-username/your-repo.git
cd your-repo
2. Build Configuration for Production
Generate the final YAML for production:
```

kubectl kustomize overlays/production
3. Apply to Your Cluster
Deploy the production configuration directly:

kubectl apply -k overlays/production
🛠️ Customization Guide
Add a New Environment (e.g., Staging)
Create a folder under overlays/staging.

Define patches (e.g., label-patch.yaml):

# label-patch.yaml
```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-app
spec:
  template:
    metadata:
      labels:
        env: staging
```
Update overlays/staging/kustomization.yaml:

Keep bases generic: Avoid environment-specific settings in base/.

Use labels: Add labels like env: production for clarity.

Test before deploying: Always run kubectl kustomize first.

---
## 📚 Resources  
- [Official Kustomize Documentation](https://kubectl.docs.kubernetes.io/guides/introduction/kustomize/)  
- [Kubernetes Configuration Best Practices](https://kubernetes.io/docs/concepts/configuration/overview/) 
---

🤝 Contributing
Found a bug or have an improvement idea? Open an issue or submit a pull request!

⭐ Star this repo if you found it helpful!
🔧 Happy Kustomizing!


---

This README provides clear instructions, code snippets, and structure to help users quickly understand and use Kustomize in your project.
