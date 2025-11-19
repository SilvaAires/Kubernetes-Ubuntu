# Kubernetes-Ubuntu
☸️ Guia Completo de Comandos Kubernetes (Ubuntu 24.04.3 LTS)

---

## 📋 **Informações e Versão**

* `kubectl version` → Exibe versão cliente/servidor
* `kubectl cluster-info` → Mostra informações do cluster
* `kubectl get componentstatuses` → Status dos componentes
* `kubectl api-resources` → Lista todos os recursos da API
* `kubectl api-versions` → Versões da API disponíveis
* `kubectl config view` → Configuração do kubectl
* `kubectl get nodes` → Lista nós do cluster

---

## ☸️ **Gerenciamento de Pods**

### 🚀 Executando Pods

* `kubectl run nginx --image=nginx` → Cria pod simples
* `kubectl run debug --image=busybox --rm -it -- /bin/sh` → Pod interativo
* `kubectl apply -f pod.yaml` → Cria pod via arquivo YAML
* `kubectl create deployment nginx --image=nginx` → Cria deployment
* `kubectl create job my-job --image=busybox -- date` → Cria job

### 📊 Listando e Monitorando

* `kubectl get pods` → Lista pods
* `kubectl get pods -A` → Todos os namespaces
* `kubectl get pods -o wide` → Informações detalhadas
* `kubectl get pods --field-selector status.phase=Running` → Filtro por status
* `kubectl get pods --show-labels` → Mostra labels
* `kubectl describe pod meu-pod` → Descrição detalhada
* `kubectl logs meu-pod` → Logs do pod
* `kubectl logs -f meu-pod` → Logs em tempo real
* `kubectl logs --tail=100 meu-pod` → Últimas 100 linhas
* `kubectl top pod` → Uso de recursos dos pods

### ⚙️ Gerenciando Pods

* `kubectl exec -it meu-pod -- /bin/bash` → Executa comando no pod
* `kubectl cp meu-pod:/path/local .` → Copia arquivo do pod
* `kubectl cp local/file meu-pod:/path/` → Copia arquivo para pod
* `kubectl delete pod meu-pod` → Remove pod
* `kubectl delete pod --all` → Remove todos pods
* `kubectl edit pod meu-pod` → Edita pod em tempo real
* `kubectl port-forward meu-pod 8080:80` → Port forward

### 🔍 Debug e Troubleshooting

* `kubectl get events --sort-by=.metadata.creationTimestamp` → Eventos ordenados
* `kubectl get events -w` → Watch eventos em tempo real
* `kubectl debug meu-pod -it --image=busybox` → Pod de debug
* `kubectl attach meu-pod -i -t` → Conecta ao pod em execução

---

## 🏞️ **Gerenciamento de Deployments**

### 🔍 Buscando e Monitorando

* `kubectl get deployments` → Lista deployments
* `kubectl get deployments -o wide` → Informações detalhadas
* `kubectl describe deployment meu-deployment` → Descrição detalhada
* `kubectl get rs` → Lista replica sets
* `kubectl rollout status deployment/meu-deployment` → Status do rollout

### 🏗️ Criando e Atualizando

* `kubectl create deployment nginx --image=nginx:1.20` → Cria deployment
* `kubectl apply -f deployment.yaml` → Aplica arquivo YAML
* `kubectl set image deployment/nginx nginx=nginx:1.21` → Atualiza imagem
* `kubectl scale deployment nginx --replicas=5` → Escala deployment
* `kubectl autoscale deployment nginx --min=2 --max=10 --cpu-percent=80` → Auto scaling

### 🔄 Gerenciando Rollouts

* `kubectl rollout history deployment/meu-deployment` → Histórico de rollouts
* `kubectl rollout undo deployment/meu-deployment` → Rollback
* `kubectl rollout undo deployment/meu-deployment --to-revision=2` → Rollback para revisão específica
* `kubectl rollout pause deployment/meu-deployment` → Pausa rollout
* `kubectl rollout resume deployment/meu-deployment` → Retoma rollout
* `kubectl rollout restart deployment/meu-deployment` → Reinicia pods

### 🗂️ Gerenciando Deployments

* `kubectl delete deployment meu-deployment` → Remove deployment
* `kubectl patch deployment meu-deployment -p '{"spec":{"replicas":3}}'` → Patch deployment
* `kubectl edit deployment meu-deployment` → Edita deployment

---

## 🔗 **Serviços e Networking**

### 🌐 Serviços

