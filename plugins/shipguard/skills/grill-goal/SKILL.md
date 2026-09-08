---
name: grill-goal
description: "Clarifier le but de l'utilisateur par un dialogue approfondi, puis écrire un fichier goal Markdown autonome et vérifiable destiné à une IA. Utiliser pour définir, rédiger ou améliorer un goal, sans exécuter le travail décrit."
---

# Grill Goal

Comprendre avec l'humain ce qu'il veut accomplir et pourquoi, puis écrire le goal qu'une autre IA pourra poursuivre. Garder le document aussi simple que possible sans perdre de décision, de contrainte ou de preuve nécessaire.

Appliquer la règle fondamentale suivante pendant tout l'entretien et la rédaction. L'inscrire explicitement dans **chaque goal final**, dans la langue de l'utilisateur, pour qu'elle s'applique aussi à l'IA qui le poursuivra, sans dépendre d'un fichier d'instructions externe :

> Formuler les questions, réponses, notes et comptes rendus sans ambiguïté : préciser le sujet, la portée, les conditions et le statut des affirmations. Ne jamais prendre sa propre formulation antérieure pour une preuve ou un accord humain. Avant de tenir une affirmation reprise pour acquise, la rattacher à un fait observé, une source ou une décision humaine explicite ; conserver son éventuelle incertitude. La répétition ne transforme pas une hypothèse en fait ni une proposition en accord. Signaler et résoudre toute interprétation incertaine avant d'en dépendre ; corriger aussi les notes et conclusions affectées.

## Dialoguer jusqu'à comprendre

Partir de la demande, du goal existant s'il y en a un et des sources pertinentes disponibles. Examiner le besoin derrière la solution proposée ; ne pas ajouter d'exigences par habitude. Vérifier les faits accessibles et signaler les contradictions entre documents, état observé et demande. Réserver à l'humain ses intentions et ses arbitrages.

Parcourir les dimensions du goal ci-dessous comme un arbre de décisions. Poser une question à la fois par défaut, en résolvant les prérequis avant les questions dépendantes. Regrouper seulement des questions indépendantes si cela convient à l'utilisateur. Employer ses mots, expliquer les conséquences et proposer une recommandation motivée lorsqu'elle est fondée. Utiliser des scénarios concrets pour préciser les termes ambigus et les cas limites.

L'IA conduit l'entretien et attend les réponses humaines avant d'avancer sur les branches concernées. Une recherche peut avancer sur les autres branches ; son résultat ne vaut jamais réponse de l'utilisateur. Si une question n'est pas comprise, l'expliquer avant de la reposer.

Continuer tant qu'un doute pourrait changer le but, une contrainte, le périmètre ou l'acceptation. Ne pas limiter le nombre de questions, inventer de réponse ou prendre le silence pour accord. Aider l'utilisateur à arbitrer s'il hésite. Laisser ouverts les moyens qu'il délègue, jamais une décision qui définit la réussite sous prétexte de détail d'implémentation.

Rechercher les erreurs réellement rencontrées sur la tâche ou des tâches comparables : retours de l'utilisateur, issues pertinentes avec commentaires et corrections, incidents et retours d'expérience sur le web. Expliquer pourquoi les précédents d'autres tâches s'appliquent ici ; leur recherche reste possible même si un dépôt pertinent existe. Retenir les précédents qui peuvent changer une décision ou un contrôle. Distinguer signalement, fait confirmé et cause supposée ; une issue fermée ne prouve pas une correction. Si les sources sont inaccessibles ou qu'aucun précédent fiable n'est trouvé, l'écrire dans le goal avec la recherche effectuée et ses limites, sans inventer d'historique.

Conserver dans des notes brèves les termes, décisions, raisons et questions ouvertes ; utiliser un brouillon Markdown si l'entretien se prolonge. Après une correction, retirer les branches et formulations devenues caduques.

Quand les décisions nécessaires sont résolues, présenter une synthèse conservant le sens de chaque exigence déterminante retenue des sources et des réponses humaines. Résumer est permis ; remplacer ces exigences par un intitulé comme « contraintes » ne l'est pas. Distinguer décision humaine, fait vérifié, proposition et hypothèse ; rendre les propositions à accepter explicites. Obtenir la confirmation ou les corrections avant de rédiger et livrer le goal final. Une synthèse modifiée doit être confirmée à nouveau ; une confirmation déjà donnée sur la même synthèse suffit. Une interruption laisse un brouillon avec les inconnues restantes, pas un goal final.

