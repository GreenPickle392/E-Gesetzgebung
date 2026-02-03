# egesetz-gitops

GitOps repo for E-Gesetzgebung running on Kubernetes via Argo CD (App-of-Apps).
Workloads are deployed as Helm charts.

## Structure
- argocd/root-app.yaml: root application pointing to argocd/apps
- argocd/apps/*.yaml: child applications (namespace, mysql, iamock, editor, backend)
- charts/*: helm charts per component

## First install
1) Create Argo CD in your cluster (not in this repo)
2) Apply root app:
   kubectl apply -f argocd/root-app.yaml

## Access (port-forward)
- Backend:
  kubectl -n egesetz port-forward svc/backend-with-cockpit 8080:8080
  http://localhost:8080/egesetzgebung-platform-backend/actuator/health

