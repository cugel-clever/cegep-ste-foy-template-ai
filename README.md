Ateliers, programme *Spécialiste en solutions d'intelligence artificielle*.

## Organisation du dépôt

| Répertoire | Contenu |
|---|---|
| `docker/` | Image de l'environnement de travail |
| `.devcontainer/` | Configuration Dev Container (VS Code) |

## Environnement de travail

Python 3.13 ; les versions des bibliothèques sont épinglées dans
[docker/requirements.txt](docker/requirements.txt).

### Avec VS Code (recommandé)

Ouvrir le dépôt dans VS Code, puis **Reopen in Container** : le Dev Container construit l'image
et installe les extensions Python / Jupyter.

### Avec Docker seul

Depuis la racine du dépôt :

```bash
docker build -t 420-c74-sf docker/
docker run --rm -it -p 8888:8888 -v $(pwd):/notebooks 420-c74-sf
```

Puis ouvrir http://localhost:8888. Voir [docker/README.md](docker/README.md) pour les détails.
