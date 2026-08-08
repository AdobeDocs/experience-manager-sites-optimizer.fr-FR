---
title: Notes de mise à jour
description: Découvrez les dernières fonctionnalités, améliorations et correctifs de bugs dans Adobe Experience Manager Sites Optimizer.
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: 9af59e18de7ce016778f25d4add450b50e0b1fde
workflow-type: tm+mt
source-wordcount: 1805
ht-degree: 1%

---


# Notes de mise à jour

Cette page présente les dernières mises à jour, les nouvelles fonctionnalités et les améliorations de Adobe Experience Manager Sites Optimizer.

Les fonctionnalités marquées **(Accès anticipé)** sont disponibles sur demande. Contactez votre équipe de compte ou l’ingénieur du succès client pour les activer pour votre organisation.

## Du 1Er Au 19 Juillet 2026

### Nouvelles fonctionnalités

- **Gestion des autorisations (accès anticipé)** — Les utilisateurs dotés de la fonctionnalité Gérer les utilisateurs peuvent désormais contrôler l’accès au site à partir d’un nouvel onglet Autorisations — Rechercher des personnes par nom ou adresse e-mail et accorder ou révoquer des fonctionnalités spécifiques. Les actions qu’un utilisateur n’est pas autorisé à effectuer apparaissent désactivées avec une info-bulle expliquant comment demander l’accès.
- **Badges d’état de déploiement** — Les correctifs marqués comme déployés manuellement affichent désormais un badge « Marqués comme déployés » distinct dans la vue Déployé, ce qui facilite la distinction entre les mises à jour manuelles et les déploiements automatiques.

### Améliorations

- **Correctif automatique pour GitHub (Cloud Manager)** — Le correctif automatique de correctif de code pour des opportunités telles que Core Web Vitals, la sécurité et l’accessibilité des formulaires peut désormais générer des demandes d’extraction sur des référentiels Git Cloud Manager apportez votre propre contenu hébergé sur GitHub, ce qui correspond à la prise en charge existante de GitLab, Bitbucket et Azure DevOps. Le nouveau bouton (bascule) Paramètres permet de contrôler la confirmation de configuration unique de votre site.
- **Correction automatique par branche (Cloud Manager Standard)** : la fonction de correction automatique par branche est désormais disponible pour les référentiels Cloud Manager standard lorsqu’elle est activée pour votre site.
- **Vue déployée : effectuée par** — La vue déployée indique désormais qui a marqué chaque correctif comme déployé et quand son statut a été mis à jour pour la dernière fois, via les nouvelles colonnes « Effectué par » et « Dernier statut mis à jour ».
- **Commentaires sur la déconnexion de Google Ads** — La déconnexion d’un compte Google Ads dans les paramètres affiche désormais l’état « Déconnexion... », avec un message d’erreur « Annulation » si la déconnexion échoue pour que vous puissiez réessayer.

### Correctifs

- L’opportunité Corriger les libellés ARIA affiche désormais l’URL de page correcte dans la boîte de dialogue Détails lorsqu’un correctif s’étend sur plusieurs pages.
- Le message d’information de la boîte de dialogue Ignorer s’affiche désormais correctement, avec le texte correctement aligné, en coréen, en chinois simplifié et en chinois traditionnel.
- Les boîtes de dialogue des pages associées pour Texte de remplacement et Métadonnées non valides ou manquantes se chargent désormais de manière fiable. La vue déployée Métadonnées non valide ou manquante et les correctifs de balises de métadonnées fonctionnent désormais correctement avec le dernier format de suggestion.

## 11-22 Mai 2026

### Nouvelles fonctionnalités

