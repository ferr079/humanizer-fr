---
name: humanizer-fr
version: 1.0.0
description: |
  Supprime les marques d'écriture IA dans un texte français. À utiliser pour relire ou
  réécrire du texte afin qu'il sonne humain. Adaptation française du skill « humanizer »
  de blader/humanizer, fondée sur le guide Wikipédia « Signs of AI writing ». Repère et
  corrige l'inflation de portée, le langage promotionnel, les attributions vagues, la
  voix passive, la règle de trois, le parallélisme négatif, les anglicismes calqués, les
  tics typographiques (guillemets droits, capitalisation à l'anglaise, abus du tiret
  cadratin) et les formules de remplissage propres au français.
license: MIT
based-on: blader/humanizer v2.8.0 (MIT, © 2025 Siqi Chen)
upstream: https://github.com/blader/humanizer
compatibility: claude-code opencode
allowed-tools:
  - Read
  - Write
  - Edit
  - Grep
  - Glob
  - AskUserQuestion
---

# Humanizer FR — retirer les marques d'écriture IA

Ce skill réécrit un texte français pour qu'il cesse de sonner « machine ». Il ne
cherche pas à tromper un détecteur : il enlève les tournures creuses, les formules
toutes faites et les tics que les modèles de langage produisent en masse, pour
rendre le texte au style de son auteur.

Adaptation française de `blader/humanizer` (MIT). L'original vise l'anglais ; ici la
table des motifs est refaite pour le français — en particulier la typographie, où
plusieurs « défauts » anglais sont au contraire la norme (les guillemets « » par
exemple), et l'inverse.

## Votre tâche

On vous donne un texte (collé directement, ou via un chemin de fichier à lire). Vous
devez :

1. Le lire en entier avant de toucher quoi que ce soit.
2. Si un échantillon de la voix de l'auteur est fourni, le calibrer d'abord (voir
   ci-dessous).
3. Repérer les motifs listés plus bas, catégorie par catégorie.
4. Réécrire en gardant le sens, les faits et la personnalité — sans aplatir.
5. Montrer le avant / après, puis appliquer les éditions.

Vous corrigez le style, pas le fond. Vous ne supprimez aucune information vraie, vous
n'inventez rien, vous ne « rallongez » jamais pour faire sérieux.

## Calibrage de la voix (optionnel)

Ce mécanisme est indépendant de la langue : il fonctionne pour n'importe quel texte
d'auteur.

Si l'utilisateur fournit un échantillon de sa propre écriture — collé dans la
conversation, ou désigné par un chemin de fichier à lire avec `Read` — analysez-le
avant de réécrire, sur ces axes :

- **Longueur et rythme des phrases** : courtes et sèches ? longues et articulées ? un
  mélange ?
- **Vocabulaire** : registre courant ou technique, mots de prédilection, niveau de
  familiarité.
- **Ouvertures de paragraphe** : entre direct dans le sujet, ou met en contexte ?
- **Ponctuation** : usage des deux-points, des parenthèses, des tirets, des points de
  suspension.
- **Tics personnels** : tournures, images, ironie, manière de trancher ou de nuancer.

Alignez ensuite la réécriture sur ce profil plutôt que sur un « bon français » neutre.
Le but n'est pas un style générique propre, c'est *ce* style-là, débarrassé du bruit IA.

> Bon échantillon de référence : un texte réellement écrit par l'auteur — un billet de
> blog, un courriel soigné, une note. Pour Stéphane : ses billets du blog Pixelium
> (`blog.pixelium.win`) font une référence fiable.

Sans échantillon, visez un français naturel, concret et direct, et appliquez la table
ci-dessous.

## PERSONNALITÉ ET ÂME

Humaniser ne veut pas dire lisser. Le piège, en retirant les tics IA, est de produire
un texte correct mais mort. Préservez (ou rendez) au texte :

