# Créer une vue personnalisée DNS dans l'Event Viewer

Cette marche à suivre décrit les étapes nécessaires pour configurer une vue personnalisée dans l'Event Viewer de Windows Server afin de surveiller les événements liés au service DNS.

## Prérequis

- Une machine Windows Server avec le rôle DNS installé.
- Le fichier XML d'exportation de la vue personnalisée sera nommé **"surveillance DNS.xml"**.

## Étapes pour créer la vue personnalisée

1. **Ouvrir l'Event Viewer** :
   - Appuyez sur **Windows + R** pour ouvrir la boîte de dialogue "Exécuter".
   - Tapez `eventvwr` et appuyez sur **Entrée**.

2. **Accéder à la section des vues personnalisées** :
   - Dans l'Event Viewer, dans le panneau de gauche, cliquez sur **Custom Views** (Vues personnalisées).
   
3. **Créer une nouvelle vue personnalisée** :
   - Cliquez avec le bouton droit sur **Custom Views** et sélectionnez **Create Custom View** (Créer une vue personnalisée).

4. **Configurer les critères de filtrage** :
   - Dans la fenêtre **Create Custom View**, configurez les paramètres comme suit :
     - **Log level (Niveaux de journal)** : Cochez les cases pour les niveaux suivants :
       - **Critical (Critique)**
       - **Error (Erreur)**
       - **Warning (Avertissement)**
       - **Information (Information)**
     - **Event sources (Sources d'événements)** : Cochez les cases suivantes :
       - **DNS-Server-Service**
       - **DNS Client Events**
     - **Event IDs (ID d'événements)** : Ajoutez les identifiants d'événements suivants :
       - **2** : Démarrage du serveur DNS
       - **4** : Arrêt du serveur DNS
       - **409** : Erreur de résolution de nom
       - **501-502** : Échec de chargement de zone
       - **6001-6002** : Problèmes de réplication DNS

5. **Nommer et sauvegarder la vue** :
   - Donnez un nom descriptif à la vue personnalisée, par exemple **Surveillance DNS**.
   - Cliquez sur **OK** pour enregistrer la vue personnalisée.

6. **Exporter la vue personnalisée** :
   - Cliquez avec le bouton droit sur la vue personnalisée **Surveillance DNS** dans le panneau de gauche.
   - Sélectionnez **Export Custom View** (Exporter la vue personnalisée).
   - Choisissez un emplacement pour sauvegarder le fichier XML et nommez-le **surveillance DNS.xml**.
   - Cliquez sur **Enregistrer**.

## Importer la vue personnalisée sur un autre serveur

1. **Ouvrir l'Event Viewer** sur un autre serveur Windows.
2. Allez dans **Custom Views** (Vues personnalisées).
3. Cliquez avec le bouton droit sur **Custom Views** et sélectionnez **Import Custom View** (Importer une vue personnalisée).
4. Sélectionnez le fichier XML **surveillance DNS.xml** que vous avez exporté précédemment.
5. Cliquez sur **OK** pour importer la vue personnalisée.

Votre vue personnalisée **Surveillance DNS** sera maintenant disponible dans l'Event Viewer pour surveiller spécifiquement les événements du service DNS.

