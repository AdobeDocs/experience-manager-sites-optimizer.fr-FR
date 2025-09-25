---
title: Configuration en amont
description: Découvrez comment configurer l’extension Preflight pour AEM Sites Optimizer.
source-git-commit: 6e177ef6b9d121ac7484ae118037c7e542f981d8
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 2%

---


# Configuration en amont

L’identification de l’opportunité de contrôle en amont AEM Sites Optimizer nécessite la configuration de l’extension de contrôle en amont dans l’éditeur universel, l’aperçu basé sur les documents ou AEM Cloud Service afin d’exécuter des audits de contrôle en amont sur vos pages avant leur publication.

## Activer l’accès utilisateur

Pour utiliser l’extension de contrôle en amont, assurez-vous que votre utilisateur est affecté à au moins l’un des profils de produit AEM Sites Optimizer suivants dans [Adobe Admin Console ](https://adminconsole.adobe.com) :

* AEM Sites Optimizer - Suggérer automatiquement l’utilisateur
* AEM Sites Optimizer - Optimisation automatique de l’utilisateur

## Activation de l’extension de contrôle en amont

>[!BEGINTABS]

>[!TAB Éditeur universel]

Pour configurer le contrôle en amont dans l’éditeur universel, procédez comme suit :

1. Ouvrez l’**Extension Manager** à l’adresse :
   [https://experience.adobe.com/#/@org/aem/extension-manager/universal-editor](https://experience.adobe.com/#/@org/aem/extension-manager/universal-editor)
1. Recherchez l’extension **AEM Sites Optimizer Preflight** et envoyez une requête pour l’activer.
1. L’équipe Adobe AEM **&#x200B;**&#x200B;examinera et activera l’extension pour votre organisation.
1. Une fois l’extension activée, ouvrez une page dans **Éditeur universel**, par exemple :
   `https://author-p12345-e123456.adobeaemcloud.com/ui#/@org/aem/universal-editor/canvas/author-p12345-e123456.adobeaemcloud.com/content/en/example/home.html`
1. L’**Extension de contrôle en amont**’affiche dans le **rail latéral**.
1. Sélectionnez l’**Extension de contrôle en amont** dans le rail latéral pour lancer un **contrôle en amont** de la page active.

>[!TAB Création basée sur des documents]

Pour configurer le contrôle en amont pour la création basée sur des documents, procédez comme suit :

1. Ajoutez la configuration suivante à `/tools/sidekick/config.json` dans le référentiel GitHub de votre projet Edge Delivery Services :

   ```json
   {
     "plugins": [
       {
         "id": "preflight",
         "titleI18n": {
           "en": "Preflight"
         },
         "environments": ["preview"],
         "event": "preflight"
       }
     ]
   }
   ```

1. Créez un nouveau `/tools/sidekick/aem-sites-optimizer-preflight.js` de fichier et ajoutez le contenu suivant :

   ```javascript
   (function () {
     let isAEMSitesOptimizerPreflightAppLoaded = false;
     function loadAEMSitesOptimizerPreflightApp() {
       const script = document.createElement('script');
       script.src = 'https://experience.adobe.com/solutions/OneAdobe-aem-sites-optimizer-preflight-mfe/static-assets/resources/sidekick/client.js?source=plugin';
       script.onload = function () {
         isAEMSitesOptimizerPreflightAppLoaded = true;
       };
       script.onerror = function () {
         console.error('Error loading AEMSitesOptimizerPreflightApp.');
       };
       document.head.appendChild(script);
     }
   
     function handlePluginButtonClick() {
       if (!isAEMSitesOptimizerPreflightAppLoaded) {
         loadAEMSitesOptimizerPreflightApp();
       }
     }
   
     // Sidekick V1 extension support
     const sidekick = document.querySelector('helix-sidekick');
     if (sidekick) {
       sidekick.addEventListener('custom:preflight', handlePluginButtonClick);
     } else {
       document.addEventListener('sidekick-ready', () => {
         document.querySelector('helix-sidekick')
           .addEventListener('custom:preflight', handlePluginButtonClick);
       }, { once: true });
     }
   
     // Sidekick V2 extension support
     const sidekickV2 = document.querySelector('aem-sidekick');
     if (sidekickV2) {
       sidekickV2.addEventListener('custom:preflight', handlePluginButtonClick);
     } else {
       document.addEventListener('sidekick-ready', () => {
         document.querySelector('aem-sidekick')
           .addEventListener('custom:preflight', handlePluginButtonClick);
       }, { once: true });
     }
   }());
   ```

1. Mettez à jour la fonction `loadLazy()` dans `/scripts/scripts.js` pour importer le script de contrôle en amont pour les URL de prévisualisation :

   ```javascript
   if (window.location.href.includes('.aem.page')) {
      import('../tools/sidekick/aem-sites-optimizer-preflight.js');
   }
   ```

1. Ouvrez l’URL d’aperçu (`*.aem.page`) de la page à auditer.
1. Dans **Sidekick**, cliquez sur le bouton **Contrôle en amont** pour démarrer l’audit de la page active.

>[!TAB Éditeur de page AEM Sites]

Pour utiliser le contrôle en amont dans l’éditeur de page d’AEM Sites, vous pouvez créer un signet dans votre navigateur web. Procédez comme suit :

1. Affichez la **barre de signets** dans votre navigateur web :

   * Appuyez sur **Ctrl+Maj+B** (Windows) ou **Cmd+Maj+B** (Mac).

!. Créez un signet dans votre navigateur :

* Cliquez avec le bouton droit sur la barre des signets et sélectionnez **Nouvelle page** ou **Ajouter un signet**.
* Dans le champ **Adresse (URL)** collez le code suivant :

```javascript
javascript:(function(){const script=document.createElement('script');script.src='https://experience.adobe.com/solutions/OneAdobe-aem-sites-optimizer-preflight-mfe/static-assets/resources/sidekick/client.js?source=bookmarklet&target-source=aem-cloud-service';document.head.appendChild(script);})();
```

1. Nommez le signet **Contrôle en amont** (ou tout autre nom de votre choix).
1. Ouvrez l’URL d’aperçu (`*.aem.page`) de la page que vous souhaitez auditer dans l’éditeur de page d’AEM Sites **&#x200B;**.
1. Cliquez sur le signet **Contrôle en amont** dans la barre des signets pour lancer l’audit de la page active.

>[!ENDTABS]

## Bonnes pratiques

Lors de l’exécution des audits de contrôle en amont, gardez à l’esprit les instructions suivantes :

* Exécutez toujours des audits sur **les pages d’évaluation ou de prévisualisation** avant de les publier en production.
* Donner la priorité à la résolution **problèmes à fort impact** tels que des liens rompus, des balises H1 manquantes ou des liens non sécurisés.
* Assurez-vous **l’authentification est activée** pour les environnements d’évaluation protégés avant d’exécuter des audits.
* Examinez et appliquez les **recommandations de balises meta** pour améliorer les performances d’optimisation du moteur de recherche.
