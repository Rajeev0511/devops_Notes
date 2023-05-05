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
