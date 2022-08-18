# Monitor Kubernetes cluster (Kubeadm) with metrics-server

![K8s](images/k8s-metrics-server.png)

## Consideration

- We have Kubeadm cluster with one master node and atleast one worker node in ready state. To check the cluster state, run: 
```kubectl get nodes" command```

### Step-01: Install the metrics-server on master node

Clone the metrics server from below GitHub repository and create a deployment.
(https://github.com/kubernetes-sigs/metrics-server/releases/tag/v0.3.7)

```kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/download/v0.3.7/components.yaml```

### Step-02: Edit the metrics-server Deployment manifest file

```kubectl edit deployment.apps metrics-server -n kube-system```

Now, go to specs section and add below three commands:

```command:
        - /metrics-server
        - --kubelet-insecure-tls
        - --kubelet-preferred-address-types=InternalDNS,InternalIP,ExternalDNS,ExternalIP,Hostname```

Save and exit from the manifest file.

### Step-03: Restart the kubelet service

```sudo systemctl restart kubelet```

```sudo systemctl enable kubelet```

### Step-04: View the metrics captured by metrics-server

Note: Usually it takes around 2-3 minutes by metrics-server to aggregate the metrics from all the nodes.

Run below command to view resource utilization at Node level:

```kubectl top nodes```

Run below command to view resource utilization at Pod level:

```kubectl top pods```


## Resources

- Kubeadm [Installation](https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/install-kubeadm/)
- Docker [Installation](https://docs.docker.com/engine/install/#server)
- Weaver [Installation](https://www.weave.works/docs/net/latest/kubernetes/kube-addon/)
- CKA Exam [Curriculum](https://github.com/cncf/curriculum)


