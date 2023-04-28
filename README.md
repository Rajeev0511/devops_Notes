# devops_Notes


kubectl port-forward --address 0.0.0.0 service/nginx 80:80
kubectl proxy -- its a http proxy service created by kubectl utility to acess kube-apiserver 
Starting to serve on 127.0.0.1:8001
Docker Storge
  Volume Mount - VM mounts a volume from volumes directory (/var/lib/docker/volume) ex: docker run -v data_vol:/var/lib/mysql mysql
  Bind Mount   - BM mounts a directory from any location on the Docker host ex: docker run -v /data/mysql:/var/lib/mysql mysql
