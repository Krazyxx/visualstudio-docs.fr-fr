---
title: Suppression des informations de contrôle de code Source. Proj et. Fichiers sln | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, .sln and .proj files
ms.assetid: 7b06883f-35de-41e2-9a9e-d3edba236f17
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 695a4ccfc5da20bda25c78929488625c244959a8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="removal-of-source-control-information-from-proj-and-sln-files"></a>Suppression des informations de contrôle de code Source. Proj et. Fichiers sln
Dans la version 1.2 de l’API de plug-in du contrôle Source le contrôle de code source, les informations sont stockées dans un MSSCCPRJ. Fichier de contrôle de code source. L’avantage de le MSSCCPRJ. Fichier de contrôle de code source est que les informations de contrôle de code source n'est pas de source - contrôlés, comme dans les fichiers .proj et .sln.  
  
## <a name="version-12-changes"></a>Modifications de la version 1.2  
 Dans le contrôle plug-ins de source qui sont basées sur l’API de plug-in de contrôle de Source de version 1.1, plus d’informations sur le contrôle de code source sont stockés dans le projet (.proj) et les fichiers solution (.sln). L’emplacement de la base de données des informations de contrôle de source est spécifié par le AuxPath, et l’emplacement spécifique dans la base de données est spécifiée par NomProjet. Ce comportement peut provoquer des problèmes après les opérations de copie, branchement ou une branche, car le NomProj généralement ne suivre pas valide après une des opérations suivantes.  
  
 Dans l’API de plug-in du contrôle Source version 1.1, l’IDE utilisée ~ fichiers SAK pour détecter si un plug-in pris en charge la MSSCCPRJ. Méthode de contrôle de code source du stockage des informations de contrôle de code source. L’API de plug-in de contrôle de Source de version 1.2 fournit une nouvelle fonctionnalité de détection de la prise en charge pour MSSCCPRJ. Fichier de contrôle de code source sans utiliser un ~ les fichiers SAK. Pour plus d’informations, consultez [élimination de ~ SAK fichiers](../../extensibility/internals/elimination-of-tilde-sak-files.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Nouveautés dans l’API de plug-in de contrôle de code source version 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)