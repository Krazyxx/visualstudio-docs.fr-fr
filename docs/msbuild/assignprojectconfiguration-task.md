---
title: Tâche AssignProjectConfiguration | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 09633a0b-8f6f-4aba-8058-7cb4d13ce2c0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d771117829ab8ef37ea495b4862ffa492e686770
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="assignprojectconfiguration-task"></a>Tâche AssignProjectConfiguration
Cette tâche accepte une liste de chaînes de configuration et les affecte aux projets spécifiés.  
  
## <a name="task-parameters"></a>Paramètres de tâche  
 Le tableau ci-dessous décrit les paramètres de la tâche `AssignProjectConfiguration`.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`SolutionConfigurationContents`|Paramètre de sortie `string` facultatif.<br /><br /> Contient une chaîne XML qui contient une configuration de projet pour chaque projet. Les configurations sont affectées aux projets nommés.|  
|`DefaultToVcxPlatformMapping`|Paramètre de sortie `string` facultatif.<br /><br /> Contient la liste des mappages séparés par des points-virgules des noms de plateforme utilisés<br /><br /> par la plupart des types aux types utilisés par les fichiers .vcxproj.<br /><br /> Exemple :<br /><br /> `"AnyCPU=Win32;X86=Win32;X64=X64"`|  
|`VcxToDefaultPlatformMapping`|Facultatif<br /><br /> Paramètre de sortie `string`.<br /><br /> Contient la liste des mappages séparés par des points-virgules des noms de plateforme .vcxproj aux noms de plateforme utilisés par la plupart des types.<br /><br /> Exemple :<br /><br /> `"Win32=AnyCPU;X64=X64"`|  
|`CurrentProjectConfiguration`|Paramètre de sortie `string` facultatif.<br /><br /> Contient la configuration du projet actif.|  
|`CurrentProjectPlatform`|Paramètre de sortie `string` facultatif.<br /><br /> Contient la plateforme du projet actif.|  
|`OnlyReferenceAndBuildProjectsEnabledInSolutionConfiguration`|Paramètre de sortie `bool` facultatif.<br /><br /> Contient un indicateur spécifiant que des références doivent être générées même si elles ont été désactivées dans la configuration du projet.|  
|`ShouldUnsetParentConfigurationAndPlatform`|Paramètre de sortie `bool` facultatif.<br /><br /> Contient un indicateur spécifiant si la définition de la plateforme et de la configuration parente doit être annulée.|  
|`OutputType`|Paramètre de sortie `string` facultatif.<br /><br /> Contient le type de sortie du projet.|  
|`ResolveConfigurationPlatformUsingMappings`|Paramètre de sortie `bool` facultatif.<br /><br /> Contient un indicateur spécifiant si la génération doit utiliser les mappages par défaut pour résoudre la configuration et la plateforme des éléments transmis dans les références de projet.|  
|`AssignedProjects`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Contient la liste des chemins d’accès de référence résolus.|  
|`UnassignedProjects`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Contient la liste des éléments de référence de projet qui n’ont pas pu être résolus en utilisant la liste des sorties déjà résolues.|  
  
## <a name="remarks"></a>Notes  
 En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task>. Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches](../msbuild/msbuild-tasks.md)   
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/msbuild-task-reference.md)