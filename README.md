# Oh Ce Cours - Notebooks

Notebooks Jupyter pour le blog [Oh Ce Cours](https://ohcecours.fr).

## Lancer un notebook

[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/ohcecours/notebooks/main)

Cliquez sur le badge ci-dessus pour lancer l'environnement Binder, puis naviguez vers le notebook de votre choix.

## Structure

```
notebooks/
├── requirements.txt          # Dépendances pour Binder
└── articles/
    └── mon-article/
        ├── notebook.ipynb    # Le notebook
        ├── requirements.txt  # Dépendances spécifiques (optionnel)
        └── data/             # Données associées (optionnel)
```

## Créer un nouvel article

1. Créer un dossier dans `articles/` avec un nom en kebab-case
2. Créer le notebook `notebook.ipynb`
3. Ajouter les métadonnées Oh Ce Cours dans le notebook

### Métadonnées requises

Dans le notebook, section `metadata` :

```json
{
  "metadata": {
    "ohcecours": {
      "title": "Titre de l'article",
      "slug": "mon-article",
      "description": "Description courte pour le SEO",
      "author": "prenom",
      "tags": ["python", "tag2"],
      "difficulty": "débutant|intermédiaire|avancé",
      "duration_minutes": 30,
      "published": true
    }
  }
}
```

### Insérer des CTAs

Dans une cellule Markdown, ajoutez un commentaire HTML :

```markdown
<!-- ohcecours:cta type="formation" slug="python-clean-code" -->
<!-- ohcecours:cta type="academie" slug="python-avance" -->
<!-- ohcecours:cta type="expertise" -->
<!-- ohcecours:cta type="newsletter" -->
```

Ces commentaires seront remplacés par des blocs CTA lors du rendu sur le site.

## Synchronisation avec le site

Les notebooks sont automatiquement synchronisés avec le site Wagtail via :

```bash
python manage.py sync_notebooks
```