- les **opinions tranchées** et les partis pris assumés ;
- les **détails concrets** et chiffrés, qui ancrent le propos ;
- l'**humour**, l'ironie, les images personnelles ;
- les **imperfections vivantes** : une phrase courte qui claque, une digression
  assumée, une répétition voulue.

Un texte humain a une voix. Si après réécriture il pourrait avoir été écrit par
n'importe qui, le travail n'est pas fini.

---

## MOTIFS DE CONTENU

### 1. Inflation de portée et de notabilité
**Signe :** présenter une chose ordinaire comme majeure, révolutionnaire, incontournable.
**Avant :** « Ce script s'impose comme une solution révolutionnaire qui redéfinit les standards de la sauvegarde. »
**Après :** « Ce script sauvegarde le serveur PBS chaque nuit. »

### 2. Langage promotionnel
**Signe :** vocabulaire de brochure commerciale plaqué sur du factuel.
**Avant :** « Une expérience fluide et sans précédent, pensée pour offrir le meilleur à ses utilisateurs. »
**Après :** « L'interface tient sur une page et se charge en moins d'une seconde. »

### 3. Fausse profondeur en participe présent
**Signe :** une proposition en « -ant » ajoutée en fin de phrase pour simuler de l'analyse.
**Avant :** « Le projet repose sur Astro, témoignant d'une recherche de performance et illustrant l'adoption des meilleures pratiques. »
**Après :** « Le projet utilise Astro, parce que le site est statique et doit se charger vite. »

### 4. Attributions vagues
**Signe :** « beaucoup pensent », « il est largement reconnu », « les experts s'accordent » — sans source.
**Avant :** « Il est largement reconnu que cette approche est la meilleure. »
**Après :** « La documentation officielle de Docker recommande cette approche. »

### 5. Éditorialisation injectée
**Signe :** des jugements glissés dans un texte censé être descriptif (« fait remarquable », « de façon impressionnante »).
**Avant :** « Fait notable, le serveur tourne en continu depuis deux ans, ce qui est tout simplement impressionnant. »
**Après :** « Le serveur tourne sans interruption depuis deux ans. »

### 6. Symbolisme gonflé
**Signe :** prêter un sens profond ou une « essence » à un choix anodin.
**Avant :** « Ce choix de couleur incarne l'essence même de la philosophie du projet. »
**Après :** « Le fond est bleu nuit pour réduire la fatigue visuelle. »

---

## MOTIFS DE LANGUE ET DE GRAMMAIRE

### 7. Vocabulaire « IA » récurrent
**Signe :** les mots-béquilles des modèles : robuste, riche, transparent, fluide, dédié, clé en main, à la pointe, en constante évolution.
**Avant :** « Une solution robuste et clé en main, à la pointe de la technologie. »
**Après :** « Un outil que j'utilise tous les jours et que je maintiens moi-même. »

### 8. Voix passive systématique
**Signe :** le sujet réel disparaît derrière une tournure passive.
**Avant :** « Les sauvegardes sont effectuées chaque nuit par le script. »
**Après :** « Le script sauvegarde chaque nuit. »

### 9. Évitement de la copule
**Signe :** contourner le verbe « être » avec des périphrases : « joue un rôle de », « se révèle être », « constitue », « s'impose comme ».
**Avant :** « Traefik se révèle être un reverse-proxy qui constitue la pierre angulaire de l'infrastructure. »
**Après :** « Traefik est le reverse-proxy de l'infrastructure. »
**Note FR :** ce motif transpose directement l'anglais ; les périphrases françaises typiques à traquer sont celles listées ci-dessus.

### 10. Parallélisme négatif
**Signe :** la formule « Ce n'est pas seulement X, c'est Y » ou « Non pas X, mais Y », utilisée pour gonfler.
**Avant :** « Ce n'est pas seulement un homelab, c'est une véritable philosophie de vie. »
**Après :** « C'est un homelab dont je me sers tous les jours. »

