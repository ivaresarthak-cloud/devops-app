# DevOps CI/CD Project

## CI/CD pipeline using AWS, Jenkins, Docker, Kubernetes

## Tools
AWS EC2, Jenkins 2.541.3, Docker, Kubernetes (Minikube), GitHub

## Pipeline Flow
Github - Jenkins - Docker - DockerHub - Kubernates - Live App

## Steps
1. Created EC2
2. Installed Jenkins
3. Built Docker image
4. Deployed to Kubernetes
5. Automated with Jenkins
   
## Challenges And Solution
1. t2.micro insufficient RAM — Minikube requires minimum 1.8GB RAM, t2.micro only has 1GB. Fixed by upgrading to t3.small
2. Jenkins repo URL wrong — Original guide used old redhat-stable URL. Fixed by using new rpm-stable URL with jenkins.io-2026.key
3. Node.js 18 EOL — Original guide used outdated Node 18. Updated to Node 22 LTS
4. GitHub push rejected — Repo had README causing conflict. Fixed by git pull --allow-unrelated-histories then push
5. Jenkins node offline — Caused by disk space below 1GB threshold. Fixed by docker system prune -af
6. Disk space 84% full — 8GB disk too small. Fixed by increasing EC2 volume to 20GB using AWS Modify Volume
7. Jenkins forgot password — Fixed by disabling security in config.xml temporarily
8. kubectl permission denied in Jenkins — Jenkins user couldn't access Minikube certificates. Fixed by copying kubeconfig and setting chmod 755 on .minikube folder
9. deployment.yaml validation error — Jenkins workspace had corrupted file. Fixed by adding --validate=false flag

## What I Learned
- How CI/CD pipelines work in real world
- Containerizing applications with Docker
- Kubernetes pod management and deployment
- Debugging real infrastructure issues
- AWS EC2 instance management
