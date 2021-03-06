---
title: Ajout d'extensions à des définitions DSL
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: dc764df3037baeba36666ce896549018d86c2a21
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="add-extensions-to-dsl-definitions"></a>Ajouter des Extensions à des définitions DSL

Extension de définition DSL vous permet de créer un package d’extensions à un langage spécifique à un domaine (DSL). L’extension DSL, qui est contenue dans une Extension d’intégration Visual Studio (VSIX), peut être installée sur l’ordinateur d’un utilisateur de la même manière que DSL. Les fonctionnalités supplémentaires peuvent être activées et désactivées au moment de l’exécution dynamique. DSL n’ont pas à être explicitement conçus pour l’extension, et extensions peuvent être conçues ultérieurement, ou par des tiers, sans modifier l’étendue DSL.

Les extensions DSL peuvent inclure les fonctionnalités suivantes :

-   Propriétés des éléments de modèle et de présentation

-   Décorateurs pour des formes et connecteurs

-   Classes, des relations, des formes et des connecteurs

-   Contraintes de validation

-   Onglets et des éléments de boîte à outils

Un utilisateur d’un langage DSL étendu peut créer et enregistrer un modèle qui contient les instances des fonctionnalités supplémentaires. Le modèle peut être lus par d’autres utilisateurs qui ont installé l’extension appropriée. Les utilisateurs qui n’ont pas installé l’extension ne peut pas utiliser les fonctionnalités supplémentaires, mais ils peuvent mettre à jour et enregistrez un modèle sans perdre les fonctionnalités supplémentaires.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>Voir aussi

- [Billets de blog connexes](https://blogs.msdn.microsoft.com/visualstudioalm/tag/code-index/)
