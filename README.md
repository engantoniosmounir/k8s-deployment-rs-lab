# Kubernetes Deployment & ReplicaSet Lab

This lab demonstrates core Kubernetes concepts:

- ReplicaSet
- Deployment
- Scaling
- Rolling Updates
- Rollback

## Files

frontend-rs.yaml  
ReplicaSet that maintains 3 nginx pods.

webapp-deploy.yaml  
Deployment that manages nginx pods with resource limits.

## Commands Used

Create ReplicaSet

kubectl apply -f frontend-rs.yaml

Create Deployment

kubectl apply -f webapp-deploy.yaml

Scale Deployment

kubectl scale deployment webapp-deploy --replicas=5

Rolling Update

kubectl set image deployment/webapp-deploy nginx=nginx:1.25

Rollback

kubectl rollout undo deployment/webapp-deploy