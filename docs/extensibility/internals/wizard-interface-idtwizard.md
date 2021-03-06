---
title: Interface de l’Assistant (IDTWizard) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDTWizard interface
- wizards, interface
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7ebb605ed61cc06ef70fde97f3d5831c6d5c4503
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="wizard-interface-idtwizard"></a>Interface de l’Assistant (IDTWizard)
L’environnement de développement intégré (IDE) utilise le <xref:EnvDTE.IDTWizard> interface pour communiquer avec les Assistants. Assistants doivent implémenter cette interface afin d’être installé dans l’IDE.  
  
 Le <xref:EnvDTE.IDTWizard.Execute%2A> est la seule méthode associée à la <xref:EnvDTE.IDTWizard> interface. Assistants implémentent cette méthode et l’IDE appelle la méthode sur l’interface. L’exemple suivant montre la signature de la méthode.  
  
```  
/* IDTWizard Method */  
STDMETHOD(Execute)(THIS_  
   /* [in] */ IDispatch *Application,  
   /* [in] */ long hwndOwner,  
   /* [in] */ SAFEARRAY * *ContextParams,  
   /* [in] */ SAFEARRAY * *CustomParams,  
   /* [out] [in] */ wizardResult *RetVal  
   );  
```  
  
 Le mécanisme de démarrage est similaire à la fois pour le **nouveau projet** et **ajouter un nouvel élément**Assistants. Pour démarrer le, vous appelez le <xref:EnvDTE.IDTWizard> interface définie dans Dteinternal.h. La seule différence est l’ensemble de contexte et des paramètres personnalisés qui sont passés à l’interface lorsque l’interface est appelée.  
  
 Les informations suivantes décrivent les <xref:EnvDTE.IDTWizard> interface Assistants doivent implémenter pour travailler dans le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Les appels de l’IDE le <xref:EnvDTE.IDTWizard.Execute%2A> méthode dans l’Assistant, en lui passant les éléments suivants :  
  
-   L’objet DTE  
  
     L’objet DTE est la racine du modèle Automation.  
  
-   Le handle de la boîte de dialogue de fenêtre comme indiqué dans le segment de code, `hwndOwner ([in] long)`.  
  
     L’Assistant utilise cette `hwndOwner` en tant que le parent de la boîte de dialogue.  
  
-   Paramètres de contexte passé à l’interface en tant que variant de SAFEARRAY comme indiqué dans le segment de code, `[in] SAFEARRAY (VARIANT)* ContextParams`.  
  
     Paramètres de contexte contiennent un tableau de valeurs qui sont spécifiques au type de l’Assistant en cours de démarrage et l’état actuel du projet. L’IDE transmet les paramètres de contexte à l’Assistant. Pour plus d’informations, consultez [des paramètres de contexte](../../extensibility/internals/context-parameters.md).  
  
-   Paramètres personnalisés passé à l’interface en tant que variant de SAFEARRAY comme indiqué dans le segment de code, `[in] SAFEARRAY (VARIANT)* CustomParams`.  
  
     Paramètres personnalisés contiennent un tableau de paramètres définis par l’utilisateur. Un fichier .vsz passe des paramètres personnalisés à l’IDE. Les valeurs sont déterminées par la `Param=` instructions. Pour plus d’informations, consultez [personnalisé paramètres](../../extensibility/internals/custom-parameters.md).  
  
-   Sont des valeurs de retour pour l’interface  
  
    ```  
    wizardResultSuccess = -1,  
    wizardResultFailure = 0  
    wizardResultCancel = 1  
    wizardResultBackout = 2  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres de contexte](../../extensibility/internals/context-parameters.md)   
 [Paramètres personnalisés](../../extensibility/internals/custom-parameters.md)   
 [Assistants](../../extensibility/internals/wizards.md)   
 [Fichier Assistant (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)