---
title: 'Comment : inclure un Assembly personnalisé dans une fonctionnalité BDC | Documents Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.BDC.Add_Assemblies_Dialog
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], add reference
- Business Data Connectivity service [SharePoint development in Visual Studio], custom assembly
- BDC [SharePoint development in Visual Studio], custom assembly
- BDC [SharePoint development in Visual Studio], add reference
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ab104ee31246a524e2c34c513a66a5f5143d5f55
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-include-a-custom-assembly-in-a-bdc-feature"></a>Comment : inclure un assembly personnalisé dans une fonctionnalité BDC
  Votre projet peut référencer des assemblys à partir d’autres projets dans la même solution. Toutefois, vous devez ajouter ces assemblys dans le fichier de fonctionnalité du projet à l’aide de la **affecter référencé des assemblys à des LobSystems** boîte de dialogue.  
  
### <a name="to-include-a-custom-assembly-in-a-business-data-connectivity-bdc-feature"></a>Pour inclure un assembly personnalisé dans une fonctionnalité de connectivité de données métiers (BDC)  
  
1.  Dans **l’Explorateur de solutions**, choisissez le dossier qui contient le modèle BDC.  
  
2.  Dans le menu **Affichage** , cliquez sur **Fenêtre Propriétés**.  
  
3.  Dans le **propriétés** fenêtre, choisissez le **assemblys** propriété, puis sur le bouton de sélection (![ellipse de concepteur ASP.NET Mobile](../sharepoint/media/mwellipsis.gif "Mobile ASP.NET Ellipse de concepteur")).  
  
     Le **affecter référencé des assemblys à des LobSystems** boîte de dialogue s’affiche.  
  
4.  Dans le **sélectionner un Assembly** , sélectionnez l’assembly personnalisé.  
  
    > [!NOTE]  
    >  Assemblys s’affichent uniquement dans le **affecter référencé des assemblys à des LobSystems** boîte de dialogue si vous avez ajouté une référence au projet qui contient l’assembly. Pour plus d’informations, consultez [Comment : ajouter ou supprimer des références à l’aide de la boîte de dialogue Ajouter une référence](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
5.  Dans le **propriétés de la référence** groupe, ouvrez la liste qui s’affiche pour le **LobSystem étendue** propriété, choisissez le système LOB des méthodes qui utilisent l’assembly personnalisé, puis choisissez le **OK**  bouton.  
  
    > [!NOTE]  
    >  Pour déboguer le code dans l’assembly personnalisé, vous devez ajouter l’assembly au package de solution. Pour plus d’informations, consultez [Comment : ajouter et supprimer des assemblys supplémentaires](../sharepoint/how-to-add-and-remove-additional-assemblies.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : utiliser un fichier de ressources pour spécifier des noms localisés, propriétés et autorisations](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [Comment : ajouter un fichier de modèle BDC existant à un projet SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [Création d’un modèle de connectivité de données métiers](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Comment : créer un modèle BDC](../sharepoint/how-to-create-a-bdc-model.md)   
 [Intégration de données métiers dans SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  