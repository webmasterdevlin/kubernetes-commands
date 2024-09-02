# Kubernetes (K8S) Debugging and Management Commands

## 1. Logs and Resource Usage

- View real-time resource usage:
```zsh
  kubectl top pods -n <namespace>
```
- View logs:
```zsh
  kubectl logs <pod_name> -n <namespace>
```
```zsh
  kubectl logs <pod-name> -c <container-name>
```

- View stream logs:
```zsh
  kubectl logs -f <pod_name> -n <namespace>
```

- View logs of a specific container in a multi-container pod:
```zsh
  kubectl logs <pod_name> -c <container_name> -n <namespace>
```

- View logs of a specific date/time range:
```zsh
  kubectl logs <pod_name> --since=<duration> -n <namespace>
```

- View recent events:
```zsh
  kubectl get events -n <namespace> --sort-by='.metadata.creationTimestamp'
```

---

## 2. Pod and Node Status

- View general status overview:
```zsh
  kubectl get pods -n <namespace>
```

- View detailed information:
```zsh
  kubectl describe pod <pod-name> -n <namespace>
```

- View node status:
```zsh
  kubectl get nodes
```

- View yaml configuration:
```zsh
  kubectl get pod <pod_name> -n <namespace> -o yaml
```

- Pod scheduling issues:
```zsh
  kubectl describe pod <pod_name> -n <namespace> | grep -A 10 "Events"
```

---

## 3. Configurations and Connectivity

- Check mounting of ConfigMap and Secret usage:
```zsh
  kubectl describe pod <pod_name> -n <namespace> | grep -A 5 "Mounts"
```

- View info about ConfigMap:
```zsh
  kubectl get configmap <configmap-name> -n <namespace>
```

- View info about Secret:
```zsh
  kubectl get secret <secret-name> -n <namespace>
```

- Check service endpoint resolution:
```zsh
  kubectl get endpoints <service_name> -n <namespace>
```

- View persistent volume claims (PVCs):
```zsh
  kubectl get pvc -n <namespace>
```

- View if the pod can reach other services or external URLs:
```zsh
  kubectl exec -it <pod_name> -n <namespace> -- curl <service_or_external_url>
```

---

## 4. Namespace Management

- List all namespaces:
```zsh
  kubectl get namespaces
```

- Switch to a different namespace:
```zsh
  kubectl config set-context --current --namespace=<namespace>
```

---

## 5. Deployment and ReplicaSet Management

- View deployment status:
```zsh
  kubectl get deployments -n <namespace>
```

- View detailed deployment information:
```zsh
  kubectl describe deployment <deployment_name> -n <namespace>
```

- Scale a deployment:
```zsh
  kubectl scale deployment <deployment_name> --replicas=<number_of_replicas> -n <namespace>
```

- View ReplicaSets:
```zsh
  kubectl get rs -n <namespace>
```

- Restart a pod deployment:
```zsh
  kubectl rollout restart deployment <deployment_name> -n <namespace>
```

- Use a yaml file to deploy:
```zsh
  kubectl apply -f <deployment-yaml>.yaml
```

---

## 6. Service and Ingress Management

- View services:
```zsh
  kubectl get svc -n <namespace>
```

- Describe a service:
```zsh
  kubectl describe svc <service_name> -n <namespace>
```

- View ingress resources:
```zsh
  kubectl get ingress -n <namespace>
```

- Describe an ingress resource:
```zsh
  kubectl describe ingress <ingress_name> -n <namespace>
```

---

## 7. ConfigMap and Secret Management

- Create a ConfigMap from a file:
```zsh
  kubectl create configmap <configmap_name> --from-file=<path_to_file> -n <namespace>
```

- Create a Secret from literal values:
```zsh
  kubectl create secret generic <secret_name> --from-literal=<key>=<value> -n <namespace>
```

---

## 8. Advanced Pod Management

- Debug and test a pod with an interactive shell:
```zsh
  kubectl run -it --rm --image=busybox --namespace=<namespace> debug-pod -- sh
```

- Execute a command inside a pod:
```zsh
  kubectl exec -it <pod_name> -n <namespace> -- <command>
```

- Debug a container within a pod (e.g., with bash):
```zsh
  kubectl exec -it <pod_name> -c <container_name> -- /bin/bash -n <namespace>
```

- Port-forward a local port to a pod:
```zsh
  kubectl port-forward <pod_name> <local_port>:<pod_port> -n <namespace>
```

- Copy files to/from a pod:
```zsh
  kubectl cp <namespace>/<pod_name>:<source_path> <destination_path>
```
```zsh
  kubectl cp <source_path> <namespace>/<pod_name>:<destination_path>
```

- Delete a pod:
```zsh
  kubectl delete pod <pod_name> -n <namespace>
```

---

## 9. Cluster Management

- View cluster information:
```zsh
  kubectl cluster-info
```

- View the API resources available in the cluster:
```zsh
  kubectl api-resources
```

- View API versions available:
```zsh
  kubectl api-versions
```