* `kubectl get services` → Lista serviços
* `kubectl get svc` → Alias para serviços
* `kubectl describe service meu-service` → Descrição detalhada
* `kubectl expose deployment nginx --port=80 --type=LoadBalancer` → Expõe deployment
* `kubectl create service clusterip meu-svc --tcp=80:8080` → Cria service
* `kubectl delete service meu-service` → Remove service

### 🌐 Ingress

* `kubectl get ingress` → Lista ingress
* `kubectl describe ingress meu-ingress` → Descrição detalhada
* `kubectl apply -f ingress.yaml` → Aplica configuração ingress

### 🔗 Network Policies

* `kubectl get networkpolicies` → Lista políticas de rede
* `kubectl describe networkpolicy minha-policy` → Descrição detalhada

---

## 💾 **Storage e Volumes**

### 📦 Persistent Volumes (PV)

* `kubectl get pv` → Lista persistent volumes
* `kubectl describe pv meu-pv` → Descrição detalhada
* `kubectl apply -f pv.yaml` → Cria persistent volume

### 📁 Persistent Volume Claims (PVC)

* `kubectl get pvc` → Lista persistent volume claims
* `kubectl describe pvc meu-pvc` → Descrição detalhada
* `kubectl apply -f pvc.yaml` → Cria persistent volume claim

### 🔧 Storage Classes

* `kubectl get storageclass` → Lista storage classes
* `kubectl describe storageclass minha-sc` → Descrição detalhada

---

## 🧹 **ConfigMaps e Secrets**

### ⚙️ ConfigMaps

* `kubectl get configmaps` → Lista configmaps
* `kubectl describe configmap meu-cm` → Descrição detalhada
* `kubectl create configmap meu-cm --from-literal=chave=valor` → Cria via linha de comando
* `kubectl create configmap meu-cm --from-file=./config.properties` → Cria via arquivo

### 🔐 Secrets

* `kubectl get secrets` → Lista secrets
* `kubectl describe secret meu-secret` → Descrição detalhada
* `kubectl create secret generic meu-secret --from-literal=senha=123456` → Cria secret
* `kubectl create secret docker-registry regcred --docker-server=registry --docker-username=user --docker-password=pass` → Secret de registry

---

## 📊 **Namespaces e Contextos**

### 📁 Namespaces

* `kubectl get namespaces` → Lista namespaces
* `kubectl create namespace meu-ns` → Cria namespace
* `kubectl delete namespace meu-ns` → Remove namespace
* `kubectl config set-context --current --namespace=meu-ns` → Muda namespace atual

### 🔄 Contextos

* `kubectl config get-contexts` → Lista contextos
* `kubectl config use-context meu-contexto` → Muda contexto
* `kubectl config set-context meu-contexto --namespace=meu-ns` → Configura contexto
* `kubectl config current-context` → Contexto atual

---

## 🔍 **Inspeção e Debug**

* `kubectl get all` → Lista todos os recursos
* `kubectl get all -A` → Todos recursos em todos namespaces
* `kubectl explain pod` → Documentação do recurso
* `kubectl explain pod.spec.containers` → Documentação específica
* `kubectl auth can-i create pods` → Verifica permissões
* `kubectl auth can-i list pods --as=system:serviceaccount:default:default` → Verifica permissões específicas

---

## ☸️ **Kubernetes Compose (Kompose)**

* `kompose convert` → Converte docker-compose para Kubernetes
* `kompose convert -f docker-compose.yml` → Arquivo específico
* `kompose up` → Implanta no Kubernetes
* `kompose down` → Remove do Kubernetes

---

## 🔐 **Segurança e RBAC**

### 👤 Service Accounts

* `kubectl get serviceaccounts` → Lista service accounts
* `kubectl create serviceaccount meu-sa` → Cria service account
* `kubectl describe serviceaccount meu-sa` → Descrição detalhada

### 🛡️ Roles e RoleBindings

* `kubectl get roles` → Lista roles
* `kubectl get rolebindings` → Lista role bindings
* `kubectl describe role minha-role` → Descrição detalhada
* `kubectl auth reconcile -f rbac.yaml` → Reconcilia RBAC

---

## ⚡ **Avançados**

### 🔄 StatefulSets

* `kubectl get statefulsets` → Lista statefulsets
* `kubectl describe statefulsets meu-sts` → Descrição detalhada
* `kubectl scale statefulsets meu-sts --replicas=3` → Escala statefulset

### 🎯 DaemonSets

* `kubectl get daemonsets` → Lista daemonsets
* `kubectl describe daemonsets meu-ds` → Descrição detalhada

### ⏰ Jobs e CronJobs

* `kubectl get jobs` → Lista jobs
* `kubectl get cronjobs` → Lista cronjobs
* `kubectl describe cronjob meu-cj` → Descrição detalhada

