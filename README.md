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
```

---

## 4. List Applications

```bash
argocd app list
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
