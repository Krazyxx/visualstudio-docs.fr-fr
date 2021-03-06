---
title: ProjectItemFolder, élément | Documents Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItemFolder element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 25d126ab05edccf44642271ed7e379988defe212
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="projectitemfolder-element"></a>ProjectItemFolder, élément
  Représente un dossier mappé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<ProjectItemFolder Target = "Path of SharePoint folder the mapped folder corresponds to"  
    Type = "Type of deployment for the mapped folder" />  
```  
  
## <a name="type"></a>Type  
 **ProjectItemFolderType**  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|**Target**|Requis **xs : String** attribut.<br /><br /> Le chemin d’accès du dossier dans l’installation de SharePoint, le dossier mappé correspond, relatif au dossier racine de déploiement. Dossier racine de déploiement est déterminé par le type de déploiement spécifié par le **Type** attribut.<br /><br /> Pour plus d’informations, consultez les descriptions pour le **le chemin de déploiement** et **racine du déploiement** propriétés de SharePoint dans les éléments de projet [développement de Solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md).|  
|**Type**|Requis **xs : String** attribut.<br /><br /> Le type de déploiement pour le dossier mappé. Pour plus d’informations sur les valeurs possibles, consultez la description de la **Type de déploiement** propriété des éléments de projet SharePoint dans [développement de Solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md).|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|Représente un élément de projet SharePoint. Il s’agit de l’élément racine obligatoire du fichier .spdata.|  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations sur les dossiers mappés, consultez [Comment : ajouter et supprimer les dossiers mappés](../sharepoint/how-to-add-and-remove-mapped-folders.md).  
  
## <a name="element-information"></a>Informations sur les éléments  
  
|||  
|-|-|  
|**Espace de noms**|http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**Nom du schéma**|Schéma d’élément de projet SharePoint|  
|**Fichier de validation**|ProjectItemModelSchema.xsd|  
|**Peut être vide.**|Non|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence du schéma élément de projet SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [Guide pratique pour ajouter et supprimer des dossiers mappés](../sharepoint/how-to-add-and-remove-mapped-folders.md)  
  
  