### 🔧 Custom Resources (CRD)

* `kubectl get crd` → Lista custom resource definitions
* `kubectl get nome-do-crd` → Lista instâncias do CRD

---

## 📊 **Formatação de Saída**

* `kubectl get pods -o json` → Saída JSON
* `kubectl get pods -o yaml` → Saída YAML
* `kubectl get pods -o jsonpath='{.items[*].metadata.name}'` → JSONPath
* `kubectl get pods --sort-by=.metadata.creationTimestamp` → Ordenado por criação
* `kubectl get pods -o custom-columns="NAME:.metadata.name,STATUS:.status.phase"` → Colunas customizadas

---

## 🚨 **Troubleshooting**

* `kubectl get nodes -o wide` → Status dos nós
* `kubectl describe node nome-do-node` → Detalhes do nó
* `kubectl top nodes` → Uso de recursos dos nós
* `kubectl get pods --field-selector=status.phase!=Running` → Pods não running
* `kubectl get events --sort-by='.lastTimestamp'` → Eventos recentes
* `kubectl logs --previous meu-pod` → Logs do container anterior

---

## ☸️ **Exemplo: Aplicação Web Completa**

```bash
# 1. Criar namespace
kubectl create namespace minha-app

# 2. Aplicar configurações
kubectl apply -f deployment.yaml -n minha-app
kubectl apply -f service.yaml -n minha-app
kubectl apply -f ingress.yaml -n minha-app

# 3. Verificar status
kubectl get all -n minha-app

# 4. Monitorar rollout
kubectl rollout status deployment/web-app -n minha-app

# 5. Verificar serviços
kubectl get svc -n minha-app

# 6. Port forward para teste
kubectl port-forward svc/web-service 8080:80 -n minha-app
```

### 📄 **deployment.yaml exemplo:**
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: web-app
  namespace: minha-app
spec:
  replicas: 3
  selector:
    matchLabels:
      app: web-app
  template:
    metadata:
      labels:
        app: web-app
    spec:
      containers:
      - name: nginx
        image: nginx:1.21
        ports:
        - containerPort: 80
        env:
        - name: ENVIRONMENT
          value: "production"
---
apiVersion: v1
kind: Service
metadata:
  name: web-service
  namespace: minha-app
spec:
  selector:
    app: web-app
  ports:
  - port: 80
    targetPort: 80
  type: LoadBalancer
```

---

## 🧹 **Limpeza e Manutenção**

* `kubectl delete all --all` → Remove todos recursos no namespace
* `kubectl delete all --all -n meu-namespace` → Remove tudo no namespace específico
* `kubectl delete pods --field-selector=status.phase=Succeeded` → Remove pods completados
* `kubectl delete pods --field-selector=status.phase=Failed` → Remove pods falhos
* `kubectl patch pv meu-pv -p '{"spec":{"persistentVolumeReclaimPolicy":"Delete"}}'` → Configura reclaim policy

---

## 📑 **O que consta na documentação oficial do Kubernetes**

### 🔹 1. Comandos principais de **pods**

* `kubectl get pods` – lista pods
* `kubectl describe pod` – detalhes do pod
* `kubectl logs` – logs do pod
* `kubectl exec` – executa comando no pod
* `kubectl port-forward` – encaminhamento de porta
* `kubectl cp` – copia arquivos de/para pod
* `kubectl attach` – anexa a um container em execução
* `kubectl wait` – aguarda condições específicas

### 🔹 2. Comandos principais de **deployments**

* `kubectl create deployment` – cria deployment
* `kubectl get deployments` – lista deployments
* `kubectl scale deployment` – escala deployment
* `kubectl rollout` – gerencia rollouts
* `kubectl set image` – atualiza imagem do deployment
* `kubectl autoscale` – configura auto-scaling

### 🔹 3. Comandos de **serviços e networking**

* `kubectl get services` – lista serviços
* `kubectl expose` – expõe aplicação como serviço
* `kubectl get ingress` – lista regras de ingress
* `kubectl describe service` – detalhes do serviço

### 🔹 4. Comandos de **storage**

* `kubectl get pv` – persistent volumes
* `kubectl get pvc` – persistent volume claims
* `kubectl describe pv` – detalhes do volume
* `kubectl get storageclass` – classes de storage

### 🔹 5. Comandos de **configuração**

* `kubectl get configmaps` – lista configmaps
* `kubectl create configmap` – cria configmap
* `kubectl get secrets` – lista secrets
* `kubectl create secret` – cria secret

### 🔹 6. Comandos de **namespaces**

* `kubectl get namespaces` – lista namespaces
* `kubectl create namespace` – cria namespace
* `kubectl config set-context` – muda namespace atual

### 🔹 7. Comandos de **RBAC e segurança**

* `kubectl get serviceaccounts` – service accounts
* `kubectl get roles` – roles
* `kubectl get rolebindings` – role bindings
* `kubectl auth can-i` – verifica permissões

### 🔹 8. Comandos de **estado e jobs**

* `kubectl get statefulsets` – statefulsets
* `kubectl get daemonsets` – daemonsets
* `kubectl get jobs` – jobs
* `kubectl get cronjobs` – cronjobs

### 🔹 9. Comandos de **inspeção e debug**

* `kubectl describe` – descrição detalhada de recursos
* `kubectl explain` – documentação de recursos
* `kubectl get events` – eventos do cluster
* `kubectl top` – métricas de recursos

### 🔹 10. Comandos de **aplicação de arquivos**

* `kubectl apply` – aplica/configura recurso via arquivo
* `kubectl create` – cria recurso via arquivo
* `kubectl delete` – remove recurso via arquivo
* `kubectl patch` – atualização parcial de recurso
* `kubectl edit` – edita recurso

---

# ☸️ **PASSO A PASSO KUBERNETES COM DESCRIÇÕES**

```bash
# 1. Verifica conexão com o cluster
kubectl cluster-info