## Écrire le goal confirmé

Rédiger dans la langue de l'utilisateur, pour une IA sans accès à la conversation. Inscrire le contenu des exigences déterminantes confirmées, y compris celles que le livrable devra lui-même respecter ou transmettre. Un nom de rubrique, de personne, de méthode ou un renvoi à une source ne remplace pas ce contenu. Nommer l'acteur et l'objet de chaque instruction lorsqu'ils pourraient être confondus. Les rubriques suivantes décrivent ce que le goal doit transmettre, à adapter à la mission sans perdre d'exigence :

- **But et résultat attendu** : besoin, bénéficiaire, changement observable et livrables ; leur forme et destination lorsqu'elles s'appliquent, ou qui en décide. Pour une investigation, définir la question et les preuves attendues sans imposer la conclusion.
- **Contexte utile** : entrées, chemins ou sources, vocabulaire et décisions déterminantes avec leurs raisons. Distinguer état vérifié, choix acceptés à réaliser, hypothèses et dépendances ; une décision n'est pas une réalisation.
- **Périmètre et contraintes** : inclusions, exclusions, obligations, préférences et priorités, ressources et autorisations. Vérifier leur compatibilité et leur faisabilité. Écrire les interdictions propres à la mission, les choses à préserver et les options rejetées dont la raison reste déterminante. Ne pas inventer de délai, budget ou autorisation.
- **Erreurs connues à ne pas reproduire** : pour chaque précédent pertinent, indiquer le fait rapporté et son statut, une source identifiable sans la conversation, le contexte, la pertinence, la prévention et le contrôle associé. Résumer les informations nécessaires même si la source devient inaccessible. Ne pas y copier un catalogue d'erreurs génériques de rédaction de goals.
- **Critères de réussite** : pour chaque exigence, condition observable, preuve et contrôle dans les conditions visées ; grille et responsable d'appréciation si un jugement qualitatif l'exige. Si l'acceptation revient à l'humain, attendre son jugement pour déclarer la réussite. Couvrir les scénarios d'échec pertinents. Distinguer preuve réelle, test local et approximation ; ne pas inventer de commande ou de seuil.
- **Progression et fin** : adapter les moyens aux observations, conserver décisions et preuves, vérifier l'état à la reprise. Ne pas affaiblir ni réinterpréter le résultat attendu ou les conditions d'acceptation pour déclarer la réussite ; leur modification exige un arbitrage humain. Les moyens de vérification peuvent être corrigés ou améliorés en conservant ces exigences. Continuer tant que des critères restent insatisfaits et qu'une action utile est possible. En cas de blocage, préciser tentatives, manque et entrée nécessaire pour reprendre ; revenir à l'humain si une hypothèse déterminante est démentie ou qu'un arbitrage changerait le but.

Avant livraison, confronter les exigences déterminantes retenues des sources et de l'entretien, la synthèse confirmée et le goal rédigé. Retrouver le contenu de chacune, pas seulement sa rubrique ; corriger les omissions, affaiblissements, ajouts non décidés et ambiguïtés. Vérifier qu'un lecteur sans la conversation comprend chaque exigence. Vérifier aussi la présence intégrale de la règle fondamentale, le résultat de la recherche de précédents et les conditions de livraison. Les moyens explicitement délégués restent libres.

Chercher un cas où les contrôles passeraient malgré un besoin insatisfait, puis corriger la vérification sans affaiblir l'exigence. Des actions effectuées, un fichier présent, un contrôle vert ou un budget épuisé ne prouvent pas à eux seuls la réussite. Revenir au dialogue si une décision manque, si des exigences sont incompatibles ou irréalisables, ou si la correction change une décision déterminante de la synthèse confirmée.

## Livrer

Écrire le fichier Markdown au chemin demandé, sinon dans `GOAL-<sujet>.md`, sans écraser un fichier existant sans accord. Donner son lien, son chemin absolu et le texte suivant pour une IA disposant de `/goal`, avec le chemin réel et dans la langue de l'utilisateur :

`/goal Lis le fichier /chemin/absolu/GOAL-sujet.md et poursuis le goal qu'il décrit.`

Si l'autre IA n'a pas accès à ce chemin, indiquer de joindre le fichier. S'arrêter après livraison ; ne pas lancer le goal.
