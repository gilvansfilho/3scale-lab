# 3scale App of Apps

Para instanciar todas as Applications, AppProjects e etc presentes neste repositório crie a seguinte `Application` no Red Hat Openshift Gitops.

```
apiVersion: argoproj.io/v1alpha1
kind: Application
metadata:
  name: 3scale-app-of-apps
  namespace: openshift-gitops
spec:
  destination:
    name: in-cluster
    namespace: ''
    server: ''
  source:
    path: .
    repoURL: 'https://github.com/gilvansfilho/3scale-lab.git'
    targetRevision: HEAD
    directory:
      recurse: true
  sources: []
  project: default
  syncPolicy:
    automated:
      prune: false
      selfHeal: true
    syncOptions:
      - Replace=false
      - ApplyOutOfSyncOnly=true
```