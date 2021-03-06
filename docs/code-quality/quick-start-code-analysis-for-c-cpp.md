---
title: 'Démarrage rapide : analyse du code pour C/C++'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- C/C++ code analysis
- code analysis,C/C++
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: 74d613a5f6fe6470e16c86baa4189b46c6f2727f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="quickstart-code-analysis-for-cc"></a>Démarrage rapide : Analyse du Code pour C/C++

Vous pouvez améliorer la qualité de votre application en exécutant l'analyse de code de manière régulière sur le code C ou C++. Cela peut vous aider à rechercher les problèmes courants, les violations d'une bonne pratique de programmation ou les défauts difficiles à détecter à travers des tests. Les avertissements de l'analyse du code diffèrent des erreurs et des avertissements du compilateur, car l'analyse du code recherche des modèles de code spécifiques qui sont valides, mais qui peuvent créer des problèmes pour vous ou d'autres utilisateurs de votre code.

## <a name="configure-rule-sets-for-a-project"></a>Configurer des ensembles de règles pour un projet

1. Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le nom du projet, puis sélectionnez **propriétés**.

2. Les étapes suivantes sont facultatives :

    1. Dans le **Configuration** et **plateforme** listes, choisissez la plateforme de configuration et la cible de génération.

    2. Par défaut, l'analyse du code ne signale pas d'avertissements pour le code généré automatiquement par les outils externes. Pour afficher les avertissements du code généré, désactivez le **supprimer les résultats du code généré** case à cocher.

        > [!NOTE]
        > Cette option ne supprime pas les erreurs d'analyse du code et les avertissements du code généré qui apparaissent dans les formulaires et les modèles. Vous pouvez afficher et gérer le code source pour un formulaire ou un modèle.

3. Pour exécuter l’analyse du code chaque fois que le projet est généré à l’aide de la configuration sélectionnée, sélectionnez le **activer l’analyse du Code pour C/C++ sur la Build** case à cocher. Vous pouvez également exécuter manuellement l’analyse du code en ouvrant le **analyser** menu, puis en choisissant **exécuter l’analyse du Code sur** *nom_projet*.

4. Dans le **exécuter cet ensemble de règles** liste, effectuez l’une des opérations suivantes :

    - Choisissez l'ensemble de règles que vous souhaitez utiliser.

    - Choisissez  **\<Parcourir... >** pour spécifier une règle personnalisée existante du jeu qui n’est pas dans la liste.

    - Définir un [ensemble de règles personnalisé](../code-quality/how-to-create-a-custom-rule-set.md).

### <a name="standard-cc-rule-sets"></a>Ensembles de règles standard C/C++

Visual Studio inclut deux ensembles de règles standard pour le code natif :

|Ensemble de règles|Description|
|--------------|-----------------|
|Règles minimales recommandées par Microsoft pour les projets natifs|Cet ensemble de règles couvre les problèmes les plus critiques rencontrés dans votre code natif, notamment les failles de sécurité potentielles et les blocages d'application. Vous devez inclure cet ensemble de règles dans tout ensemble de règles personnalisé que vous créez pour vos projets natifs.|
|Règles recommandées natives Microsoft|Cet ensemble de règles couvre une large gamme de problèmes. Il inclut toutes les règles dans l'ensemble Règles minimales recommandées par Microsoft pour les projets natifs.|

## <a name="run-code-analysis"></a>Exécuter l'analyse du code

Dans la page Analyse du code des pages de propriétés du projet, vous pouvez configurer l'analyse du code pour l'exécuter chaque fois que vous générez votre projet. Vous pouvez également exécuter l'analyse du code manuellement.

Pour exécuter l'analyse du code sur une solution :

- Dans le menu **Générer**, choisissez **Exécuter l’analyse du code sur la solution**.

 Pour exécuter l'analyse du code sur un projet :

- Dans l'Explorateur de solutions, choisissez le nom du projet.

- Sur le **générer** menu, choisissez **exécuter l’analyse du Code sur** *nom du projet*.

 Le projet ou la solution est compilé et l'analyse du code est exécutée. Résultats s’affichent dans la liste d’erreurs.

