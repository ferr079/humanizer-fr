# humanizer-fr

Skill [Claude Code](https://docs.claude.com/en/docs/claude-code) (compatible OpenCode) qui **retire les marques d'écriture IA d'un texte en français**, sans changer ce qu'il dit. On lui donne un texte, collé ou par un chemin de fichier ; il repère les tournures typiques des modèles de langage et réécrit pour que le texte se lise comme son auteur.

Ce n'est pas un outil pour tromper les détecteurs d'IA. Le but est un texte que l'on a envie de lire.

## Exemple

**Avant :**
> À l'ère du numérique, il est important de noter que l'auto-hébergement s'impose comme une solution robuste et incontournable. Ce homelab, qui fait tourner une cinquantaine de conteneurs sur quatre machines, ne se contente pas d'héberger des services : il incarne une véritable philosophie. Par ailleurs, il met en lumière un savoir-faire certain. En conclusion, n'hésitez pas à explorer cette approche révolutionnaire ! 🚀

**Après :**
> Ce homelab fait tourner une cinquantaine de conteneurs sur quatre machines.

Le seul fait du texte d'origine est resté, et rien n'a été ajouté. Le reste était de l'emballage : l'ouverture « À l'ère de » et l'amorce « il est important de noter » (§4), « s'impose comme » (§18), les mots-béquilles (§12), « ne se contente pas de… il incarne » (§1), l'essence prêtée au projet (§3), « met en lumière » (§29), « Par ailleurs » (§27), « En conclusion » (§2), « n'hésitez pas » et l'emoji (§20, §22).

## Les signes les plus forts

1. **Pas X mais Y** : « Ce n'est pas seulement un outil, c'est une philosophie. »
2. **Chutes en une ligne** : « Tout est dit. », « C'est toute la différence. »
3. **Maximes creuses** : « Au fond, la vraie question est celle de la confiance. »
4. **Amorces** : « Il est important de noter que », « Sans plus attendre ».
5. **Adversaire absent** : « Entendons-nous bien, je ne dis pas que… »

Le skill en compte 29, en sept sections. Les numéros 1 à 26 suivent ceux de l'original anglais ; la section G (§27 à §29) regroupe les tics propres au français : connecteurs en surnombre, anglicismes calqués, verbes et formules vides.

## Ce qui change par rapport à l'original

C'est une adaptation, pas une traduction. Les exemples sont réécrits en français, et la typographie est refaite :

- **Guillemets** : en français, « » avec espaces insécables est la norme. Les guillemets droits ou anglais sont le signe à repérer, à l'inverse de l'anglais.
- **Majuscules** : le Title Case n'existe pas en français ; seuls la première lettre d'un titre et les noms propres prennent la majuscule.
- **Tirets** : l'incise entre tirets espacés est correcte en français, mais le skill suit la règle de l'original et n'en laisse aucun, sauf si votre propre écriture en contient.

Le skill est rebasé sur `blader/humanizer` v3.1.0. Le détail des versions est dans [`CHANGELOG.md`](./CHANGELOG.md).

## Installation

**Comme plugin Claude Code :**

```
/plugin marketplace add ferr079/humanizer-fr
/plugin install humanizer-fr@humanizer-fr
```

**À la main :** copier `SKILL.md` dans `~/.claude/skills/humanizer-fr/` (ou dans le `.claude/skills/` d'un projet). Le fichier se suffit à lui-même.

## Utilisation

Le skill se déclenche quand on demande d'« humaniser » un texte français, de « retirer le ton IA » ou de le « rendre plus naturel » :

```
Humanise ce brouillon : <texte collé>

Relis cet article et enlève le ton IA : ./brouillons/mon-article.md

Réécris ce paragraphe pour qu'il sonne comme moi. Mon échantillon de
référence : ./echantillons/ma-voix.md
```

Avec un échantillon de votre écriture (un billet, un courriel soigné, une note), le skill aligne le résultat sur votre style plutôt que sur un français neutre. Sur un fichier, il ne modifie que la prose : le code, les commandes, les chemins et les métadonnées restent intacts.

## Sans risque par conception

Le skill est uniquement déclaratif : il ne contient et n'exécute aucun code. Il lit, propose des réécritures et applique des modifications de texte.

## Attribution

> Fork français de **[blader/humanizer](https://github.com/blader/humanizer)** (MIT, © 2025 Siqi Chen).
> Adaptation française © 2026 Stéphane Ferreira. Sous licence MIT, voir [`LICENSE`](./LICENSE).

Les deux skills s'appuient sur le guide Wikipédia [« Signs of AI writing »](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing).

Le dépôt séparé n'est pas un contournement. La question a été posée à l'original ([blader/humanizer#163](https://github.com/blader/humanizer/issues/163)), et le mainteneur a choisi des dépôts communautaires par langue : chaque langue évolue à son rythme, sans multiplier les versions concurrentes dans le skill d'origine.

## Licence

MIT. L'avis de copyright original (Siqi Chen) est conservé dans [`LICENSE`](./LICENSE), comme l'exige la licence MIT pour toute œuvre dérivée.
