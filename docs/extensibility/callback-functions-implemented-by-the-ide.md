---
title: Fonctions de rappel implémentées par l’IDE | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, callback functions
- callback functions, source control plug-ins
ms.assetid: 4a8833f0-6ac0-4ea7-9400-8275aa991468
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ffdcc7d92770f486f9a345acf14e12e14214a2b1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="callback-functions-implemented-by-the-ide"></a>Fonctions de rappel implémentées par l’IDE
Pour faciliter l’intégration avec l’environnement de développement intégré (IDE) comme transparente que possible et pour fournir une expérience unifiée de l’utilisateur final, le plug-in de contrôle de code source peut utiliser les fonctions de rappel qui sont implémentées par l’IDE. Le plug-in peut appeler ces fonctions à des moments appropriés pendant une opération de contrôle de code source pour passer des informations à l’IDE ; l’IDE peut ensuite afficher ces informations en tant qu’éléments incorporés dans son interface utilisateur native. L’utilisateur profite d’une expérience moins fragmentée dans ce scénario que si le plug-in employé sa propre interface utilisateur.  
  
 Le fichier d’en-tête requis est scc.h. L’emplacement par défaut est \Program Files\VSIP 8.0\EnvSDK\common\inc\\. Il est également dans le dossier VSIP doté de l’exemple de plug-in de contrôle de code source à \Program Files\VSIP 8.0\MSSCCI\\.  
  
## <a name="in-this-section"></a>Dans cette section  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 Décrit la fonction de rappel qui est utilisée par [SccOpenProject](../extensibility/sccopenproject-function.md) pour afficher les messages de contrôle de source de plug-in via l’IDE.  
  
 [POPLISTFUNC](../extensibility/poplistfunc.md)  
 Décrit la fonction de rappel qui est utilisée par [SccPopulateList](../extensibility/sccpopulatelist-function.md) lorsque l’IDE n’a pas d’accès complet aux informations qui est disponibles uniquement pour le plug-in, telle qu’une liste complète des fichiers sous contrôle de version de contrôle de code source.  
  
 [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)  
 Décrit la fonction de rappel qui est utilisée par le [SccQueryChanges](../extensibility/sccquerychanges-function.md) opération.  
  
 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)  
 Décrit la fonction de rappel qui est utilisée par le [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) opération.  
  
 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)  
 Décrit la fonction de rappel définie par un appel à la [SccSetOption](../extensibility/sccsetoption-function.md) qui permet le contrôle de source de plug-in pour communiquer des modifications de nom dans l’IDE.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [SccOpenProject](../extensibility/sccopenproject-function.md)  
 Ouvre un projet.  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 Examine la liste des fichiers pour leur état actuel. Utilise en outre, le `pfnPopulate` fonction pour notifier l’appelant quand un fichier ne correspond pas les critères pour le `nCommand`.  
  
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)  
 Examine la liste des répertoires et des fichiers dans un projet ou les projets qui sont sous contrôle de code source. Chaque nom de répertoire et fichier trouvé est passé à une fonction de rappel.  
  
 [SccQueryChanges](../extensibility/sccquerychanges-function.md)  
 Examine les modifications de noms qui ont été apportées à une liste de fichiers. Chaque nom de fichier est passé à une fonction de rappel avec son état de modification.  
  
 [SccSetOption](../extensibility/sccsetoption-function.md)  
 Définit un large éventail d’options. Chaque option commence par `SCC_OPT_xxx` et a son propre jeu défini de valeurs.  
  
 [Plug-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)  
 Décrit le contenu de la section de référence du SDK de plug-in de contrôle Source.