
# Commencez avec Azure OpenAI Service

Azure OpenAI Service apporte les modèles d'IA générative développés par OpenAI sur la plateforme Azure, vous permettant de développer des solutions d'IA puissantes qui bénéficient de la sécurité, de l'évolutivité et de l'intégration des services fournis par la plateforme cloud Azure. Dans cet exercice, vous apprendrez à démarrer avec Azure OpenAI en provisionnant le service en tant que ressource Azure et en utilisant Azure OpenAI Studio pour déployer et explorer des modèles d'IA générative.

Dans le scénario de cet exercice, vous jouerez le rôle d'un développeur de logiciels chargé de mettre en œuvre un agent d'IA capable d'utiliser l'IA générative pour aider une organisation de marketing à améliorer son efficacité dans la communication avec les clients et la publicité de nouveaux produits. Les techniques utilisées dans l'exercice peuvent être appliquées à tout scénario où une organisation souhaite utiliser des modèles d'IA générative pour aider les employés à être plus efficaces et productifs.

Cet exercice dure environ **30** minutes.

## Provisionner une ressource Azure OpenAI

Si vous n'en avez pas déjà une, provisionnez une ressource Azure OpenAI dans votre abonnement Azure.

1. Connectez-vous au **portail Azure** à l'adresse `https://portal.azure.com`.
2. Créez une ressource **Azure OpenAI** avec les paramètres suivants :
    - **Abonnement** : *Sélectionnez un abonnement Azure qui a été approuvé pour accéder au service Azure OpenAI*
    - **Groupe de ressources** : *Choisissez ou créez un groupe de ressources*
    - **Région** : *Faites un choix **aléatoire** parmi les régions suivantes*\*
        - Australie Est
        - Canada Est
        - États-Unis Est
        - États-Unis Est 2
        - France Centrale
        - Japon Est
        - États-Unis Nord Central
        - Suède Centrale
        - Suisse Nord
        - Royaume-Uni Sud
    - **Nom** : *Un nom unique de votre choix*
    - **Niveau de tarification** : Standard S0

    > \* Les ressources Azure OpenAI sont limitées par des quotas régionaux. Les régions listées incluent un quota par défaut pour le(s) type(s) de modèles utilisé(s) dans cet exercice. Choisir une région de manière aléatoire réduit le risque qu'une seule région atteigne sa limite de quota dans des scénarios où vous partagez un abonnement avec d'autres utilisateurs. En cas de dépassement de quota plus tard dans l'exercice, il est possible que vous deviez créer une autre ressource dans une région différente.

3. Attendez que le déploiement soit terminé. Ensuite, accédez à la ressource Azure OpenAI déployée dans le portail Azure.

## Déployer un modèle

Le service Azure OpenAI propose un portail web nommé **Azure OpenAI Studio**, que vous pouvez utiliser pour déployer, gérer et explorer des modèles. Vous commencerez votre exploration d'Azure OpenAI en utilisant Azure OpenAI Studio pour déployer un modèle.

> **Remarque** : Lors de l'utilisation d'Azure OpenAI Studio, des boîtes de dialogue suggérant des tâches à effectuer peuvent apparaître. Vous pouvez les fermer et suivre les étapes de cet exercice.

1. Dans le portail Azure, sur la page **Aperçu** de votre ressource Azure OpenAI, utilisez le bouton **Accéder à Azure OpenAI Studio** pour ouvrir Azure OpenAI Studio dans un nouvel onglet de navigateur.

    Une fois le nouvel onglet ouvert, vous pouvez fermer les notifications de bannière pour les nouveaux services en avant-première affichés en haut de la page d'Azure OpenAI Studio.

