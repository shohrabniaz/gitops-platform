# GitOps Platform

Multi-environment GitOps with **Argo CD**, **Helm**, and Kustomize overlays.

## Live demo (local kind cluster)

```powershell
cd "D:\New folder"
.\scripts\bootstrap-gitops-local.ps1 -UseKind
kubectl port-forward svc/argocd-server -n argocd 8443:443
```

Open https://localhost:8443 — user `admin`. Root app syncs `apps/overlays/dev` (nginx sample API).

See [docs/local-gitops-lab.md](docs/local-gitops-lab.md) (bootstrap script lives in the portfolio workspace `scripts/` folder).

## Structure

```
argocd/applications/   # App-of-apps (root-app)
apps/overlays/dev/       # Demo namespace + sample-api
```

## Bootstrap (DigitalOcean)

1. Create DOKS — `docs/digitalocean-doks-setup.md` (in workspace `docs/`)
2. `.\scripts\install-cluster-addons.ps1`
3. `kubectl apply -f argocd/applications/root-app.yaml`

## CI

GitHub Actions validates manifest YAML on every push.

## Phase 2

- Argo Rollouts canary
- External Secrets Operator
- Multi-env promotion via PR