- **Rapport sur les alertes sur le site (accès anticipé)** — Un nouveau rapport sur les alertes sur le site de 90 jours fournit une vue trimestrielle de l&#39;état de votre site, en utilisant des blocs quotidiens codés par couleur pour mettre en évidence les périodes d&#39;alertes élevées afin que vous puissiez rapidement identifier et étudier les tendances au fil du temps.
- **Intégration de la télémétrie opérationnelle** — Les sites qui n’ont pas encore connecté les données de télémétrie opérationnelle reçoivent désormais une bannière persistante sur la page d’accueil et une boîte de dialogue d’intégration guidée pour terminer la configuration, ce qui vous garantit une visibilité complète des performances en temps réel de l’utilisateur.
- **Texte de remplacement : sensibilisation à Multi-Site Manager** — Lors de la génération de correctifs de texte de remplacement pour les sites qui utilisent AEM Multi-Site Manager ou la copie de langue, Sites Optimizer vérifie désormais si les correctifs peuvent être appliqués en toute sécurité à chaque variante de langue avant de les suggérer.

### Améliorations

- **Exactitude du texte de remplacement** — Les suggestions de texte de remplacement s’appuient désormais sur le signal d’audit le plus récent et les problèmes détectés à nouveau sont affichés dans les onglets Problèmes actuels et Déployés pour obtenir une vue d’ensemble.

### Correctifs

- L’état du bouton Déployer indique désormais correctement si un correctif peut être déployé.
- Le thème sombre est désormais correctement appliqué lors de l’actualisation de la page.
- Les rapports affichent les dates dans les paramètres régionaux de l’utilisateur.
- Les préférences régionales pour la langue et le format de nombre/date peuvent désormais être configurées indépendamment.
- Le texte secondaire de l’image endommagée est désormais accessible aux lecteurs d’écran.

## Du 21 Avril Au 10 Mai 2026

### Nouvelles fonctionnalités

- **Aucun état d’intégration du site** — Les clients qui n’ont pas encore ajouté de site reçoivent désormais une invite claire et exploitable sur la page d’accueil pour commencer rapidement.
- **Documentation dans le centre d’aide** — La documentation d’AEM Sites Optimizer sur Experience League est désormais accessible directement à partir du centre d’aide in-app, sans quitter le produit.

### Correctifs

- Les sites sans suggestions actives affichent désormais correctement une boîte de dialogue Action requise.
- Les suggestions ignorées s’affichent désormais correctement dans l’onglet Ignorés .
- Les listes déroulantes du sélecteur de trafic payant ne tronquent plus le texte traduit.
- Le sélecteur de page du plan de site est désormais correctement dimensionné.

## Du 13 Mars Au 20 Avril 2026

### Nouvelles fonctionnalités

- **Intégration d’essais** — Les nouveaux utilisateurs d’essais bénéficient désormais d’un flux de configuration guidé : saisissez votre domaine, attendez l’analyse, puis explorez vos premières opportunités. Aucune configuration n’est nécessaire pour commencer.
- **Page des opportunités d’évaluation** — Les utilisateurs de la version d’évaluation peuvent rechercher, trier et filtrer les opportunités. Trois suggestions sont déverrouillées et les suggestions restantes s’affichent dans un aperçu verrouillé avec une invite de mise à niveau.
- **Progression de l’optimisation mensuelle** — Une barre de progression sur la page d’accueil effectue le suivi du nombre d’actions d’optimisation effectuées ce mois-ci, ce qui vous permet de respecter les objectifs d’intégrité de votre site.
- **URL de la cible d’audit (accès anticipé)** — Sous Paramètres, vous pouvez désormais spécifier jusqu’à 100 URL personnalisées pour vous assurer que ces pages sont toujours incluses dans les audits.
- **Configuration du type de diffusion** — Les paramètres vous permettent désormais de spécifier le type de diffusion de votre site (Edge Delivery Services, AEM Cloud Service ou AEM Managed Services) et de connecter votre fournisseur de contenu.
- **Reconception de Core Web Vitals** — L’opportunité Core Web Vitals a été repensée avec la liaison Jira, le téléchargement CSV et la prise en charge multi-sélection des actions par lots.
- **Tableau unifié de liens retour rompus** — Les liens retour rompus provenant de toutes les sources sont désormais affichés dans un seul tableau unifié, avec la possibilité d’exporter directement des règles de redirection CDN.
- **Pas de CTA au-dessus du pli : déployer sur l’instance de création** — Les correctifs de l’opportunité Pas de CTA au-dessus du pli peuvent désormais être déployés directement sur l’instance de création AEM.
- **Déploiement d’un correctif automatique Forms** — Les correctifs d’opportunités Forms peuvent désormais être déployés directement sur l’instance de création AEM.
- **Prise en charge d’AEM Multi-Site Manager** — Les opportunités qui affectent plusieurs copies de langue d’un site indiquent désormais à quel site racine le correctif a été appliqué, à l’aide d’une colonne « Fixe à ».
- **Ignorer les correctifs ayant échoué** — Vous pouvez désormais ignorer les correctifs individuels dont le déploiement a échoué, ce qui permet de débloquer votre workflow.
- **Ouvrir dans l’éditeur AEM** — Les suggestions d’opportunités incluent désormais un lien direct pour ouvrir la page concernée dans l’éditeur visuel AEM afin d’effectuer des modifications rapides sur la ligne.