1. Dans Azure OpenAI Studio, dans le volet de gauche, sélectionnez la page **Déploiements** et visualisez vos déploiements de modèles existants. Si vous n'en avez pas déjà un, créez un nouveau déploiement du modèle **gpt-35-turbo-16k** avec les paramètres suivants :
    - **Nom du déploiement** : *Un nom unique de votre choix*
    - **Modèle** : gpt-35-turbo-16k *(si le modèle 16k n'est pas disponible, choisissez gpt-35-turbo)*
    - **Version du modèle** : Mise à jour automatique par défaut
    - **Type de déploiement** : Standard
    - **Limite de débit de jetons par minute** : 5K\*
    - **Filtre de contenu** : Par défaut
    - **Quota dynamique activé** : Activé

    > \* Une limite de débit de 5 000 jetons par minute est plus que suffisante pour compléter cet exercice tout en laissant de la capacité pour d'autres personnes utilisant le même abonnement.

## Utiliser le terrain de jeu Chat

Maintenant que vous avez déployé un modèle, vous pouvez l'utiliser pour générer des réponses basées sur des invites en langage naturel. Le terrain de jeu *Chat* dans Azure OpenAI Studio fournit une interface de chatbot pour les modèles GPT 3.5 et plus récents.

> **Remarque :** Le terrain de jeu *Chat* utilise l'API *ChatCompletions* plutôt que l'ancienne API *Completions* utilisée par le terrain de jeu *Completions*. Le terrain de jeu Completions est fourni pour la compatibilité avec les anciens modèles.

1. Dans la section **Terrain de jeu**, sélectionnez la page **Chat**. La page du terrain de jeu **Chat** se compose de trois panneaux principaux (qui peuvent être disposés de droite à gauche horizontalement, ou de haut en bas verticalement selon la résolution de votre écran) :
    - **Configuration** - utilisé pour définir le contexte des réponses du modèle.
    - **Session de chat** - utilisé pour soumettre des messages de chat et visualiser les réponses.
    - **Configuration** - utilisé pour configurer les paramètres du déploiement du modèle.
1. Dans le panneau **Configuration**, assurez-vous que votre déploiement du modèle gpt-35-turbo-16k est sélectionné.
1. Dans le panneau **Configuration**, examinez le **Message système** par défaut, qui devrait être *Vous êtes un assistant IA qui aide les gens à trouver des informations.* Le message système est inclus dans les invites soumises au modèle et fournit un contexte pour les réponses du modèle ; définissant les attentes quant à la manière dont un agent IA basé sur le modèle doit interagir avec l'utilisateur.
1. Dans le panneau **Session de chat**, saisissez la requête utilisateur `Comment puis-je utiliser l'IA générative pour m'aider à commercialiser un nouveau produit ?`

    > **Remarque** : Vous pouvez recevoir une réponse indiquant que le déploiement de l'API n'est pas encore prêt. Dans ce cas, attendez quelques minutes et réessayez.

1. Examinez la réponse, en notant que le modèle a généré une réponse en langage naturel cohérente et pertinente par rapport à la requête avec laquelle il a été invité.
1. Entrez la requête utilisateur `Quelles compétences dois-je acquérir si je veux développer une solution pour accomplir cela ?`.
1. Examinez la réponse, en notant que la session de chat a conservé le contexte conversationnel (donc "cela" est interprété comme une solution d'IA générative pour le marketing). Cette contextualisation est obtenue en incluant l'historique récent de la conversation dans chaque soumission d'invite successive, de sorte que l'invite envoyée au modèle pour la deuxième requête comprenait la requête et la réponse d'origine ainsi que la nouvelle entrée utilisateur.
1. Dans la barre d'outils du panneau **Session de chat**, sélectionnez **Effacer le chat** et confirmez que vous souhaitez redémarrer la session de chat.
1. Entrez la requête `Pouvez-vous m'aider à trouver des ressources pour acquérir ces compétences ?` et examinez la réponse, qui devrait être une réponse en langage naturel valide, mais comme l'historique du chat précédent a été perdu, la réponse est susceptible d'être axée sur la recherche de ressources génériques plutôt que sur les compétences spécifiques nécessaires pour créer une solution d'IA générative pour le marketing.

## Expérimentez avec des messages système, des invites et des exemples à quelques coups

Jusqu'à présent, vous avez participé à une conversation de chat avec votre modèle basée sur le message système par défaut. Vous pouvez personnaliser la configuration du système pour avoir plus de contrôle sur le type de réponses générées par votre modèle.

1. Dans le panneau **Configuration**, sous **Utiliser un modèle de message système**, sélectionnez le modèle **Assistant à la rédaction marketing** et confirmez que vous souhaitez mettre à jour le message système.
1. Examinez le nouveau message système, qui décrit comment un agent IA devrait utiliser le modèle pour répondre.
1. Dans le panneau **Session de chat**, saisissez la requête utilisateur `Créez une publicité pour une nouvelle brosse à récurer`.
1. Examinez la réponse, qui devrait inclure un texte publicitaire pour une brosse à récurer. Le texte peut être assez étendu et créatif.

    Dans un scénario réel, un professionnel du marketing connaîtrait probablement déjà le nom du produit brosse à récurer ainsi que certaines idées sur les principales caractéristiques à mettre en avant dans une publicité. Pour obtenir les résultats les plus utiles d'un modèle d'IA générative, les utilisateurs doivent concevoir
