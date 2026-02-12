# Argo CD – Day 2 Lab

This guide covers key **Argo CD CLI operations** for managing applications through GitOps.

---

## 1. Verify Argo CD CLI Installation

```bash
argocd version
```

---

## 2. Login to Argo CD Server

```bash
argocd login <ARGOCD_SERVER_URL> --username admin --password <PASSWORD> --insecure
```

Example:

```bash
argocd login localhost:8080 --username admin --password admin --insecure
```

---

## 3. Check Logged-In User

```bash
argocd account get-user-info

argocd login a0b5fa36904a842c9bcd9232e0d0c936-1242755315.ap-south-1.elb.amazonaws.com:80 --username admin --password 5c0KKgcZ9tW66TZm --insecure

argocd repo add https://github.com/siva912sri/argocdcli.git

argocd app create nginx-demo-cli --repo https://github.com/siva912sri/argocdcli.git --path . --dest-server https://kubernetes.default.svc --dest-namespace default
```

---

## 4. List Applications

```bash
argocd app list

kubectl -n argocd get applications

kubectl -n argocd describe app demoapp
```

---

## 5. Get Application Details

```bash
argocd app get nginx-demo-cli
```

---

## 6. Sync the Application

```bash
argocd app sync nginx-demo-cli
```

---

## 7. Refresh Application Status

```bash
argocd app refresh nginx-demo-cli
```

---

## 8. Check Application Health and Sync Status

```bash
argocd app get nginx-demo-cli --refresh
```

---

## 9. Rollback Application to Previous Revision

To list previous revisions:

```bash
argocd app history nginx-demo-cli
```

Then rollback using the **revision number** (not commit hash):

```bash
argocd app rollback nginx-demo-cli 1

argocd app set nginx-demo-cli --sync-policy automated

kubectl get pods -n default -l app=nginx

kubectl get deployment nginx-demo-cli -n default -o=jsonpath='{.spec.template.spec.containers[*].image}'
```

---

## 10. Delete an Application

```bash
argocd app delete nginx-demo-cli
```

---

## 11. Logout from Argo CD

```bash
argocd logout <ARGOCD_SERVER_URL>
```

Example:

```bash
argocd logout localhost:8080
```

---

## Notes

* Always verify the correct context before syncing or deleting apps.
* If `argocd` command is not found, ensure it’s added to your PATH.

---
