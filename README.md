# OTTO – Recommandation multi-objectifs

Prédire, pour chaque session e-commerce, les prochains **clics**, **ajouts au panier**
et **commandes** (compétition Kaggle OTTO).

- **Données** : [Kaggle OTTO](https://www.kaggle.com/competitions/otto-recommender-system).
- **Métrique** : score = 0.10·R_clicks + 0.30·R_carts + 0.60·R_orders (Recall@20).
- **Méthode** : candidats = produits de la session + voisins d'une matrice de
  co-visitation construite sur ≈ 12,7 M de sessions, re-ranking par LightGBM.

## Résultats
| Évaluation | Score |
|---|---|
| **Kaggle (public / privé)** | **0.57054 / 0.57017** |
| Validation locale (20 000 sessions, coupure pseudo-aléatoire) | 0.2827 |

La validation locale sert à comparer les modèles entre eux ; elle est plus dure que
le test officiel et ne s'y compare pas.

## Fichiers
- `otto_covisitation.ipynb` : code complet et sorties
- `requirements.txt` : bibliothèques
