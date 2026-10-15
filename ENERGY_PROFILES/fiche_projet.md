# Energy profiles

## Contexte métier

Energy profiles est une plateforme externe de ventes de rapport contenant les profiles energetiques de plus de 100 pays. Les rapports sont conséquents (+ de 50 pages et jusqu'à 100),
et contiennent plusieurs parties bien définies et identiques.
Les rapports sont payants et ne doivent pas fuiter publiquement à des non clients.

Le service commercial voudrait pouvoir afficher, sur le portail, de manière dynamique, le résumé des différentes parties d'un rapport sans en dévoiler toute l'intégralité.


LocalMind est une plateforme interne de traitement documentaire pour des équipes qui manipulent des rapports, comptes rendus et politiques internes sensibles. Les documents ne doivent pas sortir du système d'information. Les collaborateurs passent beaucoup de temps à lire des contenus longs pour en extraire l'essentiel.

Le projet porte sur une assistance de synthèse fiable, ciblée par défaut sur les 2-3e centres d'interêts du prospect, mesurable et compatible avec ces contraintes de non divulgations.

## Utilisateurs et enjeux

Les utilisateurs principaux sont des visiteurs (prospects) qui veulent connaitre ce que contient nos profils. Les responsables commerciaux sont attentifs à la disponibilité du service, à la protection des données et à la qualité des synthèses.

Les enjeux sont de permettre l'extraction et le résumé d'une partie définit pour un pays donné et de rendre l'information plus accessible sans dénaturer le document.
Les risques sont une fuite de contenu sensible, une synthèse trompeuse, des traitements longs qui bloquent l'utilisateur et l'indisponibilité sur des machines aux ressources limitées.
Par défaut seul le profil de son pays peut être intérogeable par un prospects, un utilisateur interne à accès à tous les résumés.

## Données mises à disposition

Les jeux suivants sont fournis. Ils représentent des sources de travail ; leur sélection et leur rôle dans votre proposition font partie du cadrage.

- `donnees/sources_documentaires/profil_malaisie` : le profil energetique complet de la Malaysie au format pdf.
- `donnees/sources_documentaires/profil_tchéquie` : le profil energetique complet de la répulbique tchèque au format pdf.
- `donnees/exemples_prompts/prompt_v1.txt` et `prompt_v2.txt` : exemples de consignes de synthèse à comparer et faire évoluer.
- `donnees/jeux_evaluation/eval.csv` : documents et synthèses de référence pour construire et exécuter votre évaluation.

## Contraintes réelles

- Les contenus restent dans le système d'information et ne doivent pas être transmis à un service externe.
- Les documents peuvent être longs et nécessiter un traitement dont la durée varie.
- L'utilisateur doit comprendre l'état d'un traitement et pouvoir récupérer son résultat sans attente opaque.
- Des machines modestes peuvent être utilisées ; prévoyez des comportements acceptables lorsque les ressources sont limitées ou le service indisponible.

## Workflows métier actuels

### Remplir les synthèses par métiers des profils pays

**Déclencheur → acteurs → informations consultées → décisions → actions → résultat attendu**  
Profil rédigé → collaborateur → liste des sous parties du profil, contenu des sous parties → décider du type de synthèse utile et des informations à préserver → soumettre la demande → synthèse adaptée au besoin du portail.

Frottements et risques observables : difficulté de séléction des éléments importants d'une partie, traitement très long, qualité syntaxique, trop de contenu exposé.

### Suivre un traitement long

**Déclencheur → acteurs → informations consultées → décisions → actions → résultat attendu**  
Demande en cours → collaborateur, service commercial → état du traitement, disponibilité des ressources, profil concerné → décider d'attendre, de relancer ou de réduire le périmètre de la demande → consulter l'avancement et récupérer le résultat lorsqu'il est disponible → utilisateur informé sans blocage opaque.

Frottements et risques observables : durée imprévisible, échec non signalé, indisponibilité locale, perte de résultat.

### Publier les synthèses publiquement

**Déclencheur → acteurs → informations consultées → décisions → actions → résultat attendu**  
Synthèse préparée pour la publication → collaborateur, service Research → document d'origine, synthèse, listes des utilisateur du portail profil → vérifier l'exactitude des informations → un responsable humain valide le partage et le pays de chaque prospects → synthèse publiées avec liste des utilisateurs/prospects autorisés.

Frottements et risques observables : synthèse inexacte, omission de nuance, diffusion à un mauvais destinataire, absence de validation, contenu non ciblé "prospect".

## Votre cadrage

À partir de ces éléments, choisissez un objectif prioritaire et formulez un MVP observable. Quel problème précis mérite d'être traité en premier, pour quel utilisateur, et pourquoi ? Définissez une baseline, une métrique de succès et les sources réellement utiles. Précisez le niveau d'automatisation retenu, les risques, les garde-fous et les non-objectifs. Quelle décision doit rester humaine ? Quelle preuve vous ferait conclure que le MVP aide réellement sans accroître le risque ?

Justifiez explicitement pourquoi un **traitement LLM simple (chat)**, un **Workflow**, un **RAG** ou un **Agent** sont retenus ou écartés pour votre périmètre — la solution la plus simple qui fait la preuve de la valeur est un choix légitime. Expliquez comment vous préservez la confidentialité, évaluez la qualité et gérez les traitements longs ou indisponibles.

## Démarrer

Commencez par la [méthodologie unifiée AI Engineering](../../AI_engineering_project_message/README.md). Elle vous guide du cadrage à l'exploitation et rappelle les bonnes pratiques de software engineering attendues.

Documentez vos décisions importantes dans des ADR et conservez les preuves demandées à chaque phase : contrat, baseline, tests, résultats d'évaluation, traces et démonstrations de fonctionnement ou d'échec maîtrisé.

Le jeu de 5 à 10 cas demandé dès le cadrage peut partir des cas fournis dans `donnees/jeux_evaluation/` ; complétez-les par vos propres cas ambigus et d'erreur, en documentant ce que vous ajoutez et pourquoi.
