# Journal des modifications

## 2.0.0

Rebasée sur `blader/humanizer` v3.1.0 (la 1.0.0 partait de la v2.8.0).

- Les motifs suivent la structure et la numérotation de l'original : 26 motifs en six sections (A à F), classés du plus fort au plus faible, plus une section G propre au français (§27 à §29). 29 motifs au total, contre 33 ; aucun n'est perdu, plusieurs sont fusionnés.
- Six motifs nouveaux : contredire un adversaire absent (§5), débuts de phrase répétés (§7), association vague (§14), titre répété dans la première phrase (§24), parler du document au lieu de son sujet (§25), réexpliquer ce que le lecteur sait (§26).
- Motif retiré : la variation élégante (synonymie forcée). Wikipédia la classe désormais comme une habitude humaine, et l'original l'a retirée.
- Le §10 de l'original (traits d'union des adjectifs composés anglais) n'a pas d'équivalent en français ; son numéro est gardé pour la correspondance.
- Les exemples « Après » ne contiennent plus que des faits présents dans le « Avant ». Plusieurs exemples de la 1.0.0 inventaient un chiffre, une source ou une raison, à l'inverse de la règle qu'ils illustraient.
- Nouvelle ouverture : pourquoi un texte IA sonne IA, et les deux règles qui en découlent. Méthode en quatre étapes, avec une vérification que la réécriture n'a ni ajouté ni perdu de fait. Modes texte collé, fichier et intégré. Section « Quand ne pas agir », et motifs marqués *faible seul* quand une occurrence isolée ne suffit pas.
- Tirets (§8) : alignés sur l'original. Aucun tiret cadratin dans la version finale, sauf si l'échantillon de l'auteur en emploie. L'incise entre tirets espacés est correcte en typographie française, mais c'est l'outil que les modèles prennent par défaut.
- Guillemets droits (§21) : marqués *faible seul*, beaucoup de claviers en produisent.
- Frontmatter : `version`, `based-on` et `upstream` rangés sous `metadata:`, comme dans l'original.
- Packaging : manifestes `.claude-plugin/` pour l'installation comme plugin Claude Code.
- La référence personnelle à un échantillon de voix a été retirée du skill.

## 1.0.0

Première adaptation française de `blader/humanizer` v2.8.0 : 33 motifs en cinq catégories, typographie refaite pour le français, motifs propres aux modèles francophones.
