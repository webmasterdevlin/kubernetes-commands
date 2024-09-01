### K8S Debugging
---
view real-time resource usage
```bash
kubectl top pods -n <namespace>
```
---
view general status overview
```bash
kubectl get pods -n <namespace>
```
---
view detailed information
```bash
kubectl describe pod <pod-name> -n <namespace>
```
---
view logs
```bash
kubectl logs <pod_name> -n <namespace>
```
---
```bash
kubectl logs <pod-name> -c <container-name>
```
---
view stream logs
```bash
kubectl logs -f <pod_name> -n <namespace>
```
---
use a yaml file
```bash
kubectl apply -f <deployment-yaml>.yaml
```
---
view recent events
```bash
kubectl get events -n <namespace> --sort-by='.metadata.creationTimestamp'
```
---
restart a pod deployment
```bash
kubectl rollout restart deployment <deployment_name> -n <namespace>
```
---
view info about configmap
```bash
kubectl get configmap <configmap-name> -n <namespace>
```
---
view info about secret
```bash
kubectl get secret <secret-name> -n <namespace>
```
---
debug and test a pod
```bash
kubectl run -it --rm --image=busybox --namespace=<namespace> debug-pod -- sh
```
---
execute a command inside a pod
```bash
kubectl exec -it <pod_name> -n <namespace> -- <command>
```
---
view yaml configuration
```bash
kubectl get pod <pod_name> -n <namespace> -o yaml
```
---
delete a pod
```bash
kubectl delete pod <pod_name> -n <namespace>
```
---
view node status
```bash
kubectl get nodes
```
---
view persistent volume claims (PVCs)
```bash
kubectl get pvc -n <namespace>
```
---
view if the pod can reach other services or external URLs.
```bash
kubectl exec -it <pod_name> -n <namespace> -- curl <service_or_external_url>
```
---
check mounting of ConfigMap and Secret usage
```bash
kubectl describe pod <pod_name> -n <namespace> | grep -A 5 "Mounts"
```
---
check service endpoint resolution
```bash
kubectl get endpoints <service_name> -n <namespace>
```
---
pod scheduling issues
```bash
kubectl describe pod <pod_name> -n <namespace> | grep -A 10 "Events"
```
---