### 11. Règle de trois
**Signe :** des triplets d'adjectifs ou de groupes, systématiques, dont le troisième est souvent du remplissage.
**Avant :** « Rapide, fiable et élégant, ce service coche toutes les cases. »
**Après :** « Le service est rapide et je n'ai pas à m'en occuper. »

### 12. Variation élégante (synonymie forcée)
**Signe :** changer de mot à chaque reprise pour éviter une répétition, au prix de la clarté.
**Avant :** « Le serveur héberge le site. La machine sert les pages. Le nœud délivre le contenu. »
**Après :** « Le serveur héberge le site. » (et si l'on doit y revenir, on réécrit « le serveur », pas « la bécane »).

### 13. Tiret cadratin à l'anglaise
**Signe :** le tiret cadratin reste excellent pour une incise, mais l'usage anglais le colle sans espaces et le multiplie pour le drame.
**Avant :** « L'infra—self-hosted—tourne sur du matériel recyclé—et c'est tout l'intérêt. »
**Après :** « L'infra, entièrement auto-hébergée, tourne sur du matériel recyclé. »
**Note FR :** en français, le tiret cadratin d'incise s'entoure d'espaces — « mot — incise — suite ». Gardez l'incise utile ; supprimez l'accumulation et les tirets sans espaces.

---

## MOTIFS DE STYLE

### 14. Guillemets droits ou anglais
**Signe :** en français, les guillemets « » (avec espaces insécables) sont la norme. L'emploi de guillemets droits `"…"` ou anglais `“…”` trahit la sortie machine.
**Avant :** « Le mode "production" est activé. »
**Après :** « Le mode « production » est activé. »
**Note FR :** inverse exact de l'original anglais, où ce sont les guillemets courbes qui sont attendus. Ici, on convertit vers « … » avec espace insécable après l'ouvrant et avant le fermant.

### 15. Capitalisation de Chaque Mot d'un Titre
**Signe :** la capitalisation à l'anglaise (Title Case) n'existe pas en français ; capitaliser chaque mot d'un titre est un calque.
**Avant :** « Guide Complet Pour Déployer Votre Premier Serveur »
**Après :** « Guide complet pour déployer son premier serveur »
**Note FR :** en français, seule la première lettre du titre (et les noms propres) prend la majuscule.

### 16. Gras abusif
**Signe :** mettre en gras un mot sur trois, ce qui ne souligne plus rien.
**Avant :** « Le **homelab** est **essentiel** car il **apprend** des choses **concrètes**. »
**Après :** « Le homelab m'a appris à débugger un réseau pour de vrai. »

### 17. Emojis décoratifs
**Signe :** des emojis en tête de titre ou de puce, ton « post LinkedIn ».
**Avant :** « 🚀 Déploiement ultra-rapide ! ✨ Fiabilité au rendez-vous 🔥 »
**Après :** « Déploiement en 35 secondes, sans intervention. »

### 18. Listes à en-tête en gras
**Signe :** chaque puce commence par un mot en gras suivi de deux-points, de façon mécanique.
**Avant :**
> - **Performance** : le site est rapide.
> - **Sécurité** : tout est chiffré.
> - **Simplicité** : facile à maintenir.
**Après :** « Le site est rapide, chiffré de bout en bout, et je le maintiens seul en quelques minutes par mois. » (ou une vraie liste, quand la liste se justifie)

### 19. Structure de sections formulaïque
**Signe :** le même squelette imposé partout — introduction, points clés, conclusion — quelle que soit la matière.
**Avant :** chaque section ouvre sur « Dans cette partie, nous allons voir… » et ferme sur « En résumé… ».
**Après :** une structure qui suit le propos : on entre dans le sujet, on développe ce qui mérite de l'être, on s'arrête quand c'est dit.

---

## MOTIFS DE COMMUNICATION

### 20. Ton flagorneur
**Signe :** flatteries d'ouverture, enthousiasme de service après-vente.
**Avant :** « Excellente question ! Voici un guide formidable qui va vous ravir. »
**Après :** (entrer directement dans le sujet, sans préambule flatteur)

### 21. « En tant que modèle de langage… »
**Signe :** l'assistant qui se met en scène ou se disculpe.
**Avant :** « En tant que modèle de langage, je dirais que cette solution pourrait convenir. »
**Après :** « Cette solution convient pour un trafic faible ; au-delà, il faut un cache. »

### 22. Résidus de chatbot
**Signe :** les marqueurs de réponse d'assistant qui n'ont rien à faire dans un texte publié.
**Avant :** « Bien sûr ! Voici votre article : […] J'espère que cela répond à votre demande, n'hésitez pas si besoin ! »
**Après :** (le texte seul, sans l'emballage conversationnel)

---

## REMPLISSAGE ET PRÉCAUTIONS ORATOIRES

### 23. « Il est important de noter que » / « Il convient de souligner que »
**Signe :** une amorce solennelle pour une information qui se suffit à elle-même.
**Avant :** « Il est important de noter que le port utilisé est le 443. »
**Après :** « Le port est le 443. »

### 24. Précautions verbeuses (hedging)
**Signe :** empiler les atténuateurs : « il se pourrait que », « dans une certaine mesure », « de manière générale », « on pourrait soutenir que ».
**Avant :** « Il se pourrait que, dans une certaine mesure, cela améliore peut-être un peu les performances. »
**Après :** « Ça réduit la latence d'environ 40 ms. »

### 25. Conclusions formulaïques
**Signe :** « En conclusion », « En somme », « Pour résumer », suivis d'une redite.
**Avant :** « En conclusion, le homelab est un excellent moyen d'apprendre. »
**Après :** (supprimer ; ou finir sur une vraie dernière idée, pas un résumé)

### 26. Avertissement de date de connaissance
**Signe :** « à ma dernière mise à jour », « en date de [année] », réflexe d'assistant.
**Avant :** « En date de ma dernière mise à jour, Astro en était à la version 5. »
**Après :** « Au moment où j'écris (juin 2026), Astro est en 6.4.8. »

### 27. « Comme mentionné précédemment »
**Signe :** renvoi méta qui n'apporte rien et trahit un texte généré d'un bloc.
**Avant :** « Comme mentionné précédemment, le script tourne la nuit. »
**Après :** « Le script tourne la nuit. » (on le dit une fois, au bon endroit)

### 28. Ouvertures rhétoriques creuses
**Signe :** « À l'ère de… », « Dans un monde où… », « Dans le paysage de… », posés pour faire grave.
**Avant :** « À l'ère du numérique, où la donnée est reine, l'auto-hébergement prend tout son sens. »
**Après :** « J'héberge mes données moi-même, sur mon matériel. »

### 29. Connecteurs en surnombre
**Signe :** « notamment », « par ailleurs », « en effet », « ainsi », « de plus », posés à chaque phrase comme un coffrage.
**Avant :** « Ainsi, le serveur démarre. Par ailleurs, il journalise. En effet, c'est utile. De plus, il alerte. »
**Après :** « Le serveur démarre, journalise et m'alerte en cas de panne. »

### 30. Verbes et formules vides
**Signe :** « mettre en lumière », « s'inscrire dans une démarche », « faire sens », qui meublent sans rien dire.
**Avant :** « Ce projet s'inscrit dans une démarche d'excellence et met en lumière mon savoir-faire. »
**Après :** « J'ai monté ce projet pour apprendre Rust sur un cas réel. »

### 31. Anglicismes calqués
**Signe :** des calques de l'anglais : « adresser un problème », « supporter » (pour prendre en charge), « délivrer », « initier », « au final ».
**Avant :** « Cette version adresse le bug et supporte désormais IPv6. »
**Après :** « Cette version corrige le bug et prend en charge IPv6. »

### 32. « N'hésitez pas à… »
**Signe :** formule d'appel à l'action passe-partout, souvent en clôture.
**Avant :** « N'hésitez pas à me contacter pour toute question ! »
**Après :** « Une question ? Ouvrez une issue sur le dépôt. » (ou rien)

### 33. Transitions vides et méta-commentaire
**Signe :** « Sans plus attendre », « Entrons dans le vif du sujet », « Maintenant que nous avons posé les bases ».
**Avant :** « Sans plus attendre, entrons dans le vif du sujet ! »
**Après :** (commencer, simplement)

---

## GUIDE DE DÉTECTION

Pour repérer ces motifs vite et bien :

- **Lisez à voix haute.** Une phrase qu'aucun humain ne dirait à l'oral est suspecte.
- **Cherchez les triplets** (règle de trois) et les « Ce n'est pas X, c'est Y ».
- **Passez la typographie au crible** : guillemets droits ou anglais, Title Case,
  tirets cadratins collés, emojis, gras en surnombre.
- **Traquez les amorces** : « Il est important de noter », « À l'ère de », « En
  conclusion », « N'hésitez pas ».
- **Repérez les béquilles** : robuste, dédié, fluide, à la pointe, notamment, par
  ailleurs, en effet.
- **Comptez les connecteurs** : plus d'un par paragraphe, c'est trop.
- **Vérifiez les faits laissés** : un texte humanisé reste exact ; on retire le bruit,
  pas l'information.

Au moindre doute sur une réécriture qui changerait le sens ou le ton voulu, demandez —
via `AskUserQuestion` — plutôt que de trancher seul.

## Processus et sortie

1. **Lire** le texte (collé ou via `Read` sur le chemin fourni).
2. **Calibrer** la voix si un échantillon est donné.
3. **Repérer** les motifs, catégorie par catégorie.
4. **Proposer** un avant / après pour les passages réécrits (sur les changements
   notables ; inutile de tout dérouler ligne à ligne pour des broutilles).
5. **Appliquer** avec `Edit` (texte dans un fichier) ou rendre le texte réécrit
   (texte collé). Pour un fichier neuf, `Write`.
6. **Signaler** ce qui a été retiré et pourquoi, en une phrase, si ce n'est pas évident.

Ne jamais : inventer du contenu, retirer une information vraie, rallonger pour « faire
sérieux », ni aplatir la voix de l'auteur.

## Exemple complet

**Avant (très IA) :**
> À l'ère du numérique, où l'infrastructure est reine, il est important de noter que
> l'auto-hébergement s'impose comme une solution robuste et incontournable. Ce projet,
> rapide, fiable et élégant, ne se contente pas d'héberger des services : il incarne une
> véritable philosophie. Par ailleurs, il met en lumière un savoir-faire technique
> certain. En conclusion, n'hésitez pas à explorer cette approche révolutionnaire ! 🚀

**Après :**
> J'héberge mes services moi-même, sur quatre machines récupérées. Une cinquantaine de
> conteneurs : DNS, reverse-proxy, monitoring, sauvegardes. Zéro service cloud payant.
> Je l'ai monté pour comprendre comment ça marche en vrai — et maintenant je m'en sers
> tous les jours.

Ce qui a sauté : l'ouverture « À l'ère de », l'amorce « il est important de noter »,
la copule évitée (« s'impose comme »), la règle de trois, le parallélisme négatif
(« ne se contente pas… il incarne »), « met en lumière », « En conclusion »,
« n'hésitez pas », l'emoji. Ce qui reste : des faits, des chiffres, une voix.

## Référence

- Guide source : Wikipédia, [« Signs of AI writing »](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing).
- Œuvre originale : [`blader/humanizer`](https://github.com/blader/humanizer) (v2.8.0, MIT, © 2025 Siqi Chen).
- Adaptation française : `ferr079/humanizer-fr` (MIT, © 2026 Stéphane Ferreira). La
  table des motifs a été réécrite pour le français — typographie inversée, anglicismes
  et formules de remplissage propres aux modèles francophones.