# 2. Lista todos os nós do cluster
kubectl get nodes

# 3. Cria um namespace para a aplicação
kubectl create namespace minha-aplicacao

# 4. Verifica namespaces existentes
kubectl get namespaces

# 5. Cria um deployment básico
kubectl create deployment nginx --image=nginx:1.21 -n minha-aplicacao

# 6. Lista deployments no namespace
kubectl get deployments -n minha-aplicacao

# 7. Lista pods criados
kubectl get pods -n minha-aplicacao

# 8. Expõe o deployment como serviço
kubectl expose deployment nginx --port=80 --type=NodePort -n minha-aplicacao

# 9. Lista serviços
kubectl get services -n minha-aplicacao

# 10. Verifica detalhes do serviço
kubectl describe service nginx -n minha-aplicacao

# 11. Aumenta o número de réplicas
kubectl scale deployment nginx --replicas=3 -n minha-aplicacao

# 12. Verifica pods escalados
kubectl get pods -n minha-aplicacao

# 13. Acessa logs de um pod específico
kubectl logs -f <pod-name> -n minha-aplicacao

# 14. Executa comando dentro do pod
kubectl exec -it <pod-name> -n minha-aplicacao -- /bin/bash

# 15. Verifica status do rollout
kubectl rollout status deployment/nginx -n minha-aplicacao

# 16. Atualiza a imagem do deployment
kubectl set image deployment/nginx nginx=nginx:1.22 -n minha-aplicacao

# 17. Monitora a atualização
kubectl rollout status deployment/nginx -n minha-aplicacao

# 18. Verifica histórico de rollouts
kubectl rollout history deployment/nginx -n minha-aplicacao

# 19. Faz port-forward para acesso local
kubectl port-forward service/nginx 8080:80 -n minha-aplicacao

# 20. Verifica todos os recursos no namespace
kubectl get all -n minha-aplicacao
```

# ☸️ **FLUXO COMPLETO KUBERNETES - DESENVOLVIMENTO À PRODUÇÃO**

## 🚀 **FLUXO INTEGRADO PASSO A PASSO**

```bash
# 1. 🏗️ PREPARAÇÃO DO AMBIENTE
kubectl create namespace desenvolvimento
kubectl create namespace staging
kubectl create namespace producao

# 2. 🔧 DESENVOLVIMENTO (Namespace de dev)
kubectl apply -f deployment-dev.yaml -n desenvolvimento
kubectl apply -f service-dev.yaml -n desenvolvimento

# 3. 📊 MONITORAMENTO DESENVOLVIMENTO
kubectl get all -n desenvolvimento
kubectl logs -f deployment/app-dev -n desenvolvimento
kubectl port-forward svc/app-dev 8080:80 -n desenvolvimento

# 4. 🧪 TESTES NO STAGING
kubectl apply -f deployment-staging.yaml -n staging
kubectl apply -f service-staging.yaml -n staging

# 5. ✅ VALIDAÇÃO STAGING
kubectl get pods -n staging
kubectl describe deployment app-staging -n staging
kubectl logs deployment/app-staging -n staging

# 6. 🚀 DEPLOY EM PRODUÇÃO (Blue-Green)
# Deploy da versão nova (green)
kubectl apply -f deployment-prod-green.yaml -n producao

