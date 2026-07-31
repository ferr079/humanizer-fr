# humanizer-fr

Skill [Claude Code](https://docs.claude.com/en/docs/claude-code) (compatible OpenCode) qui **retire les marques d'écriture IA d'un texte en français**. On lui donne un texte — collé directement ou via un chemin de fichier — et il repère puis corrige les tournures qui « sentent » le modèle de langage, pour que le rendu sonne humain.

C'est un **fork francisé** de [`blader/humanizer`](https://github.com/blader/humanizer) (MIT, ~32k ⭐). L'original cible l'anglais ; cette adaptation réécrit la table des motifs pour le **français** : tics typographiques inversés (les guillemets « … » sont la norme ici, pas un défaut), anglicismes calqués, et formules de remplissage propres aux LLM francophones.

## Attribution

> Fork français de **[blader/humanizer](https://github.com/blader/humanizer)** (MIT, © 2025 Siqi Chen).
> Adaptation FR © 2026 Stéphane Ferreira. Sous licence MIT — voir [`LICENSE`](./LICENSE).

Les deux skills s'appuient sur le guide Wikipédia [« Signs of AI writing »](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing).

Le dépôt séparé n'est pas un contournement : la question a été posée en amont ([blader/humanizer#163](https://github.com/blader/humanizer/issues/163)) et le mainteneur a tranché pour des **dépôts communautaires par langue** — chaque locale évolue ainsi à son rythme, sans empiler d'autorités concurrentes dans le skill d'origine.

## Ce qui change par rapport à l'original

- **Table des 33 motifs réécrite pour le français** (pas une traduction littérale, une adaptation), réparties dans les 5 catégories d'origine.
- **Tics typographiques inversés** : en français, les guillemets « » avec espaces insécables sont la norme — le tic devient l'usage de guillemets droits `"…"` ou anglais `"…"`. Idem pour la capitalisation à l'anglaise (Title Case, qui n'existe pas en français) et l'abus du tiret cadratin à l'anglaise.
- **Motifs ajoutés, propres aux LLM francophones** : « Il est important de noter que », « Il convient de souligner que », « En tant que modèle de langage… », « À l'ère de… / Dans un monde où… », abus des connecteurs (« notamment », « par ailleurs », « en effet »), « mettre en lumière », « s'inscrire dans une démarche », anglicismes (« adresser un problème », « supporter » au lieu de « prendre en charge »), « N'hésitez pas à… ».
- **Mécanisme de calibrage de la voix conservé** (il est déjà indépendant de la langue) : on fournit un échantillon de sa propre écriture et le skill aligne le résultat sur ce style.

## Sans risque par conception

Le skill est **uniquement déclaratif** (prompt-only) : il ne contient et n'exécute **aucun code**. Il lit, propose des réécritures et applique des éditions de texte. Rien d'autre.

## Invocation

Dans Claude Code, le skill se déclenche quand on demande d'« humaniser », de « retirer le ton IA » ou de « rendre plus naturel » un texte français. Exemples :

```
Humanise ce brouillon : <texte collé>

Relis cet article et enlève le ton IA : ./brouillons/mon-article.md

Réécris ce paragraphe pour qu'il sonne comme moi. Mon échantillon de
référence : ./echantillons/ma-voix.md
```

Pour le calibrage de la voix, un bon échantillon de référence est un texte que vous avez réellement écrit — par exemple un billet du blog [Pixelium](https://blog.pixelium.win).

## Installation

Placer le dossier dans le répertoire des skills de Claude Code :

```
~/.claude/skills/humanizer-fr/SKILL.md
```

(ou le répertoire `.claude/skills/` d'un projet). Le fichier `SKILL.md` se suffit à lui-même.

## Licence

MIT. L'avis de copyright original (Siqi Chen) est conservé dans [`LICENSE`](./LICENSE), comme l'exige la licence MIT pour toute œuvre dérivée.
