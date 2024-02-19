
# Déploiement d'une Application sur Amazon S3 avec Pipeline

Ce guide vous aidera à mettre en place un pipeline automatisé pour déployer votre application sur Amazon S3. En suivant ces étapes, vous pourrez automatiser le processus de déploiement de votre application et garantir des déploiements fiables et cohérents. Vous pouvez utilsé React ou html/css mais moi j'ai utilisé html j'ai juste crée un pétit site qui affiche que les textes, ici le but n'est pas de créer un site web extravagant  mais plutôt de le déployer sur s3 avec pipeline , si vous voulez faire un beau site vous pouvez le faire c'est votre choix!

## Étapes pour configurer le pipeline


### 1. Création du bucket S3

- Rendez-vous sur la console AWS et accédez au service S3.
- Cliquez sur "Créer un bucket" et suivez les instructions pour créer un nouveau bucket.
- Choisissez un nom unique pour votre bucket et assurez-vous de sélectionner la région appropriée.
- cliquer sur le compartiment créé , ajouter un fichier que vous  appellerez index.html  (dans l'option upload ensuite ajouter un fichier)
- Ensuite allez dans proprietés pour activer l'hebergement d'un site static vous allez cliquer sur modifier ou edit , ensuite activer et écrire dans la case destiné pour index.html.

### 2. Configuration des autorisations

- Assurez-vous que votre bucket est configuré pour permettre l'accès public aux fichiers si nécessaire.
- Donc il faut désactivé l'option bloquer les accès publics
- ensuite mettre un petit code pour permettre l'accès. voici le code que  j'ai utilisé pour mon cas ;
  {
    "Version": "2012-10-17",
    "Statement": [
  {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::essaiestatic/*"
        }
    ]
}
- Allez tester l'application pour voir si ça passe sur votre bucket S3 au cas où  ça ne passe pas  veuillez revoir vos configurations .

### 4. Configuration du pipeline CodePipeline

- Accédez à la console AWS et accédez au service CodePipeline.
- Cliquez sur "Créer un pipeline" et suivez les étapes pour configurer votre pipeline.
- Sélectionnez votre référentiel Git comme source (github version2).
- Configurez les étapes de construction et de déploiement pour copier les fichiers vers votre bucket S3.

### 5. Testez le pipeline

Une fois que le pipeline est configuré, effectuez une modification dans votre référentiel Git pour déclencher le pipeline:
- rentrez dans votre console je ne sais pas si vous utilisez quoi mais moi j'utilise visual studio code . après modifier votre code faîtes le push et rentrez dans votre pipeline pour voir si vos modifications sont pris en compte ,si c'est pris en compte y'aura un check .ensuite actualiser l'url de votre site  et vous verrez votre modification apporté sur le code si c'est le cas donc votre pipeline prend en compte vos push.
- Vérifiez que les fichiers sont correctement déployés dans votre bucket S3.

