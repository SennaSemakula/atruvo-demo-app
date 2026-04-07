# Atruvo Demo App

Sample Kubernetes application demonstrating Atruvo AI Delivery Guard.

This repo has a clean set of K8s manifests with proper security controls.
Open a PR that weakens security (e.g. delete the NetworkPolicy, remove TLS,
widen RBAC) and watch Atruvo block it.

## What's here

```
k8s/base/
  deployment.yaml      # Hardened deployment (non-root, read-only fs, resource limits)
  service.yaml         # ClusterIP service
  ingress.yaml         # TLS-enabled ingress
  networkpolicy.yaml   # Restricts ingress to frontend namespace only
  pdb.yaml             # PodDisruptionBudget (min 2 available)

.atruvo/
  policy.overlay.yaml  # Local overlay: tighter production thresholds

.github/workflows/
  atruvo-gate.yml      # Atruvo AI Delivery Guard action
```
