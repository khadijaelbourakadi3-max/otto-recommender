# OTTO – Recommandation multi-objectifs

Prédire, pour chaque session e-commerce, les prochains **clics**, **ajouts au panier**
et **commandes** (compétition Kaggle OTTO).

- **Données** : [Kaggle OTTO](https://www.kaggle.com/competitions/otto-recommender-system) (non incluses).
- **Métrique** : score = 0.10·R_clicks + 0.30·R_carts + 0.60·R_orders (Recall@20).
- **Méthode** : candidats = produits de la session + voisins d'une matrice de
  co-visitation (3 M de sessions), classés par LightGBM (un modèle par type).
- **Validation** : 20 000 sessions coupées à un point pseudo-aléatoire (locale, non
  comparable au classement Kaggle).

## Résultats (validation locale)
| Modèle | Clicks | Carts | Orders | Score |
|---|---|---|---|---|
| Popularité | 0.0082 | 0.0085 | 0.0072 | 0.0077 |
| Derniers produits vus | 0.3980 | 0.1481 | 0.2867 | 0.2562 |
| Co-visitation (heuristique) | 0.3993 | 0.1544 | 0.3107 | 0.2727 |
| **Co-visitation + LightGBM** | **0.4129** | **0.1573** | **0.3171** | **0.2787** |

## Analyse
- Les produits déjà vus dans la session sont le signal principal.
- Les voisins de co-visitation ajoutent +0.017, LightGBM +0.006.
- Le recall maximal des candidats est de 0.18 (carts) et 0.34 (orders) : le score
  est limité par la génération de candidats, pas par le classement.


## Fichiers
- `otto_covisitation.ipynb` : code complet
- `requirements.txt` : bibliothèques