## <a name="analyze-and-resolve-code-analysis-warnings"></a>Analyser et résoudre les avertissements d'analyse du code

Pour analyser un avertissement spécifique, choisissez le titre de l’avertissement dans la liste d’erreurs. L’avertissement se développe pour afficher des informations supplémentaires sur le problème. Dans la mesure du possible, l'analyse du code affiche les numéros de ligne et la logique d'analyse qui a conduit à l'avertissement. Pour plus d’informations sur l’avertissement, y compris les solutions possibles à ce problème, choisissez l’ID d’avertissement pour afficher sa rubrique d’aide en ligne correspondante.

Lorsque vous sélectionnez un avertissement, la ligne de code qui a provoqué l’avertissement est mise en surbrillance dans l’éditeur de code Visual Studio.

Après avoir identifié le problème, vous pouvez le résoudre dans votre code. Ensuite, réexécutez l’analyse du code pour vous assurer que l’avertissement n’apparaît plus dans la liste d’erreurs, et que votre correctif n’a pas généré de n’importe quel nouveaux avertissements.

## <a name="suppress-code-analysis-warnings"></a>Supprimer les avertissements d’analyse du code

Vous pouvez décider, dans certaines situations, de ne pas corriger un avertissement de l'analyse du code. Vous pouvez décider que la résolution de l'avertissement requiert un recodage trop important par rapport à la probabilité que le problème se produise dans une implémentation réelle de votre code. Vous pouvez également estimer que l'analyse utilisée dans l'avertissement est inadéquate pour le contexte particulier. Vous pouvez supprimer des avertissements individuels afin qu’ils n’apparaissent plus dans la liste d’erreurs.

Pour supprimer un avertissement :

1. Si les informations détaillées ne sont pas affichées, choisissez le titre de l’avertissement pour le développer.

2. Choisissez le lien **Actions** au bas de l’avertissement.

3. Choisissez **supprimer le Message** , puis **dans la Source**.

 La suppression d’un message insère `#pragma warning (disable:`*WarningId*`)` qui supprime l’avertissement pour la ligne de code.

## <a name="create-work-items-for-code-analysis-warnings"></a>Créer des éléments de travail pour le code les avertissements d’analyse

Vous pouvez utiliser la fonctionnalité de suivi des éléments de travail pour enregistrer les bogues à partir de Visual Studio. Pour utiliser cette fonctionnalité, vous devez vous connecter à une instance de Team Foundation Server.

**Pour créer un élément de travail pour un ou plusieurs avertissements du code C/C++**

1. Dans la liste d’erreurs, développez et sélectionnez les avertissements

2. Dans le menu contextuel pour les avertissements, choisissez **créer un élément de travail**, puis choisissez le type d’élément de travail.

3. Visual Studio crée un élément de travail unique pour les avertissements sélectionnés et affiche l’élément de travail dans une fenêtre de document de l’IDE.

4. Ajoutez des informations supplémentaires, puis choisissez **enregistrer l’élément de travail**.

## <a name="search-and-filter-code-analysis-results"></a>Rechercher et filtrer les résultats de l’analyse de code

Vous pouvez effectuer une recherche dans de longues listes de messages d'avertissement, et vous pouvez filtrer les avertissements dans les solutions à projets multiples.

- **Pour filtrer des avertissements par titre ou l’id d’avertissement**: entrez le mot clé dans la zone de recherche.

- **Pour filtrer des avertissements par niveau de gravité**: par défaut, messages d’analyse du code sont affectés d’une gravité **avertissement**. Vous pouvez affecter le niveau de gravité d’un ou plusieurs messages en tant que **erreur** dans une règle personnalisée définie. Sur le **gravité** colonne de la **liste d’erreurs**, choisissez la flèche déroulante, puis sur l’icône de filtre. Choisissez **avertissement** ou **erreur** pour afficher uniquement les messages qui sont affectés à la gravité correspondante. Choisissez **sélectionner tout** pour afficher tous les messages.

## <a name="see-also"></a>Voir aussi

[Analyse du code pour C/C++](../code-quality/code-analysis-for-c-cpp-overview.md)