# kubeshop
Материалы для воркшопа по kubernetes/minikube/helm

## Установка

### macOS

Устанавливаем homebrew, если его нет.
```shell
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```
Устанавливаем docker, minikube, kubectl и helm
```shell
brew install docker
brew cask install minikube
brew install kubernetes-cli
brew install kubernetes-helm
```
Устанавливаем драйвер hyperkit
```shell
curl -LO https://storage.googleapis.com/minikube/releases/latest/docker-machine-driver-hyperkit \
  && sudo install -o root -g wheel -m 4755 docker-machine-driver-hyperkit /usr/local/bin/
```
### Linux

Устанавливаем minikube
```shell
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64 \
  && sudo install minikube-linux-amd64 /usr/local/bin/minikube
```
Устанавливаем kubectl
```shell
curl -LO https://storage.googleapis.com/kubernetes-release/release/v1.10.0/bin/linux/amd64/kubectl \
  && sudo install kubectl /usr/local/bin/ 
```
Устанавливаем helm
```shell
curl https://raw.githubusercontent.com/helm/helm/master/scripts/get | sh
```

Устанавливаем qemu-kvm и драйвер kvm2
Debian/Ubuntu:
```shell
sudo apt install libvirt-clients libvirt-daemon-system qemu-kvm
```
Fedora/CentOS/RHEL:
```shell
sudo yum install libvirt-daemon-kvm qemu-kvm
```

```shell
sudo usermod -a -G libvirt $(whoami)
newgrp libvirt
```

```shell
curl -LO https://storage.googleapis.com/minikube/releases/v0.25.0/docker-machine-driver-kvm2 \
  && sudo install docker-machine-driver-kvm2 /usr/local/bin/
```
## Запуск

### macOS
```shell
minikube start --vm-driver=hyperkit
```

### Linux
```shell
minikube start --vm-driver=kvm2
```

Для проверки работы проверяем список подов
```shell
kubectl get pods --all-namespaces
```