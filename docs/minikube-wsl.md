# **Minikube + WSL2 + Docker Desktop** 

## ✅ Antes de tudo (checagem importante)

No Windows:

1. Docker Desktop instalado
2. WSL2 ativado
3. Integração do Docker com sua distro Linux ativada

No Docker Desktop:

> ⚙️ Settings → Resources → WSL Integration
> Ative sua distro (Ubuntu, Debian, etc.)

---

# 🚀 Instalação no WSL (Ubuntu/Debian)

Abra o terminal da sua distro WSL.

---

## 1️⃣ Verifique se o Docker funciona dentro do WSL

```bash
docker version
docker ps
```

Se funcionar sem erro de permissão, está OK ✅

Se der erro de permissão:

```bash
sudo usermod -aG docker $USER
newgrp docker
```

---

## 2️⃣ Instalar kubectl

```bash
sudo apt update
sudo apt install -y kubectl
```

ou versão oficial:

```bash
curl -LO "https://dl.k8s.io/release/$(curl -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
chmod +x kubectl
sudo mv kubectl /usr/local/bin/
```

Teste:

```bash
kubectl version --client
```

---

## 3️⃣ Instalar Minikube

```bash
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube
```

Verifique:

```bash
minikube version
```

---

# 🔥 4️⃣ Iniciar o cluster (modo ideal para WSL)

Muito importante usar o driver Docker:

```bash
minikube start --driver=docker
```

Se quiser mais recursos (recomendado para Tsuru):

```bash
minikube start --driver=docker --memory=4096 --cpus=4
```

---

# ✅ 5️⃣ Testar

```bash
minikube status
kubectl get nodes
```

Se aparecer `Ready`, está funcionando 🎉

---

# 🎛 Dashboard (opcional)

No WSL, abra com:

```bash
minikube dashboard --url
```

Ele vai gerar uma URL que você pode abrir no navegador do Windows.

---

# ⚠️ Problemas comuns no WSL

### ❌ "Cannot connect to Docker daemon"

→ Verifique se a integração WSL está ativa no Docker Desktop.

### ❌ Erro de virtualização

→ Confirme que você está usando **WSL2**, não WSL1:

```bash
wsl -l -v
```

Deve mostrar versão 2.

---

Se você quiser, posso agora:

* 🔹 Te ajudar a instalar o Tsuru dentro do Minikube
* 🔹 Configurar ingress e LoadBalancer no WSL
* 🔹 Ajustar memória ideal para seu PC

Quanto de RAM seu computador tem?