# 7. 🔄 TESTE PRODUÇÃO GREEN
kubectl get pods -l version=green -n producao
kubectl port-forward svc/app-green 8081:80 -n producao

# 8. 🔀 TROCA DE TRAFFIC (Switch)
kubectl patch service app-main -n producao -p '{"spec":{"selector":{"version":"green"}}}'

# 9. 📈 MONITORAMENTO PRODUÇÃO
kubectl top pods -n producao
kubectl get hpa -n producao
kubectl describe ingress app-ingress -n producao

# 10. 🗂️ CONFIGURAÇÕES E SECRETS
kubectl create configmap app-config --from-file=config/ -n producao
kubectl create secret generic db-secret --from-literal=password=senha123 -n producao

# 11. 💾 STORAGE PERSISTENTE
kubectl apply -f pvc.yaml -n producao
kubectl get pvc -n producao

# 12. 🔍 DEBUG E TROUBLESHOOTING
kubectl describe pods -l app=myapp -n producao
kubectl get events --sort-by=.metadata.creationTimestamp -n producao
kubectl exec -it <pod-name> -n producao -- /bin/bash

# 13. 🔄 ATUALIZAÇÃO CONTÍNUA
kubectl set image deployment/app-green app=minha-app:v2.0 -n producao
kubectl rollout status deployment/app-green -n producao

# 14. 🚨 ROLLBACK EM CASO DE PROBLEMAS
kubectl rollout undo deployment/app-green -n producao
kubectl rollout history deployment/app-green -n producao

# 15. 🧹 LIMPEZA E MANUTENÇÃO
kubectl delete pods --field-selector=status.phase==Failed -n producao
kubectl get jobs -n producao
kubectl delete completed jobs -n producao
```

## 🔄 **FLUXO SIMPLIFICADO PARA USO DIÁRIO**

```bash
# 1. Desenvolvimento rápido
kubectl create deployment myapp --image=myapp:latest --namespace=dev
kubectl expose deployment myapp --port=80 --type=NodePort --namespace=dev

# 2. Teste local
kubectl port-forward svc/myapp 8080:80 --namespace=dev

# 3. Deploy para produção
kubectl apply -f k8s/production/ --namespace=production

# 4. Verificação
kubectl get all --namespace=production
kubectl rollout status deployment/myapp --namespace=production

# 5. Monitoramento
kubectl logs -f deployment/myapp --namespace=production
kubectl top pods --namespace=production
```

## 📋 **COMANDOS DE VERIFICAÇÃO DO FLUXO**

```bash
# Verificar saúde do cluster
kubectl get componentstatuses
kubectl get nodes

# Verificar recursos por namespace
kubectl get all --namespace=development
kubectl get all --namespace=staging
kubectl get all --namespace=production

# Verificar configurações
kubectl get configmaps --namespace=production
kubectl get secrets --namespace=production

# Verificar storage
kubectl get pvc --namespace=production
kubectl get pv

# Verificar networking
kubectl get services --namespace=production
kubectl get ingress --namespace=production

# Verificar autoscaling
kubectl get hpa --namespace=production
```

## ⚠️ **COMANDOS DE EMERGÊNCIA**

```bash
# Drenar nó para manutenção
kubectl drain <node-name> --ignore-daemonsets --delete-emptydir-data

# Cordinar nó novamente
kubectl uncordon <node-name>

# Remover pod problemático
kubectl delete pod <pod-name> --force --grace-period=0

# Rollback rápido
kubectl rollout undo deployment/<deployment-name>

# Parar tudo em um namespace
kubectl delete all --all --namespace=emergency

# Recriar recursos
kubectl apply -f k8s/ --namespace=production
```

## 📊 **COMANDOS DE MONITORAMENTO AVANÇADO**

```bash
# Monitorar recursos em tempo real
kubectl get pods --watch --namespace=production
kubectl get events --watch --namespace=production

# Métricas de performance
kubectl top nodes
kubectl top pods --namespace=production
kubectl top pods --containers --namespace=production

# Logs agregados
kubectl logs -l app=myapp --namespace=production --tail=100
kubectl logs -l app=myapp --namespace=production --since=1h

# Verificar quotas
kubectl describe resourcequota --namespace=production

# Verificar limites
kubectl describe limitrange --namespace=production
```

**Este fluxo cobre desde o desenvolvimento até a produção com estratégias de deploy avançadas!** ☸️🚀

---

💡 **Dica:** Sempre teste comandos de modificação com `--dry-run=client -o yaml` primeiro
📌 **Nota:** Use `kubectl explain <recurso>` para documentação detalhada de cada recurso
🔒 **Segurança:** Revise sempre as permissões RBAC antes de implementar em produção
