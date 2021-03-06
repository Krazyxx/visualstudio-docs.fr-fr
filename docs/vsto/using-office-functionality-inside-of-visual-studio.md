---
title: À l’aide de fonctionnalités Office dans Visual Studio | Documents Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], document protection
- Office applications [Office development in Visual Studio]
- Office functionality inside Visual Studio
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5927c9b3288755efc8e4b5700487a138f7a04f63
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="using-office-functionality-inside-of-visual-studio"></a>Utilisation de fonctionnalités Office dans Visual Studio
  Lorsque vous créez un projet au niveau du document, le document et l’application associée sont hébergés au sein de Visual Studio afin de pouvoir concevoir et travailler directement avec le document. Lorsque vous avez une application ouvre dans Visual Studio de Microsoft Office, fonctionne généralement comme prévu. Toutefois, certaines fonctionnalités de l’application est différent ou est inaccessible.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="document-protection"></a>Protection du document  
 Microsoft Office Word et Microsoft Office Excel offrent document des fonctionnalités de protection que vous pouvez utiliser dans vos projets. Toutefois, si la protection de document est activée alors que le document est ouvert dans Visual Studio, il peut vous empêcher d’apporter des modifications de conception. Pour plus d’informations, consultez [Protection des documents dans les Solutions au niveau du Document](../vsto/document-protection-in-document-level-solutions.md).  
  
## <a name="information-rights-management"></a>Information Rights Management  
 Information Rights Management (IRM) est disponible dans Microsoft Office Word et Microsoft Office Excel. IRM peut vous aider à empêcher les personnes non autorisées d’affichage ou la modification d’informations sensibles. Toutefois, IRM peut également empêcher votre code en cours d’exécution. Pour plus d’informations, consultez [Information Rights Management et présentation des Extensions de Code managé](../vsto/information-rights-management-and-managed-code-extensions-overview.md).  
  
## <a name="password-protection"></a>Mot de passe  
 Les documents Microsoft Office Word et classeurs Microsoft Office Excel peuvent être définis afin qu’ils ne peuvent pas être ouverts par une personne ne connaît pas le mot de passe. Mot de passe est géré différemment dans Word et Excel et peut affecter votre processus de développement. Pour plus d’informations, consultez [mot de passe sur des Documents Office](../vsto/password-protection-on-office-documents.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Protection des documents dans les Solutions au niveau du Document](../vsto/document-protection-in-document-level-solutions.md)   
 [Information Rights Management et vue d’ensemble des Extensions de Code managé](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Mot de passe sur des Documents Office](../vsto/password-protection-on-office-documents.md)   
 [Guide pratique pour ouvrir des solutions Office sans exécuter le code](../vsto/how-to-open-office-solutions-without-running-code.md)  
  
  