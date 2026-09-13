# Image Docker (JupyterLab)

Environnement des ateliers IA
(Python 3.13, versions des bibliothèques épinglées dans `requirements.txt`).

### Création de l'image à partir du Dockerfile
`docker build -t <nom_image> .`

#### Exemple:
`docker build -t 420-c74-sf .`

### Exécution sur Linux / macOS
`docker run --rm -it -p 8888:8888 -v $(pwd):/notebooks --name <nom_du_conteneur> <nom_image>`

### Exécution sur Powershell
`docker run --rm -it -p 8888:8888 -v ${PWD}:/notebooks --name <nom_du_conteneur> <nom_image>`

La commande doit être lancée depuis la **racine du dépôt** (et non depuis `docker/`), afin que
`data/` soit visible depuis les notebooks, qui la référencent par `../../data/`.

L'interface est ensuite accessible sur http://localhost:8888 (aucun jeton n'est demandé).