## Du 28 Février Au 13 Mars 2026

### Nouvelles fonctionnalités

- **Opportunité de correspondance d’intention d’annonce publicitaire** — Un nouveau type d’opportunité identifie les pages de destination de trafic payant qui ne sont pas converties, le taux de rebond de l’affichage, le coût par clic et les mesures de trafic afin de vous aider à hiérarchiser les améliorations des pages de destination.
- **Pas de CTA au-dessus du pli** — Cette opportunité est désormais un type de première classe dédié avec sa propre page de détails et son propre filtrage, ce qui facilite le suivi et la hiérarchisation des améliorations de conversion.
- **Suggestions d’URL de plan de site** — L’opportunité de plan de site suggère désormais des URL de remplacement pour les pages renvoyant des erreurs 404, ce qui facilite la correction des entrées de plan de site rompues.
- **Reconception des liens retour rompus** — La page détaillée des liens retour rompus a été repensée pour une plus grande clarté et convivialité.

### Améliorations

- **Pages de recherche organiques les plus consultées V2** — Les données de trafic organiques proviennent désormais d’un jeu de données Ahrefs de 30 jours, ce qui fournit des informations plus complètes et exploitables sur les performances des recherches.
- **Vulnérabilités de sécurité : arborescence des dépendances** — Les détails des vulnérabilités de sécurité incluent désormais une visualisation sous forme d’arborescence des dépendances afin que vous puissiez comprendre l’impact complet d’une vulnérabilité dans l’ensemble de votre projet.

## Du 14 Au 27 Février 2026

### Nouvelles fonctionnalités

- **Principales pages de recherche organiques** — Site Health Monitor comprend désormais un onglet dédié affichant les principales pages de trafic organique de votre site, ce qui vous donne une visibilité sur le contenu qui génère le plus de trafic de recherche.
- **Correctif automatique de texte de remplacement V2** — Avant de déployer un correctif de texte de remplacement, vous pouvez exécuter une évaluation « Vérifier la fixabilité » avant le vol pour vérifier que le correctif peut être appliqué avec succès à votre contenu.
- **Affichage déployé pour le texte de remplacement** — Les correctifs de texte de remplacement apparaissent désormais dans un onglet Déployé , ce qui vous donne un historique complet des améliorations d’accessibilité, ainsi que des problèmes en suspens actuels.
- **Porte de déploiement d’organisation externe** — Lors du déploiement de correctifs sur un site géré en externe, une étape de confirmation explicite est désormais requise afin d’éviter tout changement accidentel.

### Améliorations

- **Exemptions d’URL de balises Meta** — Des URL spécifiques peuvent désormais être exclues de la validation des balises Meta via la configuration, ce qui réduit les faux positifs pour les titres intentionnellement courts ou non standard.
- **Filtrage d’URL avancé** — Les listes d’opportunités prennent désormais en charge la correspondance des préfixes de sous-itinéraire lors du filtrage par URL, ce qui facilite la mise au point sur des sections spécifiques de votre site.
- **Graphiques de tendances améliorés** — Les graphiques de tendances du trafic gèrent désormais correctement les données d&#39;une année sur l&#39;autre, supprimant les creux trompeurs aux limites de l&#39;année.

## 6-13 Février 2026

### Nouvelles fonctionnalités

