---
title: Paramètres de Sites Optimizer
description: Découvrez comment configurer les paramètres de Sites Optimizer et les intégrer à d’autres outils.
TQID: https://experienceleague.adobe.com/eznjSHZgAmCh-ek-XE-lLtuoGJxC0yY4UVrmPjc0KYo
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: 84a1ae98d67bc02ab272131194511efbeccab492
workflow-type: ht
source-wordcount: 749
ht-degree: 100%

---

# Paramètres de Sites Optimizer

![Paramètres de Sites Optimizer](./assets/settings/hero.png){align="center"}

Les paramètres de Sites Optimizer servent de hub central pour configurer votre expérience Sites Optimizer.

## Google Search Console

![Paramètres de Sites Optimizer pour Google Search Console](./assets/settings/google-search-console.png){align="center"}

Le connecteur de paramètres de Google Search Console dans AEM Sites Optimizer permet d’analyser les mesures d’optimisation du moteur de recherche clés telles que les classements de recherche, les taux de clics et les valeurs web principales. En connectant Google Search Console, vous pouvez tirer parti de l’analyse JSON pour découvrir des opportunités d’optimisation et améliorer les performances du site.

Pour configurer ce connecteur, vous devez disposer d’informations d’identification disposant d’un accès administratif à Google Search Console pour le domaine.

## Se connecter à AEM Sites

Ce guide explique comment connecter votre site Edge Delivery Services (EDS) existant à AEM Sites Optimizer. Avant de commencer, assurez-vous que votre site EDS est déjà configuré et fonctionnel. Cette connexion est réservée à AEM Sites Optimizer pour accéder à votre contenu.

La connexion nécessite deux étapes :

1. Fournissez votre URL de référentiel de code et l’URL de la source du contenu.
2. Accordez à AEM Sites Optimizer l’accès à votre source de contenu.

### Étape 1 : associer votre référentiel de code et votre source de contenu

Dans AEM Sites Optimizer, accédez à **Paramètres → Connecter à AEM Sites** et saisissez les informations suivantes :

- **URL du référentiel de code** : URL GitHub de votre site EDS, par exemple :
  `https://github.com/owner/repo`

- **URL de la source du contenu** : URL du dossier SharePoint ou du dossier Google Drive qui soutient votre site EDS, par exemple :
  `https://drive.google.com/drive/folders/...` ou `https://myorg.sharepoint.com/...`

Une fois que vous avez saisi l’URL de la source du contenu, AEM Sites Optimizer détecte le type de votre source de contenu et affiche les instructions d’accès appropriées ci-dessous.

### Étape 2 : accorder l’accès à votre source de contenu

Suivez la section correspondant à votre source de contenu.

#### SharePoint – Domaine Adobe

![Boîte de dialogue Connexion à AEM Sites affichant Aucune action requise pour le domaine Adobe SharePoint](./assets/settings/connect-content-and-drive.png){align="center"}

Si l’URL de la source du contenu utilise le domaine Adobe SharePoint, aucune autre action n’est requise. L’accès est déjà configuré. Cliquez sur **Enregistrer** pour terminer la connexion.

#### SharePoint – Domaine personnalisé

Si l’URL de la source du contenu utilise le domaine SharePoint de votre entreprise, vous devez enregistrer une application Azure et fournir ses informations d’identification à AEM Sites Optimizer.

##### L’objet de votre création

- Autorisation d’enregistrer des applications sur le portail Azure ou contact pouvant enregistrer des applications en votre nom.
- Droits d’administration de locataire pour accorder le consentement de l’API, ou administrateur ou administratrice pouvant approuver le consentement de l’API pour vous.

##### Étape 2a : enregistrer une application dans Azure

1. Accédez à **Portail Azure → Microsoft Entra ID → Enregistrements d’application → Nouvel enregistrement**.
2. Donnez-lui un nom, par exemple : `AEM Sites Optimizer`.
3. Conservez toutes les autres valeurs par défaut et cliquez sur **Enregistrer**.
4. Sur la page **Vue d’ensemble**, notez ce qui suit :
   - **ID d’application (client)**
   - **ID de répertoire (locataire)**

