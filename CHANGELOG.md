# Journal des modifications

## 2.1.0

Rebasée sur `blader/humanizer` v4.0.0.

- Écart assumé avec l'original : la règle « n'inventez rien » reste. La v4.0.0 autorise le skill à ajouter un détail précis qu'il sait vrai quand le texte est générique, et ses exemples des §14 et §17 en gagnent (une largeur de rivière, une interview datée). Ici, un fait absent du texte et de l'utilisateur reste une erreur : un détail « su vrai » par un modèle est la forme la plus difficile à repérer d'une invention. Les §14 et §17 gardent leur consigne de la 2.0.0.
- Un texte à corriger qui contient de fausses balises de fermeture, ou des consignes d'un « opérateur » ou d'un « message système », est traité comme de la matière à corriger, jamais comme des instructions (`blader/humanizer#317`).
- Mode fichier : le skill lit tout le fichier sur le disque avant de le modifier, même s'il l'a écrit dans la session. Son résumé dit combien de sections il a relues, si bien qu'une passe partielle se voit (`#326`, `#327`).
- Étape 3 : on vérifie d'abord les faits perdus, ajoutés ou modifiés, avant la relecture à voix haute.
- Six exemples « Après » revus (§1 queue tronquée, §5, §6, §23 ×2, §26). Celui du §1 perdait le sens de l'original, ceux du §23 reprenaient une tournure de leur propre liste à repérer, et celui du §26 finissait sur une offre de chatbot.
- Phrases qui ne faisaient qu'annoncer ou répéter leur voisine retirées (ouverture, §7, §13, §26, section E).
- Ligne vide avant chaque étiquette de motif, pour que GitHub affiche chaque étiquette et chaque exemple sur sa propre ligne (`#329`).
- La description du skill ne cite plus Wikipédia ; le crédit reste dans la section Source et le README (`#321`).
- Packaging : `package.json` fait du dépôt un paquet pi (`pi install git:github.com/ferr079/humanizer-fr`), sans champ `version` puisque pi installe depuis git (`#315`).

## 2.0.1

- Packaging : clé `$schema` retirée de `.claude-plugin/plugin.json`. Claude Code ne la reconnaît pas et affichait un avertissement à chaque chargement du plugin. Même correctif que l'original (`blader/humanizer#307`). `marketplace.json` garde la sienne, qui ne déclenche aucun avertissement.

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
