FROM vamshionrails/archlinux_base
#RUN mkdir /Apps/src

RUN export ETCD_VER=v3.4.5

 
RUN rm -f /Apps/etcd/src/etcd-v3.4.5-linux-amd64.tar.gz
RUN rm -rf /Apps/etcd/src && mkdir -p /Apps/etcd

RUN curl -L https://storage.googleapis.com/etcd/v3.4.5/etcd-v3.4.5-linux-amd64.tar.gz -o /Apps/etcd/src/etcd-v3.4.5-linux-amd64.tar.gz
RUN tar xzvf /Apps/etcd/src/etcd-v3.4.5-linux-amd64.tar.gz -C /Apps/etcd --strip-components=1
RUN rm -f /Apps/src/etcd-v3.4.5-linux-amd64.tar.gz

RUN /Apps/etcd/etcd --version
RUN /Apps/etcd/etcdctl version
RUN curl -L https:https://dl.k8s.io/v1.17.0/kubernetes-client-linux-amd64.tar.gz -o /Apps/src/
RUN curl -L https://dl.k8s.io/v1.17.0/kubernetes-server-linux-amd64.tar.gz -o /Apps/src/
RUN curl -L wget https://dl.k8s.io/v1.17.0/kubernetes-node-linux-amd64.tar.gz -o /Apps/src
RUN tar -xvzf /Apps/src/dl.k8s.io/v1.17.0/kubernetes-client-linux-amd64.tar.gz -C /Apps/
RUN tar -xvzf /Apps/src/kubernetes-server-linux-amd64.tar.gz -C /Apps/
RUN tar -xvzf /Apps/src/kubernetes-node-linux-amd64.tar.gz -C /Apps/
