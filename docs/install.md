# 📦 Instalar usando Kubernetes + Helm

Se você prefere rodar no Kubernetes, existe um chart oficial que instala tudo de forma automatizada:

1. Instale **Minikube ou um cluster Kubernetes real**.



2. Adicione o repositório Helm do Tsuru:

   ```bash
   helm repo add tsuru https://tsuru.github.io/charts
   helm install tsuru tsuru/tsuru-stack --create-namespace --namespace tsuru-system
   ```

3. Após instalação, crie um usuário administrador:

   ```bash
   kubectl exec -it -n tsuru-system deploy/tsuru-api -- tsurud root user create admin@admin.com
   ```

Essa opção é excelente para ambientes de produção ou nuvem moderna. ([tsuru.github.io][2])

---

## 🎯 Próximos passos após a instalação

✔ Definir um domínio público e configurar DNS.
✔ Instalar plataformas de linguagem (ex: Node.js, Python, Go).
✔ Criar equipes e usuários no Tsuru.
✔ Criar sua primeira aplicação e fazer deploy com `tsuru app create`. ([docs.tsuru.io][3])

---

Se você quiser, posso fornecer um **script pronto para Ubuntu 20.04/22.04** ou uma versão **para produção com Kubernetes no GCP/AWS**. Quer algum desses?

[1]: https://docs.tsuru.io/0.1/docker.html?utm_source=chatgpt.com "Build your own PaaS with tsuru and Docker — tsuru 0.1.0 documentation"
[2]: https://tsuru.github.io/docs/getting_started/install_minikube/?utm_source=chatgpt.com "Installing Tsuru in a local Kubernetes cluster with Helm - Tsuru Docs"
[3]: https://docs.tsuru.io/1.10/installing/using-tsuru-installer.html?utm_source=chatgpt.com "tsuru Installer — tsuru 1.10.3-rc5 documentation"
