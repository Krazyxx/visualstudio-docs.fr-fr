---
title: "Ijsdebug::OpenVirtualProcess, méthode | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJSDebug.OpenVirtualProcess
apilocation: jscript9diag.dll
ms.assetid: 5612bf1b-a4e3-4eaf-ac5e-c2e1f147c395
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f5acb137337e46a6e84f7d68c9330a3ca847f2e5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugopenvirtualprocess-method"></a>IJsDebug::OpenVirtualProcess, méthode
Méthode de fabrique utilisé pour créer un nouvel objet de processus virtuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
 HRESULT OpenVirtualProcess(  
   DWORD processId,  
   UINT64 runtimeJsBaseAddress,  
   IJsDebugDataTarget *pDataTarget,  
   IJsDebugProcess **ppProcess  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `processId`  
 [in] Id du processus à attacher le débogueur.  
  
 `runtimeJsBaseAddress`  
 [in] L’adresse de base à laquelle le runtime JavaScript a chargé dans le processus cible.  
  
 `pDataTarget`  
 [in] Interface fournie pour interroger l’état du processus du débogueur.  
  
 `ppProcess`  
 [out] Nouvel objet de processus de débogage  
  
## <a name="return-value"></a>Valeur de retour  
  
## <a name="remarks"></a>Remarques  
 Retourne E_JsDEBUG_MISMATCHED_RUNTIME si Jscript9diag et Jscript9 ne correspondent pas.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jscript9diag.h  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IJsDebug](../../winscript/reference/ijsdebug-interface.md)