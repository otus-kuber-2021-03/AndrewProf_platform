Kubernetes production clusters
++++++++++++++++++++++++++++++++++++++
Создание нод для кластера в GCP
======================
Подготовка машин
Отключите на машинах swap
swapoff -a
Включаем маршрутизацию
cat > /etc/sysctl.d/99-kubernetes-cri.conf <<EOF
net.bridge.bridge-nf-call-iptables = 1
net.ipv4.ip_forward = 1
net.bridge.bridge-nf-call-ip6tables = 1
EOF

sysctl --system
Устанавливаем Docker


Установка kubeadm, kubelet and kubectl
=======================================
apt-get update && apt-get install -y apt-transport-https curl
curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add -

cat <<EOF > /etc/apt/sources.list.d/kubernetes.list
deb https://apt.kubernetes.io/ kubernetes-xenial main
EOF

apt-get update
apt-get install -y kubelet=1.17.4-00 kubeadm=1.17.4-00 kubectl=1.17.4-00

Создание кластера