- **Mode de maintenance** — Sites Optimizer gère désormais les fenêtres de maintenance planifiée avec élégance, affichant un message d’état clair au lieu de données incomplètes ou trompeuses pendant les temps d’arrêt.
- **Affichage déployé pour les liens retour rompus** — Les liens retour fixes sont désormais suivis dans un onglet Déployé, regroupés par date, afin que vous puissiez voir votre historique de correction en un coup d&#39;œil.
- **Pas de CTA au-dessus du pli de l’opportunité** — Un nouveau type d’opportunité survole les pages où aucun call-to-action clair n’est visible au-dessus du pli, ce qui vous permet d’identifier et d’améliorer les pages à faible potentiel de conversion.
- **Intégration Jira pour l’accessibilité et le contraste des couleurs (accès anticipé)** — Les opportunités d’accessibilité de Forms et du contraste des couleurs peuvent désormais être liées directement aux tickets Jira pour un suivi des problèmes rationalisé dans votre workflow existant.

### Améliorations

- **Vues déployées pour Meta Tags et sécurité** — Les balises Meta et les opportunités de sécurité incluent désormais des onglets Déployés groupés par dates, cohérents avec les autres types d’opportunités.
- **Suivi du déploiement du texte de remplacement** — « Marquer comme déployé » est désormais disponible pour les correctifs de texte de remplacement et le texte de remplacement modifié manuellement est conservé lors des exécutions de nouvelle analyse.

## Du 26 Janvier Au 6 Février 2026

### Nouvelles fonctionnalités

- **Vue déployée pour Canonique et Hreflang** — Les modifications apportées aux opportunités Canoniques et Hreflang sont désormais regroupées par date de déploiement dans un onglet Déployé, vous donnant un historique clair de ce qui a été corrigé et quand.
- **Exportation CSV** — Vous pouvez désormais exporter les données d’opportunité pour les opportunités High Organic Low CTR et Forms au format CSV pour une analyse et un compte rendu des performances hors ligne.
- **Opportunités favorites** — Démarrez toute opportunité à partir de son en-tête pour l’ajouter à vos favoris, ce qui permet de revenir plus rapidement aux opportunités sur lesquelles vous travaillez activement.
- **Vue déployée pour les chaînes de redirection** — Les correctifs de chaînes de redirection peuvent désormais être marqués comme Déployés directement à partir de la page de détails.

### Améliorations

- **Amélioration des estimations de coût de la bannière de cookie** — Les calculs de coût pour l’opportunité de bannière de cookie ont été affinés pour une plus grande précision.

## 16-23 Janvier 2026

### Nouvelles fonctionnalités

- **Site Health Monitor (disponibilité générale)** — Site Health Monitor est désormais disponible pour tous les clients et fournit une vue continue de l’intégrité des performances de votre site. Les nouveaux sites sont configurés automatiquement lors de l’intégration.
- **Prise en charge des sous-chemins d’accès au site** — Les sites étendus à des sous-chemins d’accès URL spécifiques sont désormais entièrement pris en charge dans Site Health Monitor.

### Améliorations

- **Avis de suffisance des données exploitables** — Les opportunités de trafic payant avec moins de 1 000 pages vues affichent désormais un avis de suffisance des données, ce qui vous permet de concentrer les efforts d’optimisation lorsque les données de trafic sont statistiquement significatives.
- **Validation flexible des titres Meta** — Le nombre minimum de caractères requis pour les méta-titres a été réduit, ce qui vous offre davantage de flexibilité dans la conception de titres de page concis.
- **Boîte de dialogue Nouveautés localisée** — La boîte de dialogue Annonces des fonctionnalités in-app s’affiche désormais dans la langue de votre choix.
- **Badge publié** — Les variations de l’opportunité Taux de clics faible organique élevé qui ont été déployées affichent désormais un badge « Publié », ce qui facilite la distinction entre les modifications actives et en attente.
- **Liens de demande d’extraction dans l’accessibilité** — L’onglet Déployé de l’opportunité d’accessibilité affiche désormais l’URL de demande d’extraction associée à chaque correctif, ce qui facilite le suivi des modifications apportées à votre historique de contrôle de code source.
