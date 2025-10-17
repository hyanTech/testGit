# 🚀 Guide de Déploiement Automatique sur cPanel (Repository GitHub)

Ce guide est spécifiquement pour votre cas : repository GitHub cloné sur le serveur cPanel 02switch.

## 📋 Votre Configuration Actuelle

- ✅ Repository GitHub existant
- ✅ Projet cloné sur le serveur cPanel via "Clone a repository"
- 🎯 **Objectif :** Déploiement automatique à chaque push vers GitHub

## 🔧 Configuration Étape par Étape

### Étape 1 : Vérification de votre Configuration Actuelle

1. **Connectez-vous à votre cPanel 02switch**

2. **Accédez à Git Version Control :**
   - Dans le menu cPanel, recherchez "Git Version Control"
   - Cliquez dessus

3. **Vérifiez votre repository existant :**
   - Vous devriez voir votre repository `git_api_test` dans la liste
   - Cliquez sur "Manage" à côté de votre repository

4. **Activez le déploiement automatique :**
   - Cochez "Enable Automatic Deployment"
   - Sélectionnez la branche `main` (ou `master`)
   - Cliquez sur "Update"

### Étape 2 : Configuration du fichier .cpanel.yml

Le fichier `.cpanel.yml` doit être dans votre repository sur le serveur. Vérifiez qu'il est bien présent :

```bash
# Connectez-vous en SSH à votre serveur (si possible)
cd /home/votre_utilisateur/public_html/git_api_test
ls -la .cpanel.yml
```

Si le fichier n'est pas là, créez-le avec le contenu que j'ai fourni.

### Étape 3 : Workflow de Développement

**Voici comment vous allez travailler maintenant :**

1. **Sur votre machine locale :**
   ```bash
   # Clonez le repository depuis GitHub (pas depuis le serveur)
   git clone https://github.com/votre_username/git_api_test.git
   cd git_api_test
   ```

2. **Faites vos modifications :**
   ```bash
   # Éditez vos fichiers...
   # Ajoutez vos modifications
   git add .
   git commit -m "Nouvelle fonctionnalité"
   ```

3. **Poussez vers GitHub :**
   ```bash
   git push origin main
   ```

4. **cPanel déploie automatiquement :**
   - cPanel détecte le push sur GitHub
   - Exécute les tâches du `.cpanel.yml`
   - Votre site est mis à jour !

### Étape 4 : Configuration des clés SSH (si nécessaire)

Si vous avez des problèmes de connexion SSH :

1. **Générez une clé SSH sur votre machine locale :**
   ```bash
   ssh-keygen -t rsa -b 4096 -C "votre_email@example.com"
   ```

2. **Ajoutez la clé publique à votre serveur :**
   - Copiez le contenu de `~/.ssh/id_rsa.pub`
   - Dans cPanel → SSH Access → Manage SSH Keys
   - Importez votre clé publique

## 🚀 Utilisation

### Déploiement automatique
**Voici comment cela fonctionne avec votre configuration :**

1. **Vous travaillez sur votre machine locale**
2. **Vous faites des modifications** et vous les commitez
3. **Vous poussez vers votre serveur** : `git push origin main`
4. **cPanel détecte automatiquement** le push sur le serveur
5. **cPanel exécute** les tâches définies dans `.cpanel.yml`
6. **Votre site est mis à jour** automatiquement

### Déploiement manuel
Dans cPanel Git Version Control :
1. Sélectionnez votre repository
2. Cliquez sur "Pull or Deploy"
3. Sélectionnez la branche
4. Cliquez sur "Deploy"

### Workflow de développement complet
```bash
# 1. Sur votre machine locale - Clonez depuis GitHub
git clone https://github.com/votre_username/git_api_test.git
cd git_api_test

# 2. Faites vos modifications
# Éditez vos fichiers...

# 3. Commitez et poussez vers GitHub
git add .
git commit -m "Nouvelle fonctionnalité"
git push origin main

# 4. cPanel détecte automatiquement le push sur GitHub et déploie !
```

## 📝 Avantages de cette méthode

- ✅ **Intégré à cPanel** - Pas de scripts externes
- ✅ **Interface graphique** - Configuration facile
- ✅ **Sécurisé** - Gestion des permissions automatique
- ✅ **Logs intégrés** - Suivi des déploiements
- ✅ **Rollback facile** - Retour aux versions précédentes

## 🔍 Dépannage

### Vérifier le statut du déploiement
- Dans cPanel Git Version Control, consultez les logs de déploiement
- Vérifiez les permissions des fichiers

### Problèmes courants
1. **Erreur de permissions :** Vérifiez que cPanel a accès au répertoire
2. **Erreur npm :** Vérifiez que Node.js est installé
3. **Erreur de chemin :** Vérifiez les chemins dans `.cpanel.yml`

## 📞 Support

En cas de problème :
1. Consultez les logs dans cPanel Git Version Control
2. Vérifiez la syntaxe du fichier `.cpanel.yml`
3. Contactez le support de votre hébergeur si nécessaire