##### Étape 2b : ajouter des autorisations API

1. Accédez à **Autorisations API → Ajouter une autorisation → Microsoft Graph → Autorisations d’application**.
2. Ajoutez les deux éléments suivants :
   - `Sites.Selected` : accès limité à des collections de sites SharePoint spécifiques.
   - `Files.SelectedOperations.Selected` : accès aux fichiers sans utilisateur ou utilisatrice connecté.
3. Cliquez sur **Accorder le consentement d’administration** pour les deux.

![Autorisations d’API Azure affichant Sites.Selected et Files.SelectedOperations.Selected accordées](./assets/settings/app-permissions.png){align="center"}

>[!NOTE]
>
>L’octroi du consentement d’administration nécessite des droits d’administration de locataire. Si vous n’en disposez pas, demandez à votre administrateur ou administratrice informatique ou Azure de terminer cette étape avant de continuer.

##### Étape 2c : créer un secret client

![Page Certificats et secrets Azure pour l’enregistrement de l’application](./assets/settings/create-credentials.png){align="center"}

1. Accédez à **Certificats et secrets → Nouveau secret client**.
2. Définissez une description et une date d’expiration, puis cliquez sur **Ajouter**.
3. Copiez immédiatement la valeur du secret. Elle n’est affichée qu’une seule fois.

##### Étape 2d : accorder à l’application l’accès à votre site SharePoint

Vous pouvez accorder l’accès à l’application à l’aide de Microsoft Graph Explorer, de PowerShell ou des appels directs de l’API Graph.

Accédez à [Microsoft Graph Explorer](https://developer.microsoft.com/graph/graph-explorer), connectez-vous avec votre compte Microsoft et exécutez les requêtes suivantes :

1. Trouver votre ID de site :

```
GET https://graph.microsoft.com/v1.0/sites/{tenant}.sharepoint.com:/sites/{site-name}
```

1. Copiez l’`id` de la réponse, puis accordez l’accès au niveau du site :

```
POST https://graph.microsoft.com/v1.0/sites/{siteId}/permissions
```

Corps :

```json
{
  "roles": ["write"],
  "grantedToIdentities": [{
    "application": {
      "id": "{your-client-id}",
      "displayName": "{Your app name}"
    }
  }]
}
```

##### Étape 2e : saisir les informations d’identification dans AEM Sites Optimizer

![Boîte de dialogue Connecter à AEM Sites affichant les champs d’informations d’identification SharePoint](./assets/settings/add-sharepoint-credentials.png){align="center"}

De retour dans la boîte de dialogue **Connecter à AEM Sites**, saisissez ce qui suit sous **Connexion au référentiel de contenu via SharePoint** :

- **ID de locataire (Azure AD)** : depuis Enregistrement d’application → Vue d’ensemble.
- **ID de client (enregistrement d’application)** : depuis Enregistrement d’application → Vue d’ensemble.
- **Secret client** : créé à l’étape 2c.

Cliquez sur **Valider la connexion** pour confirmer l’accès, puis sur **Enregistrer**.

#### Google Drive

![Boîte de dialogue Connecter à AEM Sites affichant le compte de service Google Drive pour le partage de l’accès](./assets/settings/validate-eds-google.png){align="center"}

1. Dans Google Drive, cliquez avec le bouton droit sur le dossier qui contient votre site EDS et sélectionnez **Partager**.
2. Dans le champ **Ajouter des personnes et des groupes**, saisissez l’adresse e-mail du compte de service affiché dans la boîte de dialogue **Connecter à AEM Sites** :
   `experience-success-studio@helix-225321.iam.gserviceaccount.com`
3. Définissez le niveau d’autorisation sur **Éditeur**.
4. Décochez **Envoyer une notification** et cliquez sur **Envoyer**.

Une fois le partage terminé, cliquez sur **Valider la connexion** dans la boîte de dialogue, puis cliquez sur **Enregistrer**.
