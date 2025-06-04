# 3scale App of Apps

Para instanciar todas as Applications, AppProjects e etc presentes neste repositório crie a seguinte `Application` no Red Hat Openshift Gitops.

```
apiVersion: argoproj.io/v1alpha1
kind: Application
metadata:
  name: saude-3scale-app-of-apps
  namespace: openshift-gitops
spec:
  destination:
    name: in-cluster
    namespace: ''
    server: ''
  source:
    path: .
    repoURL: 'http://gitlab.saude.rj.gov.br:8081/3scale/gitops/app-of-apps.git'
    targetRevision: HEAD
    directory:
      recurse: true
  sources: []
  project: default
  syncPolicy:
    automated:
      prune: true
      selfHeal: true
    syncOptions:
      - Replace=true
      - ApplyOutOfSyncOnly=true
```