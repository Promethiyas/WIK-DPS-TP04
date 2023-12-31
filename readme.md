# WIK-DPS-TP04
WIK-DPS-TP04 est le quatrième TP devops à rendre. 

## Lancement du projet 

```bash
git clone https://github.com/Promethiyas/WIK-DPS-TP04.git
```

Deplacez vous dans le dossier ***\WIK-DPS-TP04***

### Créer un pod

Pour cette partie il faut utiliser le fichier ***part1.yaml***.

On va créer le namespace:

```bash
kubectl create my-namescpace 
```

Puis créer le pods:

```bash
kubectl create -f part1.yaml 
```

Et on fait le port-forwarding:

```bash
kubectl port-forward -n my-namescpace tp04-1 8080:8080
```

### Remplacer pod par un ReplicaSet

Pour cette partie il faut utliser ***part2.yaml***.

On a juste à faire:

```bash
kubectl create -f part2.yaml
```

pour créer les replicas.
Pour les afficher:

```bash
kubectl get rs
```

Pour voir plus d'informations:
```bash
kubectl describe rs/tp04-2
```

### Remplacer le ReplicaSet par un Deployement

Pour cette partie il faut utiliser ***part3.yaml.

On lance le deploiement avec:

```bash
kubectl apply -f  part3.yaml
```

Puis:

```bash
kubectl get deploy -n my-namescpace
```


### Créer un service

Pour cette partie il faut utiliser ***part4.yaml***.

Pour lancer le service il faut d'abord avoir le deploiement de lancer, donc:

```bash
kubectl create -f part3.yaml
```

Puis on lance le service:

```bash
kubectl create -f part4.yaml
```

Une fois fait on peut faire du `port-forwarding` pour verifier:

```bash
kubectl port-forward services/tp04-4 -n my-namescpace  3030:80
```

Et on peut accéder au [localhost](http://localhost:3030/ping).


### Ingress

Pour cette partie il faut utiliser ***part5.yaml***.

Pour lancer le service il faut d'abord avoir lancer:

```bash
kubectl create -f part3.yaml
```
```bash
kubectl create -f part4.yaml
```

Puis:
```bash
kubectl create -f part5.yaml
```

On lance:

```bash
minikube tunnel
```

On doit avoir modifier `/etc/host` en ajoutant ***tp04-5.info*** à localhost.

Et voilà:

<img src="https://cdn.discordapp.com/attachments/905799668938723329/1166381922478461090/image.png?ex=654a48d0&is=6537d3d0&hm=ec9cba173dd8bc1e630c2103b2a5c15b9a2f26d2be207b1e1e60b3064ce26a00&"/>
