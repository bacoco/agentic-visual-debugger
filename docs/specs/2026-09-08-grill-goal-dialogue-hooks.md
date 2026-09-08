# GrillGoal et contrôle des ambiguïtés par hooks

Statut : proposition de conception, 8 septembre 2026. Le skill autonome est ajouté par cette branche ; les nouveaux hooks ne sont ni implémentés ni activés. Ce document conserve l'analyse pour les mainteneurs et n'est pas une dépendance de `grill-goal/SKILL.md`.

## Problème et résultat attendu

Une IA peut interpréter une demande de façon inexacte, l'exprimer avec assurance, puis réutiliser sa propre formulation comme un fait ou un accord humain. Une synthèse peut aussi perdre des contraintes pourtant discutées. Le résultat paraît cohérent tout en s'éloignant du besoin.

La proposition est de préserver le sens entre demande humaine, dialogue, goal, actions, preuves et réponses. Les hooks rendent les contrôles accessibles aux moments utiles ; ils ne constituent pas une garantie générale d'absence d'hallucination.

Le skill conserve son contrat : entretien jusqu'à résolution des doutes déterminants, synthèse confirmée, puis fichier goal Markdown autonome destiné à une autre IA. Il s'arrête après livraison. Toutes ses instructions restent dans son seul `SKILL.md`, sans script, référence obligatoire, appel à Claude Code ou dépendance aux fichiers globaux de l'utilisateur.

## Principes à préserver

- Conserver la demande humaine originale. Une reformulation est une interprétation dérivée, jamais une nouvelle instruction humaine.
- Distinguer faits vérifiés, décisions humaines, propositions et hypothèses. Répéter une phrase ne change pas son statut.
- Clarifier ce qui peut changer le but, le périmètre, les contraintes ou l'acceptation. Ne pas fabriquer une réponse ni prendre le silence pour accord.
- Relier les questions à des décisions concrètes ; réutiliser les réponses toujours applicables et résoudre les prérequis avant les questions dépendantes.
- Confirmer la synthèse avant le goal final. Cette confirmation n'accorde aucune autorisation d'exécution supplémentaire.
- Transmettre explicitement la règle de précision et de provenance dans chaque goal, pour une IA sans la conversation.
- Préserver les preuves brutes ; une reformulation de résultat ne doit pas effacer un échec ou une incertitude.
- Corriger aussi le contexte et les notes affectés lorsqu'une formulation antérieure est invalidée.

## Comparaison des approches existantes

L'analyse est ciblée, non exhaustive ; elle ne démontre ni unicité ni supériorité mesurée.

