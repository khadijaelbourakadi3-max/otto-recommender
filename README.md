# OTTO – Recommandation multi-objectifs

Prédire, pour chaque session e-commerce, les prochains **clics**, **ajouts au panier**
et **commandes** (compétition Kaggle OTTO).

- **Données** : [Kaggle OTTO](https://www.kaggle.com/competitions/otto-recommender-system)
  (non incluses). Échantillon : 50 000 sessions (40 000 pour construire, 10 000 pour valider).
- **Métrique** : score = 0.10·R_clicks + 0.30·R_carts + 0.60·R_orders (Recall@20).
- **Méthode** : produits de la session classés par type et récence, complétés par
  les voisins d'une matrice de co-visitation (co-visitation v2).

## Résultats (validation locale)
| Modèle | Score |
|---|---|
| Popularité | 0.012 |
| Derniers produits vus | 0.270 |
| Co-visitation v1 (mélange) | 0.233 |
| **Co-visitation v2** | **0.298** |

## Conclusion
Le signal le plus fort vient de la session elle-même. Hiérarchiser les produits
de la session avant les voisins améliore le score (v1 → v2).
Limites : validation simplifiée (session coupée au milieu), petit échantillon.

## Fichiers
- `otto_covisitation.ipynb` : code complet
- `requirements.txt` : bibliothèques
