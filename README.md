# DLC Alerte — Android

Application Android (Java) pour scanner les codes-barres, enregistrer les lots et recevoir des alertes de DLC.

## Installation / compilation sur GitHub
1. Créer un dépôt GitHub vide, puis envoyer **tout le contenu** de ce dossier à la racine du dépôt, y compris `.github/workflows/android.yml`.
2. Ouvrir l'onglet **Actions**, choisir **Compiler APK Android**, puis **Run workflow** (ou pousser un commit sur main).
3. Attendre le succès de la compilation, ouvrir le workflow et télécharger l'artefact **DLC-Alerte-APK**.
4. Décompresser le ZIP, transférer `app-debug.apk` sur le téléphone Android et l'installer en autorisant cette source si nécessaire.

## Fonctionnement
- Scanner avec la caméra (ZXing), puis saisir nom, quantité et date limite.
- Un code EAN ordinaire ne contient généralement pas la DLC.
- Données stockées localement (SQLite), sans compte ni connexion internet.
- Contrôle périodique via WorkManager, environ toutes les 12 heures (l'heure exacte n'est pas garantie par Android). Notification quotidienne à partir de J-7, y compris après expiration.
- Android 13+ : accepter les notifications. Android peut retarder les tâches en arrière-plan selon l'économie d'énergie.

## Compilation locale
Ouvrir le dossier dans Android Studio (JDK 17), synchroniser Gradle, puis Build > Build APK(s).

## Limites version 1
La date doit être saisie manuellement; le nom n'est pas récupéré automatiquement depuis une base produit. Pas de synchronisation entre téléphones.
