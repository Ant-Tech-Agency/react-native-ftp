# @anttech/react-native-ftp

Bibliothèque de service FTP pour React Native

## Prérequis système

- Node.js >= 16
- React Native >= 0.70.0
- iOS : Xcode >= 14.0
- Android : Android Studio avec Android SDK

## Installation

### 1. Installation de la bibliothèque

````sh
# Utiliser npm
npm install @anttech/react-native-ftp

# Ou utiliser yarn
yarn add @anttech/react-native-ftp

### 2. Configuration iOS

```sh
cd ios && pod install
````

## Utilisation

### 1. Connexion FTP

```js
import FtpService from '@anttech/react-native-ftp';

// Se connecter au serveur FTP
const connect = async () => {
  try {
    await FtpService.setup(host, port, username, password);
    console.log('Connexion réussie');
  } catch (error) {
    console.error('Erreur de connexion :', error);
  }
};
```

### 2. Lister les fichiers et dossiers

```js
// Lister les fichiers dans le dossier
const listFiles = async (path = '/') => {
  try {
    const files = await FtpService.listFiles(path);
    console.log('Liste des fichiers :', files);
  } catch (error) {
    console.error('Erreur lors de la liste des fichiers :', error);
  }
};
```

### 3. Télécharger un fichier

```js
// Télécharger un fichier vers le serveur
const uploadFile = async (localPath, remotePath) => {
  try {
    const result = await FtpService.uploadFile(localPath, remotePath);
    console.log('Téléchargement réussi :', result);
  } catch (error) {
    console.error('Erreur de téléchargement :', error);
  }
};
```

### 4. Télécharger un fichier

```js
// Télécharger un fichier depuis le serveur
const downloadFile = async (remotePath, localPath) => {
  try {
    const result = await FtpService.downloadFile(remotePath, localPath);
    console.log('Téléchargement réussi :', result);
  } catch (error) {
    console.error('Erreur de téléchargement :', error);
  }
};
```

### 5. Créer un nouveau dossier

```js
// Créer un nouveau dossier
const createDirectory = async (path) => {
  try {
    await FtpService.makeDirectory(path);
    console.log('Création du dossier réussie');
  } catch (error) {
    console.error('Erreur lors de la création du dossier :', error);
  }
};
```

### 6. Supprimer un fichier ou un dossier

```js
// Supprimer un fichier
const deleteFile = async (path) => {
  try {
    await FtpService.deleteFile(path);
    console.log('Suppression du fichier réussie');
  } catch (error) {
    console.error('Erreur lors de la suppression du fichier :', error);
  }
};

// Supprimer un dossier
const deleteDirectory = async (path) => {
  try {
    await FtpService.deleteDirectory(path);
    console.log('Suppression du dossier réussie');
  } catch (error) {
    console.error('Erreur lors de la suppression du dossier :', error);
  }
};
```

### 7. Renommer un fichier ou un dossier

```js
// Renommer un fichier ou un dossier
const rename = async (oldPath, newPath) => {
  try {
    await FtpService.rename(oldPath, newPath);
    console.log('Renommage réussi');
  } catch (error) {
    console.error('Erreur lors du renommage :', error);
  }
};
```

### 8. Suivre la progression

```js
// Ajouter un listener pour suivre la progression
const removeListener = FtpService.addProgressListener((info) => {
  console.log('Progression :', info.percentage);
});

// Supprimer le listener lorsque ce n'est plus nécessaire
removeListener();
```

### 9. Mettre en pause et reprendre une tâche

```js
// Créer un token pour suivre la tâche
const token = FtpService.makeProgressToken(localPath, remotePath);

// Mettre la tâche en pause
const pauseTask = async () => {
  try {
    await FtpService.cancelUploadFile(token);
    console.log('Tâche mise en pause');
  } catch (error) {
    console.error('Erreur lors de la mise en pause :', error);
  }
};
```

## Exemple complet

Vous pouvez consulter l'exemple complet dans le dossier `example/` du projet.

## Contribution

Consultez le guide de contribution sur [CONTRIBUTING.md](CONTRIBUTING.md) pour savoir comment contribuer au dépôt et au processus de développement.

## Licence

MIT

---
