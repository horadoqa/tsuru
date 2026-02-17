Perfeito 💪 16 GB de RAM é **mais do que suficiente** para rodar **Minikube + Tsuru** com folga.

Vamos fazer a instalação correta do **Tsuru** dentro do **Minikube** usando Helm (modo recomendado).

Vou te passar o passo-a-passo ideal para **WSL2 + Docker Desktop**.

---

# 🚀 1️⃣ Iniciar o Minikube com recursos adequados

Com 16GB, recomendo:

```bash
minikube start --driver=docker --memory=8192 --cpus=4
```

Verifique:

```bash
kubectl get nodes
```

Deve aparecer `Ready`.

---

# 📦 2️⃣ Instalar o Helm (se ainda não tiver)

```bash
curl https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bash
```

Teste:

```bash
helm version
```

---

# 📥 3️⃣ Adicionar repositório do Tsuru

```bash
helm repo add tsuru https://tsuru.github.io/charts
helm repo update
```

---

# 🏗 4️⃣ Instalar o Tsuru Stack

Agora vamos instalar tudo (API, banco, router, etc.):

```bash
helm install tsuru tsuru/tsuru-stack \
  --create-namespace \
  --namespace tsuru-system
```

Isso pode levar alguns minutos.

Verifique:

```bash
kubectl get pods -n tsuru-system
```

Espere todos ficarem `Running`.

---

# 👤 5️⃣ Criar usuário admin

Depois que os pods estiverem rodando:

```bash
kubectl exec -it -n tsuru-system deploy/tsuru-api -- tsurud root user create admin@admin.com
```

Ele vai pedir senha.

---

# 🌐 6️⃣ Acessar API do Tsuru no WSL

Como estamos no Minikube:

```bash
minikube service tsuru-api-service -n tsuru-system
```

Ele abrirá a URL automaticamente no navegador do Windows.

---

# 🧩 7️⃣ Instalar cliente tsuru

Baixe o cliente:

```bash
curl -fsSL https://tsuru.io/get | bash
```

Depois configure:

```bash
tsuru target-add local <URL_DA_API>
tsuru login
```

---

# 🧠 Dica importante para WSL

Se o LoadBalancer não funcionar automaticamente, habilite o túnel:

```bash
minikube tunnel
```

Deixe esse comando rodando em outro terminal.

---

# 📊 Recursos recomendados para seu PC (16GB)

| Serviço  | Recomendação |
| -------- | ------------ |
| Minikube | 6–8GB RAM    |
| CPUs     | 4            |
| Disco    | 30GB livres  |

Você ainda terá RAM suficiente para outras coisas.

---

Se quiser, posso agora:

* 🔥 Configurar ingress com domínio local
* 🚀 Fazer deploy da sua primeira app Node ou Python
* 🏢 Configurar ambiente mais próximo de produção
* 🧱 Explicar a arquitetura interna do Tsuru

Qual você quer fazer primeiro?
