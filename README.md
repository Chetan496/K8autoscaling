## Kubernetes Pod auto scaling based on CPU, memory etc
To enable cluster autoscaling, ensure you have `metrics-server` enabled.
You can use the `metrics-server-components.yaml` manifest to enable this metric if its not enabled.

For testing purpose, deploy the K8 manifest `php-apache.yaml` which creates php and apache Deployment in K8 cluster
To enable autoscaling on it based on the CPU and memory, deploy the manifest `podautoscaler.yaml`

To load the 'php-apache' deployment, use the below command:
```
kubectl run -i --tty load-generator --rm --image=busybox --restart=Never -- /bin/sh -c "while sleep 0.01; do wget -q -O- http://php-apache; done"
```

Then observe the pods and replicas for the `php-apache`
You will see that it increases.



