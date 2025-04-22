# TP Kubernetes – Déployer une application Nginx avec contenu persistant

## 🎯 Objectif
Déployer une application Nginx sur Kubernetes avec :
- Une page HTML personnalisée injectée via ConfigMap
- Un volume persistant pour conserver le contenu
- Un Service pour l'exposer dans le cluster
- (Optionnel) un Ingress pour l'accès externe

## 🧱 Structure des fichiers

- `index.html` : contenu personnalisé de la page d'accueil
- `k8s/configmap.yaml` : ConfigMap contenant la page HTML
- `k8s/persistentvolume.yaml` : volume statique (à adapter selon votre environnement)
- `k8s/persistentvolumeclaim.yaml` : PVC utilisé par le Pod
- `k8s/deployment.yaml` : déploiement de Nginx
- `k8s/service.yaml` : service de type ClusterIP
- `k8s/ingress.yaml` : Ingress optionnel

## 🚀 Déploiement

```bash
kubectl apply -f k8s/
```

## 🌐 Accès

- Depuis le cluster : `kubectl port-forward svc/nginx 8080:80`
- Depuis l’extérieur : `http://nginx.local` (si Ingress activé + DNS local configuré)

## 🧪 Test

```bash
curl http://localhost:8080
```

## 📚 Pour aller plus loin

- Ajoutez un `HorizontalPodAutoscaler`
- Passez à un volume dynamique (sans PV statique)
- Ajoutez un probe (liveness/readiness)
