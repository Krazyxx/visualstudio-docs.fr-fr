---
title: Gestion des propriétés des projets et des solutions
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.assetid: 75247EB8-323A-4AFD-A451-6703A03D5D1F
ms.openlocfilehash: c4d4366843a6ea07286c73810f821b41f95e44b9
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2018
---
# <a name="managing-project-and-solution-properties"></a>Gestion des propriétés des projets et des solutions

## <a name="project-options"></a>Options de projet

Les options de projet sont spécifiques à chaque projet, et affectent la façon dont le projet est écrit, généré et exécuté. Ceci contraste avec les préférences de Visual Studio pour Mac (qui définissent des options spécifiques à l’utilisateur) et avec les options des solutions (qui définissent des options pour l’ensemble de la solution). Les options de projet sont stockées dans le fichier projet (.csproj), de façon que les autres développeurs puissent créer et exécuter le projet correctement. Le fait de disposer d’options de projet spécifiques permet à de nombreux développeurs de travailler sur le même document sans compromettre la mise en forme du fichier.

Pour ouvrir les options de projet dans Visual Studio pour Mac, double-cliquez sur le nom du projet, ou cliquez avec le bouton droit pour ouvrir le menu contextuel et sélectionnez **Options** :

 ![Option dans le menu contextuel](media/projects-and-solutions-image2.png)

Les options modifiables sont notamment les options qui sont utilisées pour générer, exécuter et définir le code source, ainsi que les options de gestion de versions.

Les options de projet sont organisées en cinq catégories différentes :

* **Général** : les informations du projet, comme le nom, la description et l’espace de noms par défaut, sont définies ici, ainsi que l’emplacement du projet.
* **Build** : ces options permettent aux développeurs de définir ou de modifier des profils PCL pour les bibliothèques de classes portables. Elles permettent également de définir des commandes, des configurations et des options de compilateur personnalisées. Le chemin de sortie et le nom des assemblys peuvent également être définis ici.
* **Exécuter** : vous permet de créer des configurations de séries de tests personnalisées par projet.
* **Code source** : vous permet de contrôler la mise en forme de nombreux types de fichiers différents et les conventions de nommage. Vous pouvez également définir ici les stratégies de nommage et les styles d’en-tête par défaut.
* **Gestion de version** : vous permet de modifier le style du message de validation lors de l’utilisation de la gestion de versions avec votre projet.

Chaque projet peut contenir des options de projet spécifiques qui dépendent de la plateforme. Par exemple, un projet Xamarin.Android, comme celui qui est illustré dans l’image suivante, a des options relatives à la génération Android, comme les options de l’éditeur de liens, et à l’application, comme les autorisations :

 ![Options de projet Android](media/projects-and-solutions-image5.png)

Xamarin.iOS contient des options relatives à la signature des bundles, comme le profil d’approvisionnement nécessaire à utiliser :

 ![Options de projet iOS](media/projects-and-solutions-image6.png)

## <a name="solution-options"></a>Options de la solution 

Les options de solution sont similaires aux options de projet, mais elles couvrent les solutions entières. Elles permettent de définir les informations sur l’auteur, les paramètres de génération, les styles de mise en forme du code et la gestion de versions, et d’affecter le projet de démarrage dans la solution.  La boîte de dialogue Options de la solution est accessible à partir de l’élément de menu **Projet > Options de la solution**, à partir de l’élément de menu contextuel **Options** sur la solution dans le panneau Solution, ou en double-cliquant sur la solution dans le panneau Solution :

 ![Options de la solution](media/projects-and-solutions-image7.png)
