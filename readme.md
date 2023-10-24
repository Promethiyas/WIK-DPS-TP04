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