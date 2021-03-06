---
title: IDebugMemoryContext2 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugMemoryContext2
helpviewer_keywords:
- IDebugMemoryContext2 interface
ms.assetid: 3a544c8b-11dc-46bb-8549-261e4ac5bbc4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 26ae199d1fee210559f599cdfe1393aeae5dd169
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugmemorycontext2"></a>IDebugMemoryContext2
Cette interface représente une position dans l’espace d’adressage de l’ordinateur exécutant le programme en cours de débogage.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugMemoryContext2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Le moteur de débogage (DE) implémente cette interface pour représenter une adresse en mémoire.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Un appel à [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) ou [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md) retourne cette interface. En outre, les appels à [ajouter](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md) et [soustraction](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md) retourner de nouvelles copies de cette interface une fois l’opération arithmétique appropriée a été appliquée.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugMemoryContext2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetName](../../../extensibility/debugger/reference/idebugmemorycontext2-getname.md)|Obtient le nom peut être affichée pour un utilisateur pour ce contexte.|  
|[GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)|Obtient des informations qui décrivent ce contexte.|  
|[Ajouter](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md)|Ajoute une valeur spécifiée à l’adresse du contexte actuel pour créer un nouveau contexte.|  
|[Soustraire](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md)|Soustrait une valeur spécifiée à partir de l’adresse du contexte actuel pour créer un nouveau contexte.|  
|[Compare](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)|Compare deux contextes de la manière indiquées par des indicateurs de comparaison.|  
  
## <a name="remarks"></a>Notes  
 Visual Studio **mémoire** fenêtre appels [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) pour obtenir le `IDebugMemoryContext2` interface qui contient l’expression évaluée est utilisée pour l’adresse mémoire. Ce contexte est ensuite transmis à [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) et [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md) pour spécifier l’adresse pour lire ou écrire.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)   
 [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)   
 [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)   
 [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)