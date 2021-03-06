---
title: Spécifier le pourcentage d’utilisateurs virtuels qui utilisent les données du cache web pour les tests de charge dans Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, virtual users
ms.assetid: f66d5d43-4121-4487-b27f-d0a0baaf7601
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 66b6ccc1d62cdbf163a67d5c76d310f896766819
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data"></a>Comment : spécifier le pourcentage des utilisateurs virtuels qui utilisent les données du cache Web

Après avoir créé votre test de charge avec **l’Assistant Nouveau test de charge**, vous pouvez modifier les propriétés des scénarios en fonction de vos besoins et de vos objectifs de test avec **l’Éditeur de test de charge**. Pour obtenir une liste complète des propriétés des scénarios de test de charge et leurs descriptions, consultez [Propriétés des scénarios de test de charge](../test/load-test-scenario-properties.md).

La propriété **Pourcentage de nouveaux utilisateurs** est définie dans la fenêtre Propriétés. Vous modifiez des propriétés du scénario de test de charge dans l'éditeur de test de charge.

La propriété **Pourcentage de nouveaux utilisateurs** définit le mode de simulation par le test de charge de la mise en cache qui serait exécutée par un navigateur web. Par défaut, la propriété **Pourcentage de nouveaux utilisateurs** est définie sur 0 %. Si la valeur de la propriété **Pourcentage de nouveaux utilisateurs** est définie sur 100 %, chaque test de performances web exécuté dans un test de charge est traité comme un utilisateur accédant au site web pour la première fois et qui n’a aucun contenu du site web dans le cache de son navigateur provenant de visites antérieures. Par conséquent, toutes les requêtes dans le test Web, y compris toutes les requêtes dépendantes telles que les images, sont téléchargées.

> [!NOTE]
> Lorsque la même ressource pouvant être mise en cache est demandée plus d'une fois dans un test web, les requêtes ne sont pas téléchargées.

Si vous exécutez un test de charge sur un site web présentant un nombre significatif d’utilisateurs ayant déjà accédé au site et disposant donc probablement d’images et d’autre contenu pouvant être mis en cache localement, un paramètre défini sur 100 % pour la propriété **Pourcentage de nouveaux utilisateurs** génère plus de demandes de téléchargement que dans une utilisation réelle. Dans ce cas, vous devez estimer le pourcentage de visites sur votre site web correspondant aux utilisateurs accédant pour la première fois au site web et définir la propriété **Pourcentage de nouveaux utilisateurs** en conséquence.

## <a name="to-specify-the-agents-to-use-for-a-scenario"></a>Pour spécifier les agents à utiliser pour un scénario

1.  Ouvrez un test de charge.

     L’**éditeur de test de charge** s’affiche. L’arborescence du test de charge s’affiche.

2.  Dans le dossier **Scénarios** des arborescences du test de charge, choisissez le nœud de scénario pour lequel vous voulez spécifier les agents à utiliser.

3.  Dans le menu **Affichage**, sélectionnez **Fenêtre Propriétés**.

     Les catégories et les propriétés du scénario sont affichées dans la fenêtre Propriétés.

4.  Définissez la valeur de la propriété **Pourcentage de nouveaux utilisateurs** en entrant un nombre pour le pourcentage de nouveaux utilisateurs.

5.  Une fois que vous avez modifié la propriété, choisissez **Enregistrer** dans le menu **Fichier**. Vous pouvez ensuite exécuter votre test de charge en utilisant la nouvelle valeur de **Pourcentage de nouveaux utilisateurs**.

## <a name="see-also"></a>Voir aussi

- [Modification des scénarios de test de charge](../test/edit-load-test-scenarios.md)
- [Procédure pas à pas : Créer et exécuter un test de charge](../test/walkthrough-create-and-run-a-load-test.md)
- [Contrôleurs de test et agents de test](configure-test-agents-and-controllers-for-load-tests.md)
- [Propriétés des scénarios de test de charge](../test/load-test-scenario-properties.md)
- [Modification des modèles de charge en modèle d’activités des utilisateurs virtuels](../test/edit-load-patterns-to-model-virtual-user-activities.md)