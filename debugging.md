real-time resource usage
$ kubectl top pods -n <namespace>

general status overview
$ kubectl get pods -n <namespace>

detailed information
$ kubectl describe pod <pod-name> -n <namespace>

logs
$ kubectl logs <pod_name> -n <namespace>
$ kubectl logs <pod-name> -c <container-name>

stream logs
$ kubectl logs -f <pod_name> -n <namespace>

use a yaml file
$ kubectl apply -f <deployment-yaml>.yaml

view recent events
$ kubectl get events -n <namespace> --sort-by='.metadata.creationTimestamp'

restart a pod deployment
$ kubectl rollout restart deployment <deployment_name> -n <namespace>

info about configmap
$ kubectl get configmap <configmap-name> -n <namespace>

info about secret
$ kubectl get secret <secret-name> -n <namespace>

used for debugging and testing purposes
$ kubectl run -it --rm --image=busybox --namespace=<namespace> debug-pod -- sh

execute a command inside a pod
$ kubectl exec -it <pod_name> -n <namespace> -- <command>

check yaml configuration
$ kubectl get pod <pod_name> -n <namespace> -o yaml

delete a pod
$ kubectl delete pod <pod_name> -n <namespace>

check node status
$ kubectl get nodes

check persistent volume claims (PVCs)
$ kubectl get pvc -n <namespace>


if the pod can reach other services or external URLs.
$ kubectl exec -it <pod_name> -n <namespace> -- curl <service_or_external_url>


check mounting of ConfigMap and Secret usage
$ kubectl describe pod <pod_name> -n <namespace> | grep -A 5 "Mounts"


check service endpoint resolution
$ kubectl get endpoints <service_name> -n <namespace>


pod scheduling issues
$ kubectl describe pod <pod_name> -n <namespace> | grep -A 10 "Events"