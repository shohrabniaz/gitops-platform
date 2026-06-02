# GitOps Platform

Multi-environment GitOps with **ArgoCD**, **Helm**, **Kustomize**, and canary-ready structure.

## Status

Phase 1 scaffold — deploy to DOKS after running `scripts/install-cluster-addons.ps1`.

## Structure

```
apps/           # Application manifests (Kustomize overlays)
infra/          # Cluster infra (ingress, cert-manager refs)
argocd/         # ArgoCD Application manifests
sample-app/     # Demo API + Helm chart
```

## Bootstrap (Phase 1)

1. Create DOKS cluster — `docs/digitalocean-doks-setup.md`
2. Install addons — `scripts/install-cluster-addons.ps1`
3. Port-forward ArgoCD UI — see DOKS doc
4. Apply root app:

```powershell
kubectl apply -f argocd/applications/root-app.yaml
```

## Phase 2 additions

- Argo Rollouts canary
- External Secrets Operator
- Multi-env promotion via PR

## Cost

~$36–40 USD/month on DigitalOcean (1 node + LB).
