---
title: Utilisation de Modules pour inclure des fichiers dans la Solution | Documents Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deployment modules
- SharePoint development in Visual Studio, modules
- modules [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9c11dd4ebd17b1ebef91c3d7752df7c15dd50da4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="using-modules-to-include-files-in-the-solution"></a>Utilisation de modules pour inclure des fichiers dans la solution
  Il peut arriver lorsque vous souhaitez déployer les fichiers sur le serveur SharePoint quel que soit leur type de fichier, telles que de nouvelles pages maîtres. Pour ce faire, vous pouvez utiliser *Modules* (à ne pas confondre avec [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] modules de code). Les modules sont des conteneurs pour les fichiers dans une solution SharePoint. Lorsque la solution est déployée, les fichiers dans le module sont copiés vers les dossiers spécifiés sur le serveur SharePoint.  
  
## <a name="module-items-and-elements"></a>Éléments et les éléments de module  
 Pour créer un module, ajoutez-le à un projet en la sélectionnant dans le **ajouter un nouvel élément** boîte de dialogue. Ensuite, modifiez le fichier Elements.xml pour inclure les noms des fichiers que vous souhaitez déployer, où ils se trouvent sur le système et ils doivent être copiés sur le serveur SharePoint.  
  
 Voici un exemple de fichier Elements.xml pour un module :  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
    <Module Name="Module1">  
        <File Path="Module1\Sample.txt" Url="Module1/Sample.txt" />  
    </Module>  
</Elements>  
  
```  
  
 Les modules nouvellement créés contiennent les fichiers par défaut suivants :  
  
|Nom de fichier|Description|  
|---------------|-----------------|  
|Elements.Xml|Le fichier de définition pour le module.|  
|Sample.txt|Un fichier d’espace réservé qui sert à obtenir un exemple d’un fichier dans le module.|  
  
 Le fichier Elements.xml contient les éléments suivants :  
  
|Nom de l'élément|Description|  
|------------------|-----------------|  
|Éléments|Contient tous les éléments définis dans le module.|  
|Module|L’élément de module possède un attribut unique, *nom*, qui spécifie le nom du module dans le format `<Module Name="Module1">`.<br /><br /> Notez que si vous modifiez le nom du module (ou ses *nom du dossier* propriété), vous devez mettre à jour manuellement le nom de l’élément de Module.<br /><br /> Si vous spécifiez un sous-répertoire pour l’ou les fichiers dans l’élément de Module, [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] (WSS) crée automatiquement une structure de répertoire correspondant pour eux.|  
|Fichier|L’élément du fichier possède deux paramètres, *chemin d’accès* et *Url*.<br /><br /> -Chemin d’accès : Le nom et l’emplacement du fichier dans la solution SharePoint. Le format est, `Path="Module1\Sample.txt"`.<br /><br /> -Url : L’emplacement où le fichier sera déployé sur le serveur SharePoint. Le format est, `Url="Module1/Sample.txt"`.<br /><br /> -Type : Un attribut facultatif qui a deux paramètres : *GhostableInLibrary* et *Ghostable*. Le format est, `Type="GhostableInLibrary"`. Spécification de *GhostableInLibrary* signifie le fichier est ajouté à une bibliothèque de documents dans SharePoint avec un élément de liste pour accompagner le fichier lorsqu’il est ajouté à la bibliothèque. Spécification de *Ghostable* , le fichier à ajouter à l’extérieur de la bibliothèque de documents sur SharePoint.|  
  
 Chaque fichier que vous souhaitez déployer nécessite une `<File>` entrée de l’élément dans le fichier Elements.xml.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : inclure des fichiers à l’aide d’un Module](../sharepoint/how-to-include-files-by-using-a-module.md)   
 [Comment : configurer un fichier](http://go.microsoft.com/fwlink/?LinkID=144271)   
 [Développement de Solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Création de composants WebPart pour SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Empaquetage et déploiement de solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  