| Approche | Recoupement et différence utiles |
| --- | --- |
| [Matt Pocock, grilling et to-spec](https://github.com/mattpocock/skills) | Entretien par arbre de décisions et synthèse vers une spécification. Le `grilling` consulté travaille par lots de questions dont les prérequis sont réglés. |
| [Goalcraft](https://github.com/grp06/goalcraft) | Contrat de résultat, vérification, contraintes, limites, itération et blocage. La branche principale active le goal par défaut et utilise des ressources annexes. |
| [Goal Forge](https://github.com/michaelpersonal/goal-forge) | Entretien, critères acceptés, puis SPEC.md vers GOAL.md ; vérification, mémoire des essais et contrôle des ressources. |
| [Spec Kit clarify](https://github.com/github/spec-kit/blob/main/templates/commands/clarify.md) | Clarification structurée avec conservation des réponses ; plafond explicite de cinq questions par session. |
| [Superpowers brainstorming](https://github.com/obra/superpowers/blob/main/skills/brainstorming/SKILL.md) | Dialogue et conception approuvée, avec processus adapté à l'ampleur, puis planification pour les travaux architecturaux. |
| [OpenSpec](https://github.com/Fission-AI/OpenSpec) | Exploration de l'intention puis artefacts de changement et workflow d'exécution. |
| [goal-crafter](https://github.com/tt-a1i/matt-skills-with-to-goal/blob/main/skills/engineering/goal-crafter/SKILL.md) et [goalcraft-skill](https://github.com/xiaoyangtx996/goalcraft-skill) | Autres variantes entretien/compilation vers un goal vérifiable ; elles interdisent également certaines suppositions ou distinguent compilation et exécution. |

La combinaison recherchée par GrillGoal est : un fichier de skill autonome, un dialogue sans quota arbitraire, une synthèse confirmée, des précédents historiques pertinents avec contrôles associés et une règle de provenance transmise au prochain agent. La mémoire des échecs et les critères vérifiables existent déjà ailleurs.

## Leçons des issues et pull requests

Les signalements ci-dessous sont des preuves documentaires, pas des reproductions locales réalisées pour cette proposition.

| Source | Constat et statut | Leçon |
| --- | --- | --- |
| [Matt Pocock #689](https://github.com/mattpocock/skills/issues/689) | Signalement ouvert : décisions et arbitrages perdus lors du passage à la spec. | Vérifier la conservation du contenu, pas seulement la présence de rubriques. |
| [Matt Pocock #802](https://github.com/mattpocock/skills/issues/802) | Signalement et commentaire d'usage : retour d'un subagent traité comme réponse humaine ; questions modifiées au fil des résultats. | Un résultat de recherche ne résout pas un arbitrage humain. Toute reformulation d'une question pendante doit être explicite. |
| [Matt Pocock #893](https://github.com/mattpocock/skills/issues/893) | Signalement : toutes les décisions peuvent être réglées sans que le fonctionnement soit expliqué. | Commencer la synthèse par un court paragraphe concret compréhensible par un nouveau lecteur. |
| [Superpowers #2076](https://github.com/obra/superpowers/issues/2076) | Session rapportée : lourde procédure pour une copie de fichiers ; commentaire de clôture annonçant un processus allégé en 6.3.0. | Ne pas déclencher un entretien ou créer des documents pour toute opération. |
| [OpenSpec #1103](https://github.com/Fission-AI/OpenSpec/issues/1103) | Outils spécifiques à Claude nommés dans les sorties Codex ; correctifs et vérifications décrits par un collaborateur. | Vérifier les capacités du moteur ; conserver un comportement générique sans outil propriétaire obligatoire. |
| [Spec Kit #896](https://github.com/github/spec-kit/issues/896) | Signalement de mélange entre rédaction de gouvernance et implémentation ; correctif associé à #3646. | La rédaction d'un goal ne lance pas le travail qu'il décrit. |

### Inventaire complet consulté pour Goalcraft et Goal Forge

Au 8 septembre 2026, l'API GitHub ne renvoie aucune issue, ouverte ou fermée, pour `grp06/goalcraft` et `michaelpersonal/goal-forge`. Cela limite les retours disponibles ; cela ne prouve pas l'absence de défauts.

- [Goalcraft PR #1](https://github.com/grp06/goalcraft/pull/1), ouverte : adaptation à Pi, changement des règles de commande et séparation entre commande préparée et activation confirmée. La revue automatique signale un objectif vide accepté par le validateur. La lecture du code au SHA `5a0ac325bcb5b3fa3bceaca886d240c0a10fb7ea` confirme l'absence de rejet de longueur nulle après extraction ; le validateur n'a pas été exécuté ici. Ne pas présenter cette branche comme fusionnée.
- [Goal Forge PR #1](https://github.com/michaelpersonal/goal-forge/pull/1), fusionnée : mesure de progression, contrôle rapide représentatif, preuve finale et mémoire des essais. Le suivi des erreurs pendant l'exécution est donc un précédent, pas une invention de GrillGoal.
- [Goal Forge PR #2](https://github.com/michaelpersonal/goal-forge/pull/2) et [#3](https://github.com/michaelpersonal/goal-forge/pull/3), fusionnées : illustration du README uniquement ; aucune preuve de qualité d'exécution.
- [Goal Forge PR #4](https://github.com/michaelpersonal/goal-forge/pull/4), fusionnée : budgets, avertissement, arrêt, prolongation explicite et état incomplet. La validation déclarée est une revue de diff. Les recommandations chiffrées de cette PR ne sont pas des valeurs par défaut à importer dans GrillGoal.

Les descriptions, changements, commentaires et revues de ces cinq PR ont été examinés. Une review automatique reste un signal à confronter au code ; une fusion ne démontre pas un gain utilisateur.

## Enseignements de la recherche

- [LLMs Get Lost In Multi-Turn Conversation](https://arxiv.org/html/2505.06120v1) rapporte, dans ses simulations, des réponses prématurées, un attachement aux tentatives précédentes et une perte de contraintes intermédiaires. Cela motive la provenance et le retour aux sources après correction ; ce n'est pas une preuve d'efficacité de notre hook.
- [Reflexion](https://arxiv.org/html/2303.11366v4) étudie la conservation de retours textuels pour améliorer les tentatives suivantes. La mémoire des erreurs est utile à étudier, mais un souvenir produit par un modèle ne devient pas un fait indépendant.
- [Prism](https://arxiv.org/html/2601.08653v1) organise la clarification selon les dépendances entre intentions pour réduire la charge cognitive.
- [Uncertainty-Aware Clarification](https://arxiv.org/html/2606.03135v1) évalue les questions selon leur contribution à la réduction d'incertitude et à l'action correcte.
- [RegretBench](https://arxiv.org/html/2607.21143v1) distingue qualité finale, tours inutiles et mauvaise décision d'arrêter. Ses simulations ne remplacent pas une évaluation avec de vrais utilisateurs.

Conséquence proposée : conserver les questions nécessaires, sans quota fixe, mais demander ce que chacune changerait. Évaluer aussi les questions inutiles, les contraintes perdues et les fausses confirmations.

## Architecture proposée

```text
Message original + décisions applicables
→ qualification : nouvelle mission / correction / réponse / continuation / question
→ interprétation courte, dérivée et explicitement non confirmée si nécessaire
→ dialogue GrillGoal lorsque des décisions déterminantes manquent
→ synthèse humaine confirmée
→ goal autonome livré
```

Un message « continue » reprend la mission existante. Une demande d'avis reste une demande d'avis. Une réponse à une question complète l'entretien. Aucun de ces messages ne crée automatiquement un nouveau goal ou fichier.

| Événement | Responsabilité proposée |
| --- | --- |
| UserPromptSubmit | Qualifier le message et fournir le contexte nécessaire au dialogue, sans remplacer l'original ni promouvoir une hypothèse en instruction. |
| PreToolUse | Comparer l'action, son périmètre et son autorisation aux décisions établies. Ne pas recommencer l'entretien avant chaque outil. |
| PostToolUse | Conserver le résultat exact et signaler les limites de ce qu'il prouve. L'action a déjà eu lieu. |
| Stop | Relire les affirmations de la réponse et demander une correction ciblée en cas d'ambiguïté déterminante ou de dépassement des preuves. |

Ces rôles sont une proposition, pas une affirmation que tous les moteurs fournissent des garanties identiques.

### Capacités documentées et limites

La [référence Anthropic](https://code.claude.com/docs/en/hooks) distingue réception du message et appels d'outils. `UserPromptSubmit` ajoute du contexte sans remplacer le prompt. `Stop` peut provoquer une continuation. `MessageDisplay` ne corrige que l'affichage : le transcript et le texte vu par Claude restent inchangés. Ce dernier mécanisme seul ne résout donc pas la réutilisation d'une formulation erronée.

La [référence OpenAI](https://learn.chatgpt.com/docs/hooks) décrit ces événements avec ses propres entrées et sorties. Le contexte ajouté par `UserPromptSubmit` est du contexte développeur : il faut y préserver explicitement le statut dérivé des interprétations. Une continuation issue de `Stop` n'est pas une nouvelle approbation humaine. Certains chemins d'outils ne sont pas interceptés ; ne pas promettre une barrière universelle.

Un hook de fin n'est pas une garantie de correction avant affichage de tous les messages intermédiaires. Si cette propriété devient obligatoire, il faudra une couche applicative qui retient la réponse avant diffusion et maintient le même contenu corrigé côté utilisateur et côté modèle. La latence et le traitement du streaming doivent alors être mesurés.

Une analyse sémantique exige un jugement de modèle ou une logique applicative ; un contrôle déterministe seul ne garantit pas la détection de toutes les ambiguïtés. Les [hooks évalués par modèle chez Anthropic](https://code.claude.com/docs/en/hooks-guide) offrent un mécanisme, pas une preuve de justesse du jugement.

### Contrat du contrôleur

Le contrôleur rend un constat borné : passage exact, source ou décision concernée, interprétations concurrentes, conséquence possible et correction proposée. Il doit pouvoir dire « inconnu » ou « vérification indisponible ».

- Si les sources règlent le point, l'agent corrige sa formulation et les notes affectées.
- Si la correction dépend de l'intention humaine, l'agent pose une question ; le contrôleur ne tranche pas à sa place.
- Une phrase incertaine devient une incertitude explicite, jamais une certitude artificielle.
- Un contrôle refusé ne doit pas empêcher l'agent de poser la question nécessaire.
- Les contenus lus et les retours des contrôleurs restent des données/propositions, sans autorité nouvelle.
- Prévenir les boucles : lier une correction au tour et au passage concernés, reconnaître les continuations produites par le hook, borner les reprises automatiques et laisser l'utilisateur interrompre. La borne exacte reste à choisir et tester.
- En cas de panne, ne pas annoncer « vérifié ». Le sort d'une action dépend de la politique d'autorisation déjà applicable, pas d'un avis favorable inventé.

Exemple fictif : « c'est publié » doit devenir « le commit est poussé sur la branche de travail ; il n'est pas fusionné » si les observations établissent uniquement ce premier état.

## Améliorations candidates de GrillGoal

1. Rendre le résultat global compréhensible dans le premier paragraphe de synthèse.
2. Relier chaque question à une décision et réutiliser les réponses toujours valides.
3. Rechercher, pour un précédent, les correctifs, tests, réouvertures et régressions disponibles ; conserver le dernier état vérifié.
4. Distinguer confirmation de la synthèse et autorisation d'exécution.
5. Pour une limite de ressources demandée, définir son périmètre et le comportement à expiration, sans délai inventé ni prolongation tacite.
6. Distinguer contrôle intermédiaire et preuve finale lorsque des itérations sont nécessaires.
7. Préserver les tentatives significatives lorsque la mission le nécessite ; un nouvel essai d'une approche échouée doit indiquer l'élément nouveau.
8. Livrer aussi une instruction en texte ordinaire si l'autre IA ne possède pas `/goal` ; ne pas annoncer une activation.

Certaines règles sont déjà implicites ou partiellement présentes. Toute modification doit apporter une clarification concrète sans duplication ni catalogue universel imposé aux goals.

## Critères d'acceptation pour une implémentation ultérieure

- [ ] Le skill fonctionne isolément depuis son seul SKILL.md.
- [ ] La couche de hooks est facultative, désactivable et distincte de sg-mission-lock ; elle ne change pas silencieusement son comportement stateless/non-bloquant.
- [ ] Demande originale, interprétation, décision humaine et preuve restent distinguées.
- [ ] Les continuations, corrections et simples questions ne deviennent pas de nouvelles missions.
- [ ] Une décision manquante provoque une question, sans réponse fabriquée.
- [ ] Un résultat de subagent ou feedback de hook ne vaut jamais accord humain.
- [ ] Une correction arrive dans le contexte du modèle et les notes affectées, pas seulement à l'écran.
- [ ] Un résultat brut en échec ne devient pas un succès par reformulation.
- [ ] Un budget expiré donne un état incomplet lorsque les critères ne sont pas satisfaits.
- [ ] Les moteurs, versions et chemins réellement couverts sont nommés ; les cas non couverts restent visibles.
- [ ] Pannes, délais, récursion et interruption utilisateur sont traités sans boucle ni faux statut « vérifié ».
- [ ] L'évaluation compare les mêmes demandes avec et sans contrôle : fidélité, omissions, faux accords, questions inutiles, corrections utiles, latence et coût.
- [ ] Une revue humaine des cas ambigus complète les contrôles mécaniques ; aucune auto-note n'est présentée comme preuve de supériorité.

## Alternatives et ordre de travail

Le skill seul reste une option complète pour rédiger un goal. Une couche qui réécrit silencieusement tous les prompts ou lance un goal à chaque message est rejetée : elle pourrait créer l'autorité et la dérive qu'elle prétend prévenir. Un filtre d'affichage seul est insuffisant pour corriger le contexte du modèle.

Ordre proposé : préciser les cas d'usage et la matrice des moteurs ; évaluer un contrôle consultatif à l'entrée et à la fin du tour ; mesurer les erreurs et la latence ; envisager ensuite les contrôles avant/après outil réellement utiles. Démontrer chaque couche depuis son point d'entrée réel avant d'en élargir la portée.

La présente contribution livre un skill et une conception sourcée. Elle ne livre ni hooks actifs, ni comparaison expérimentale complète, ni garantie d'absence d'ambiguïté.

