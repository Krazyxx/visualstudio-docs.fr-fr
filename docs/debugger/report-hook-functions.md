---
title: Fonctions de raccordement de rapport | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- hooks, report
- _CrtDbgReport function
- debugger, report hook functions
- memory allocation, debug heap
- debugging [C++], hook functions
- _CrtSetReportHook function
- report hook functions
ms.assetid: 1854bca7-d7eb-4502-89bf-b1ee64cb50ef
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 562944404d3e02a2e5768fcd74c67302475e6190
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
---
# <a name="report-hook-functions"></a>Fonctions de raccordement de rapport
Une fonction de raccordement de rapport, installée à l’aide de [_CrtSetReportHook](/cpp/c-runtime-library/reference/crtsetreporthook), est appelée chaque fois [_CrtDbgReport](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw) génère un rapport de débogage. Vous pouvez vous en servir, entre autres, pour filtrer les rapports de façon à vous concentrer sur des types d'allocations spécifiques. Une fonction de raccordement de rapport doit avoir un prototype similaire au suivant :  
  
```  
int YourReportHook(int nRptType, char *szMsg, int *retVal);  
```  
  
 Le pointeur que vous passez à **_CrtSetReportHook** est de type **_CRT_REPORT_HOOK**, comme défini dans CRTDBG. H :  
  
```  
typedef int (__cdecl *_CRT_REPORT_HOOK)(int, char *, int *);  
```  
  
 Lorsque la bibliothèque Runtime appelle votre fonction de raccordement, le *nRptType* argument contient la catégorie du rapport (**_CRT_WARN**, **_CRT_ERROR**, ou **_CRT _ASSERT**), *szMsg* contient un pointeur vers une chaîne de message de rapport entièrement assemblé et *retVal* Spécifie si `_CrtDbgReport` doivent poursuivre leur exécution normale Après avoir généré le rapport ou démarrer le débogueur. (A *retVal* l’exécution poursuit la valeur zéro, une valeur de 1 démarre le débogueur.)  
  
 Si le raccordement gère intégralement le message concerné et qu’aucun rapport supplémentaire n’est requis, il doit retourner **TRUE**. Si elle retourne **FALSE**, `_CrtDbgReport` communiquera le message normalement.  
  
## <a name="see-also"></a>Voir aussi  
 [Écriture de fonctions de raccordement de débogage](../debugger/debug-hook-function-writing.md)   
 [crt_dbg2, exemple](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167)