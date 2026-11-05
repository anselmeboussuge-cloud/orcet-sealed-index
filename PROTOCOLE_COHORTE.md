# Orcet : cohorte prospective PLF et PLFSS 2027

Version 1, arrêtée le 24 octobre 2026 avant tout dépôt du nouveau candidat. Aucune performance de cette cohorte n'a servi au choix du modèle. Toute modification ultérieure sera datée et justifiée ici, sans modifier les prédictions déposées.

## Question et domaine

Pour un député qui exprime un vote binaire lors d'un scrutin public nominatif sur un amendement, prévoir P(pour | pour ou contre). Il ne s'agit ni d'une prévision de présence, ni d'une probabilité d'adoption, ni d'une prévision d'abstention. Le succès historique ne prouve pas le succès futur.

Le journal local du 21 octobre appartient à une autre cohorte et à un autre modèle, Orcet v2 contenu. Il sera évalué séparément. Aucune probabilité du nouveau candidat ne lui sera substituée.

## Inclusion exhaustive, sans sélection par difficulté

Le registre d'évaluation inclut **tous** les scrutins publics nominatifs de séance de l'Assemblée nationale portant sur un ou plusieurs amendements des dossiers PLF 2027 (DLR5L17N54629, texte initial PRJLANR5L17B3210) et PLFSS 2027 (DLR5L17N54951, texte initial PRJLANR5L17B3211), entre le premier dépôt de ce candidat et le 17 novembre 2026 à 23 h 59 min 59 s, heure de Paris. Les nouvelles lectures et nouveaux numéros de texte appartenant à ces dossiers sont suivis. Le Sénat, les commissions, les articles et les votes d'ensemble restent hors du domaine validé et ne sont pas comptés comme des succès.

On émet en amont pour **tous les amendements de séance encore en discussion**, sans seuil de confiance, échantillonnage, sélection de groupe, de sujet ou de nature. Cette précaution évite d'attendre l'annonce parfois tardive d'un scrutin public. Les amendements qui ne seront jamais soumis à un scrutin nominatif sont recensés séparément et ne deviennent pas des erreurs ni des succès.

Les rectifications sont des versions distinctes. Une nouvelle version donne un nouveau fichier, jamais une réécriture. Pour l'évaluation principale, on retient la première émission horodatée recevable de la version effectivement votée et du député considéré. Un rafraîchissement ultérieur n'efface pas cette émission.

Tout scrutin non couvert figure dans le registre exhaustif avec la raison : pièce ou version absente, annonce tardive, horodatage trop tardif, rapprochement ambigu, acteur sans historique, erreur de collecte. Il n'est jamais silencieusement exclu du taux de couverture. Pour les votes groupés, les prédictions de chaque amendement restent disponibles ; faute de modèle validé de vote collectif, ils sont classés non couverts dans le score principal, et détaillés à part. On ne duplique jamais les suffrages d'un même scrutin pour gonfler l'effectif.

## Candidat figé et témoins

Le candidat est le mélange à poids égaux d'Orcet v2 contenu calibré et de la fréquence historique lissée groupe du votant × groupe de l'auteur. Il reprend les paramètres choisis sur les seuls plis historiques : graine 42, projection Ridge alpha 10, inverse de température 0,1590803490585459, poids MIRT 0,5, lissage hiérarchique de 50 pseudo-observations, sans pondération de récence. Les votes d'apprentissage précèdent strictement le 22 mai 2026. Aucun réentraînement ni réglage sur la cohorte prospective avant le bilan.

Chaque dépôt enregistre le commit exact du code d'inférence, le SHA-256 des poids, des références historiques et du protocole, les caractéristiques sources et leurs empreintes. Les groupes sont lus dans les mandats officiels connus à la production ; l'affiliation d'auteur est prise à la date du dépôt. Aucune position majoritaire réalisée au scrutin prédit n'est une entrée.

Les témoins sont émis simultanément : (1) Orcet v2 contenu calibré, (2) fréquence historique lissée du seul groupe du votant, (3) fréquence historique individuelle. La référence groupe × auteur seule est également conservée. Seuil de décision 0,5 pour tous, égalité classée pour. Une fréquence de groupe n'est pas le vote effectivement observé de ses collègues. Les inconnus sont marqués ; aucun résultat du scrutin n'est utilisé pour les compléter.

