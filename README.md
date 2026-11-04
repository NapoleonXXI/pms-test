# PMS test — version web minimaliste

- `index.html` : la page (reproduction de la page Canvas minimaliste validée).
- `tree.json` : le contenu (idées et sous-idées). Champs : `id` (stable), `label`, `kids`, et en option `note`, `tag`, `sugg` (suggestion de l'IA, cadre en pointillés), `etat` (`retenu`, `explore`, `impasse`), `actuel`, `discret`.

## Comment l'IA met à jour le contenu
1. Modifier `tree.json` en gardant les `id` existants.
2. `git commit -am "maj arbre"` puis `git push` sur `main`.
3. GitHub Pages redéploie le site. La page relit `tree.json` toutes les 3 s (`cache: 'no-store'` + `?t=`) et se met à jour sans rechargement. La sélection est conservée si l'idée existe encore, sinon on remonte au parent existant le plus proche.

Si `tree.json` est inaccessible, la page utilise sa copie de secours intégrée.
Les modifications faites dans la page (renommer, ajouter…) restent locales et sont remplacées à la prochaine mise à jour de `tree.json`.
