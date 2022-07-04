# Домашнее задание к занятию "12.1 Компоненты Kubernetes"

# Задача 1: Установить Minikube

Установку проводил на Yandex Cloud.

Проверяем версию minikube после установки

```
vagrant@epd9ks7lf20rq7r06tug:~$ minikube version
minikube version: v1.26.0
commit: f4b412861bb746be73053c9f6d2895f12cf78565
vagrant@epd9ks7lf20rq7r06tug:~$
```

Проверяем статус minikube
```
root@epd9ks7lf20rq7r06tug:/home/vagrant# minikube status
minikube
type: Control Plane
host: Running
kubelet: Running
apiserver: Running
kubeconfig: Configured

root@epd9ks7lf20rq7r06tug:/home/vagrant#
```

Проверяем запущенные служебные компоненты
```
root@epd9ks7lf20rq7r06tug:/home/vagrant# kubectl get pods --namespace=kube-system
NAME                                           READY   STATUS    RESTARTS   AGE
coredns-6d4b75cb6d-n5jmf                       1/1     Running   0          82s
etcd-epd9ks7lf20rq7r06tug                      1/1     Running   0          94s
kube-apiserver-epd9ks7lf20rq7r06tug            1/1     Running   0          94s
kube-controller-manager-epd9ks7lf20rq7r06tug   1/1     Running   0          94s
kube-proxy-dfcp8                               1/1     Running   0          83s
kube-scheduler-epd9ks7lf20rq7r06tug            1/1     Running   0          94s
storage-provisioner                            1/1     Running   0          91s
root@epd9ks7lf20rq7r06tug:/home/vagrant#
```

Удаляем кластер и создаем заново
```
root@epd9ks7lf20rq7r06tug:/home/vagrant# minikube delete
* Uninstalling Kubernetes v1.24.1 using kubeadm ...
* Deleting "minikube" in none ...
* Removed all traces of the "minikube" cluster.
root@epd9ks7lf20rq7r06tug:/home/vagrant# minikube start --vm-driver=none
* minikube v1.26.0 on Ubuntu 20.04 (amd64)
* Using the none driver based on user configuration
* Starting control plane node minikube in cluster minikube
* Running on localhost (CPUs=2, Memory=3931MB, Disk=30183MB) ...
* OS release is Ubuntu 20.04.4 LTS
* Preparing Kubernetes v1.24.1 on Docker 20.10.12 ...
  - kubelet.resolv-conf=/run/systemd/resolve/resolv.conf
  - Generating certificates and keys ...
  - Booting up control plane ...
  - Configuring RBAC rules ...
* Configuring local host environment ...
*
! The 'none' driver is designed for experts who need to integrate with an existing VM
* Most users should use the newer 'docker' driver instead, which does not require root!
* For more information, see: https://minikube.sigs.k8s.io/docs/reference/drivers/none/
*
! kubectl and minikube configuration will be stored in /root
! To use kubectl or minikube commands as your own user, you may need to relocate them. For example, to overwrite your own settings, run:
*
  - sudo mv /root/.kube /root/.minikube $HOME
  - sudo chown -R $USER $HOME/.kube $HOME/.minikube
*
* This can also be done automatically by setting the env var CHANGE_MINIKUBE_NONE_USER=true
* Verifying Kubernetes components...
  - Using image gcr.io/k8s-minikube/storage-provisioner:v5
* Enabled addons: default-storageclass, storage-provisioner
* Done! kubectl is now configured to use "minikube" cluster and "default" namespace by default
root@epd9ks7lf20rq7r06tug:/home/vagrant#
```

# Задача 2: Запуск Hello World


