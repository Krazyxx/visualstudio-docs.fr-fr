---
title: Gérer les ressources d’une application (.NET)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- msvse_resedit.dlg.SetCustomTool
- msvse_settingsdesigner.err.formatvalue
- msvse_resedit.err.nameblank
- msvse_resedit.err.duplicatename
helpviewer_keywords:
- Resource Designer
- resources [Visual Studio]
- Resources page in Project Designer
- application resources [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fe35a9a0e9b1e4b2e04e978f2b32cb38439b76cd
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="manage-application-resources-net"></a>Gérer les ressources d’une application (.NET)

Les fichiers de ressources sont des fichiers qui font partie d’une application, mais qui ne sont pas compilés, par exemple, des fichiers icône ou des fichiers audio. Comme ces fichiers ne font pas partie du processus de compilation, vous pouvez les modifier sans avoir à recompiler vos fichiers binaires. Si vous envisagez de localiser votre application, vous devez utiliser des fichiers de ressources pour toutes les chaînes et autres ressources qui doivent être modifiées quand vous localisez votre application.

Pour plus d’informations sur les ressources des applications de bureau .NET, consultez [Ressources dans des applications de bureau](/dotnet/framework/resources/index).

## <a name="work-with-resources"></a>Utiliser des ressources

Dans un projet de code managé, ouvrez la fenêtre de propriétés du projet. Vous pouvez ouvrir la fenêtre de propriétés en procédant de l’une des façons suivantes :

- en cliquant avec le bouton droit sur le nœud du projet dans l’**Explorateur de solutions**, puis sélectionnant **Propriétés**
- En tapant « propriétés de projet » dans la fenêtre **Lancement rapide**.
- En choisissant **Alt**+**Entrée** dans la fenêtre **Explorateur de solutions**.

Sélectionnez l’onglet **Ressources** . Vous pouvez ajouter un fichier *.resx* si votre projet n’en contient pas déjà un, ajouter et supprimer différents types de ressources, et modifier des ressources existantes.

## <a name="resources-in-other-project-types"></a>Ressources dans d’autres types de projets

Les ressources dans les projets .NET sont gérées différemment par rapport aux autres types de projets. Pour plus d’informations sur les ressources dans :

- Les applications Plateforme Windows universelle (UWP), consultez [Ressources d’application et le système de gestion de ressources](/windows/uwp/app-resources/).
- Les projets C++, consultez [Utiliser des fichiers de ressources](/cpp/windows/working-with-resource-files) et [Guide pratique pour créer une ressource](/cpp/windows/how-to-create-a-resource).

## <a name="see-also"></a>Voir aussi

- [Ressources dans les applications de bureau (.NET Framework)](/dotnet/framework/resources/index)
