---
title: Diagnostic, espace de noms | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic
helpviewer_keywords:
- Concurrency::diagnostic namespace
ms.assetid: ad786b19-7c4c-46ee-bfb6-c4752b373a09
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 29164c08b03bd23980aad381a1a832b2857309a6
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="diagnostic-namespace"></a>diagnostic, espace de noms
L’espace de noms `diagnostics` fournit des fonctionnalités permettant d’émettre des marqueurs du visualiseur concurrentiel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
namespace diagnostic;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="classes"></a>Classes  
  
|Name|Description|  
|----------|-----------------|  
|[marker_series, classe](../profiling/marker-series-class.md)|Représente un canal série d’événements générés par un fournisseur unique.|  
|[span, classe](../profiling/span-class.md)|Définit une phase de l’application.|  
  
### <a name="enumerations"></a>Énumérations  
  
|Name|Description|  
|----------|-----------------|  
|[marker_importance, énumération](../profiling/marker-importance-enumeration.md)|Représente le niveau d’importance d’un marqueur du visualiseur concurrentiel.|  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête** : cvmarkersobj.h  
  
 **Espace de noms :** Concurrency  
  
## <a name="see-also"></a>Voir aussi  
 [Concurrency, espace de noms (visualiseur concurrentiel)](../profiling/concurrency-namespace-concurrency-visualizer.md)