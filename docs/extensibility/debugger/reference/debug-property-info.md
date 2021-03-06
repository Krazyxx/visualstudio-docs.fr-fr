---
title: DEBUG_PROPERTY_INFO | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- DEBUG_PROPERTY_INFO
helpviewer_keywords:
- DEBUG_PROPERTY_INFO structure
ms.assetid: 5a085d18-62c6-4740-b9e9-3f5db6bfdf7f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4466d74d0e19b898b3c377c67a14f7c39922d915
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="debugpropertyinfo"></a>DEBUG_PROPERTY_INFO
Contient des informations sur une propriété de débogage.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct tagDEBUG_PROPERTY_INFO {   
   DEBUGPROP_INFO_FLAGS dwValidFields;  
   BSTR                 bstrFullName;  
   BSTR                 bstrName;  
   BSTR                 bstrType;  
   BSTR                 bstrValue;  
   IDebugProperty2*     pProperty;  
   DBG_ATTRIB_FLAGS     dwAttrib;  
} DEBUG_PROPERTY_INFO;  
```  
  
```csharp  
public struct DEBUG_PROPERTY_INFO {   
   public uint            dwValidFields;  
   public string          bstrFullName;  
   public string          bstrName;  
   public string          bstrType;  
   public string          bstrValue;  
   public IDebugProperty2 pProperty;  
   public ulong           dwAttrib;  
};  
```  
  
## <a name="members"></a>Membres  
 dwValidFields  
 Une combinaison d’indicateurs à partir de la [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) énumération qui spécifie quels champs sont renseignés.  
  
 bstrFullName  
 Le nom complet de la propriété.  
  
 bstrName  
 Le nom de propriété dans un contexte.  
  
 bstrType argument de type  
 Le type de propriété sous forme de chaîne mise en forme.  
  
 bstrValue Argument de type  
 La valeur de propriété sous forme de chaîne mise en forme.  
  
 pProperty  
 Le [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) objet décrit par cette structure.  
  
 dwAttrib  
 Une combinaison d’indicateurs à partir de la [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) énumération décrivant les attributs de cette propriété.  
  
## <a name="remarks"></a>Notes  
 Une propriété est un objet de nature hiérarchique qui a un nom, le type et la valeur. Par exemple, une propriété peut décrire des variables locales, des paramètres, des variables espionnes et des expressions et des registres.  
  
 Cette structure est passée à la [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) méthode où il est renseigné. Cette structure est également retournée en tant que partie d’une liste de cette structure à partir de la [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) interface qui, à son tour, est retourné à partir d’un appel à la [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) et [ EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) méthodes.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)   
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)   
 [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)