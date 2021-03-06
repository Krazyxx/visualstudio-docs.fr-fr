---
title: Analyse du code pour le code managé dans Visual Studio
ms.date: 03/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.projectpropertypages.codeanalysis
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: b7b992dadb703cf1c4f73830324e9934d7525645
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="overview-of-code-analysis-for-managed-code"></a>Vue d’ensemble de l’analyse du code pour le code managé

Visual Studio 2017 analyse du code managé de deux manières : avec hérité *FxCop* analyse statique d’assemblys managés et avec la plateforme des compilateurs .NET *analyseurs*. Cette rubrique traite de l’analyse statique du code FxCop. Pour plus d’informations sur l’analyse du code à l’aide des analyseurs de plateforme des compilateurs .NET, consultez [des analyseurs de vue d’ensemble de Roslyn](../code-quality/roslyn-analyzers-overview.md).

L'outil d'analyse du code managé analyse les assemblys et signale les informations à leur sujet, notamment les violations des règles de programmation et de design présentées dans les règles de conception de Microsoft .NET Framework.

L'outil d'analyse représente les contrôles effectués lors d'une analyse comme messages d'avertissement. Les messages d'avertissement identifient les problèmes de programmation et de conception pertinents et, si possible, fournissent des informations relatives à leur résolution.

## <a name="ide-integrated-development-environment-integration"></a>Intégration IDE (environnement de développement intégré)

Vous pouvez exécuter l’analyse du code sur votre projet manuellement ou automatiquement.

Pour exécuter l’analyse du code chaque fois que vous générez un projet, sélectionnez **activer l’analyse du Code sur la Build** sur la Page de propriétés du projet. Pour plus d’informations, consultez [Comment : activer et désactiver l’analyse du Code automatique](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

Pour exécuter manuellement l’analyse du code sur un projet, dans la barre de menus, choisissez **analyser** > **exécuter l’analyse du Code** > **exécuter l’analyse du Code sur \<projet >**.

## <a name="rule-sets"></a>Ensembles de règles

Règles d’analyse du code pour le code managé sont regroupés en [ensembles de règles](../code-quality/using-rule-sets-to-group-code-analysis-rules.md). Vous pouvez utiliser un des ensembles de règles standard Microsoft, ou vous pouvez [créer un ensemble de règles personnalisé](../code-quality/how-to-create-a-custom-rule-set.md) pour répondre à un besoin spécifique.

## <a name="suppress-warnings"></a>Supprimer les avertissements

Bien souvent, il est utile d'indiquer qu'un avertissement ne s'applique pas. Cela permet d’informer le développeur et les éventuels réviseurs de code, qu’un avertissement a fait l’objet d’une analyse, puis a été supprimé ou ignoré.

Suppression à la source d’avertissements est implémentée via des attributs personnalisés. Pour supprimer un avertissement, ajoutez l'attribut `SuppressMessage` au code source comme indiqué dans l'exemple suivant :

```csharp
[System.Diagnosis.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]
Public class MyClass
{
   // code
}
```

Pour plus d’informations, consultez [supprimer les avertissements](../code-quality/in-source-suppression-overview.md).

> [!NOTE]
> Si vous migrez un projet vers Visual Studio 2017, vous pouvez être confronté à avec un grand nombre d’avertissements d’analyse du code. Si vous n’êtes pas prêt à résoudre les avertissements que vous souhaitez être productif immédiatement, vous pouvez *base* l’état de l’analyse de votre projet. À partir de la **analyser** menu, sélectionnez **exécuter l’analyse du Code et supprimer les problèmes actifs**.

## <a name="run-code-analysis-as-part-of-check-in-policy"></a>Exécuter l’analyse du code dans le cadre de la stratégie d’archivage

En tant qu'organisation, vous pourriez demander à ce que tous les archivages respectent certaines stratégies. En particulier, vous souhaitez vous assurer que vous suivez ces règles :

- Il n’y a aucune erreur de build dans le code en cours d’archivage.

- Analyse du code est exécutée dans le cadre de la build la plus récente.

Vous pouvez l’effectuer en spécifiant des stratégies d’archivage. Pour plus d’informations, consultez [améliorer la qualité du Code avec les stratégies d’archivage projet d’équipe](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md).

## <a name="team-build-integration"></a>Intégration de Team build

Vous pouvez utiliser les fonctionnalités intégrées du système de génération pour exécuter l’outil d’analyse dans le cadre du processus de génération. Pour plus d’informations, consultez [créer et libérer (VSTS)](/vsts/build-release/index).

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des analyseurs de Roslyn](../code-quality/roslyn-analyzers-overview.md)
- [Utilisation d’ensembles de règles pour regrouper des règles d’analyse du code](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Comment : activer et désactiver l’analyse du Code automatique](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
