# 🧊 O que é o Minikube?

![Image](https://pbs.twimg.com/profile_images/1411010352670707720/j2_UYeDY_400x400.jpg)

![Image](https://cdn.thenewstack.io/media/2023/02/d1975006-minikubedash1.jpg)

![Image](https://fusionauth.io/img/docs/get-started/download-and-install/kubernetes/fa-minikube.png)

![Image](https://www.researchgate.net/publication/356817510/figure/fig6/AS%3A1098646078656512%401638949045044/The-diagram-of-a-Minikube-Kubernetes-cluster-15.ppm)

O **Minikube** é uma ferramenta que permite rodar um cluster Kubernetes localmente — ideal para desenvolvimento, testes e aprendizado do **Kubernetes**.

---

# 🚀 Como instalar o Minikube

Vou mostrar a forma mais comum para **Linux (Ubuntu/Debian)** e depois Windows e macOS.

---

# 🐧 Instalação no Ubuntu / Debian

### 1️⃣ Instalar dependências

```bash
sudo apt update
sudo apt install -y curl wget apt-transport-https
```

---

### 2️⃣ Instalar o Docker (driver recomendado)

```bash
sudo apt install -y docker.io
sudo usermod -aG docker $USER
newgrp docker
```

Verifique:

```bash
docker --version
```

---

### 3️⃣ Instalar o kubectl

```bash
curl -LO "https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl"

chmod +x kubectl
sudo mv kubectl /usr/local/bin/
```

Teste:

```bash
kubectl version --client
```

---

### 4️⃣ Instalar o Minikube

```bash
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64

sudo install minikube-linux-amd64 /usr/local/bin/minikube
```

Verifique:

```bash
minikube version
```

---

### 5️⃣ Iniciar o cluster

```bash
minikube start --driver=docker
```

Verificar status:

```bash
minikube status
kubectl get nodes
```

Se aparecer o nó como `Ready`, está funcionando ✅

---

# 🪟 Instalação no Windows

1. Instale o Docker Desktop.
2. Baixe o instalador do Minikube:
   👉 [https://minikube.sigs.k8s.io/docs/start/](https://minikube.sigs.k8s.io/docs/start/)
3. Instale via PowerShell:

```powershell
choco install minikube
```

ou via winget:

```powershell
winget install Kubernetes.minikube
```

Depois:

```powershell
minikube start
```

---

# 🍎 Instalação no macOS

Via Homebrew:

```bash
brew install minikube
brew install kubectl
```

Iniciar:

```bash
minikube start
```

---

# 📊 Abrir o Dashboard do Kubernetes

```bash
minikube dashboard
```

Isso abre a interface gráfica do cluster no navegador.

---

# 🛠 Comandos úteis

```bash
minikube stop        # parar cluster
minikube delete      # apagar cluster
minikube addons list # listar addons
minikube ip          # ver IP do cluster
```

---

Se você quiser, posso te passar:

* 🔹 Instalação otimizada para rodar o Tsuru
* 🔹 Configuração com mais CPU e memória
* 🔹 Instalação usando VirtualBox ao invés de Docker
* 🔹 Instalação para servidor (sem interface gráfica)

Você está usando qual sistema operacional?