## Antériorité et intégrité

Un commit de ce protocole précède tout fichier `predictions/*-orcet-*.json`. Un commit distinct fige le code et les artefacts avant leur premier usage. Les fichiers sont créés exclusivement, portent l'heure UTC de fin de production et ne sont jamais remplacés. Les données sont publiques ; aucune donnée de cabinet ni coordonnée privée n'est exportée.

Le dépôt Git privé est poussé avant le vote, après `git pull --rebase`, en ne commitant que nos fichiers. Le workflow existant ajoute les preuves OpenTimestamps à 06:00 et 18:00 UTC. On contrôle son succès et la vérification de la preuve : un fichier `.ots` en attente ne suffit pas à certifier une antériorité Bitcoin. La date déclarée par le programme et la date de commit ne remplacent pas une preuve tierce.

Le bilan principal exige une preuve tierce antérieure à l'ouverture du scrutin. À défaut d'heure officielle d'ouverture, la borne prudente est le début de la date de séance en heure de Paris. Les dépôts dont l'antériorité est seulement locale sont affichés dans une catégorie distincte, jamais certifiés prospectifs. Si le scrutin risque de précéder le prochain workflow, demander à Anselme son déclenchement manuel. Un échec des étapes précédant l'horodatage est un incident, pas une preuve acquise.

## Vérité de terrain et métriques arrêtées à l'avance

Sources : JSON officiels de l'Assemblée (amendements, votes nominatifs, dossiers, mandats), liens officiels entre scrutin et amendement. Contrôles : identifiant du texte et de l'organe, unicité du lien, version du dispositif, date, concordance des totaux nominaux avec la synthèse. Les mises au point sont documentées ; les votes officiellement recensés servent de label. Les abstentions et non-votants ne deviennent jamais des contre.

Publier : bonnes prédictions / suffrages binaires comparables, exactitude micro et moyenne par scrutin, Brier micro et moyenne par scrutin, log loss (probabilités bornées à 1e-12 pour le calcul), diagramme de calibration en dix intervalles fixes de probabilité [0;0,1[ ... [0,9;1], ECE et effectifs de chaque intervalle. Toutes les comparaisons portent sur les mêmes couples député-scrutin. Détailler par texte, groupe, nature, nouveaux députés et confiance. Analyser individuellement chaque erreur avec confiance >= 0,90, seuil fixé avant résultats.

Intervalles à 95 % et différences appariées : bootstrap de blocs par journée de séance (2 000 tirages, graine 42), avec sensibilité par scrutin. Pas d'intervalle binomial supposant les votes de députés indépendants. Si moins de cinq journées ou moins de cinq scrutins, qualifier les intervalles de non fiables et ne conclure à aucun gain généralisable. Deux dossiers ne permettent pas de démontrer une généralisation à tous les textes.

Publier aussi : couverture scrutins/amendements/députés, retards de collecte et de scellement, versions modifiées, non-votés, retirés, tombés, votes non nominatifs et collectifs. Donner une borne conservatrice d'exactitude sur tous les suffrages du périmètre en comptant les non couverts comme échecs ; ne pas la confondre avec le score conditionnel du modèle.

## Bilan et exploitation

Le 18 novembre 2026 : produire `BILAN_2026-11-18.md`, même si la procédure budgétaire a changé ou si le nombre de scrutins est insuffisant. La date de fin ne sera pas déplacée selon les résultats. Le vote d'ensemble annoncé pour le 17 novembre est un repère de calendrier, pas un résultat à prédire par ce modèle d'amendements.

Le suivi automatisé doit déclarer ses incidents et son dernier passage effectif. L'absence de nouvelles données ne vaut pas absence de vote. Aucun dépôt de prédiction de censure dans ce chantier ; aucune écriture en base ni déploiement.

## Journal des modifications

- 2026-10-24 : version initiale, écrite avant le premier dépôt du candidat combiné. Les limites sur les votes collectifs et sur les nouveaux députés sont rendues explicites pour ne pas transformer le domaine du modèle en sélection invisible des cas faciles.
