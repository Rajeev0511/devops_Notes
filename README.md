# devops_Notes


kubectl port-forward --address 0.0.0.0 service/nginx 80:80 \n
kubectl proxy -- its a http proxy service created by kubectl utility to acess kube-apiserver  \n
Starting to serve on 127.0.0.1:8001 \n
Docker Storge \n
  Volume Mount - VM mounts a volume from volumes directory (/var/lib/docker/volume) ex: docker run -v data_vol:/var/lib/mysql mysql \n
  Bind Mount   - BM mounts a directory from any location on the Docker host ex: docker run -v /data/mysql:/var/lib/mysql mysql \n

K8s Metrics Server

  Metrics Server collects resource metrics from Kubelets and exposes them in Kubernetes apiserver through Metrics API for use by Horizontal Pod Autoscaler and Vertical Pod Autoscaler. Metrics API can also be accessed by kubectl top, making it easier to debug autoscaling pipelines.

  Metrics Server is not meant for non-autoscaling purposes. For example, don't use it to forward metrics to monitoring solutions, or as a source of monitoring solution metrics. In such cases please collect metrics from Kubelet /metrics/resource endpoint directly.
       
       I was able to reproduce your issue on the latest minikube v1.25.2 (Kubernetes v1.23.3 on Docker 20.10.12): the metrics-server pod does not start because of X509 error and then kubectl top node results in Error from server (ServiceUnavailable): the server is currently unable to handle the request (get nodes.metrics.k8s.io).

    The workaround that fixed the issue for me was to add --kubelet-insecure-tls in the deployment.

    kind: Deployment
    spec:
        spec:
          containers:
          - args:
            - --kubelet-insecure-tls

 

**Kubernetes Add On:**

  **Amazon VPC CNI plugin for Kubernetes:** A Kubernetes container network interface (CNI) plugin that provides native VPC networking for your cluster. The self-managed or managed type of this add-on is installed on each Amazon EC2 node, by default. 
  
  **CoreDNS:** A flexible, extensible DNS server that can serve as the Kubernetes cluster DNS._two replicas_ of the CoreDNS image are deployed _by default_, regardless of the number of nodes deployed in your cluster. _The CoreDNS Pods provide name resolution for all Pods in the cluster_ 
  
  **Kube-proxy:**  Maintains network rules on each Amazon EC2 node. It enables network communication to your Pods
  
  **Amazon GuardDuty agent:** Amazon GuardDuty is a security monitoring service that analyzes and processes foundational data sources including AWS CloudTrail management events and Amazon VPC flow logs. Amazon GuardDuty also processes features, such as Kubernetes audit logs and runtime monitoring.
  
  **ExternalDNS** synchronizes exposed Kubernetes Services and Ingresses with DNS providers
