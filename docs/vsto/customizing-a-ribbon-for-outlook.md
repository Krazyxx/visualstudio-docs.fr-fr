---
title: Personnalisation d’un ruban pour Outlook | Documents Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Inspectors [Office development in Visual Studio]
- Outlook [Office development in Visual Studio], Ribbon
- customizing the Ribbon, about customizing the Ribbon
- custom Ribbon, about customizing the Ribbon
- Ribbon [Office development in Visual Studio], Outlook
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0c160b22a10a837e64df2ad00a07381c3d8240c3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="customizing-a-ribbon-for-outlook"></a>Personnalisation d'un ruban pour Outlook
  Quand vous personnalisez le ruban dans Microsoft Office Outlook, vous devez prendre en compte l'emplacement où votre ruban personnalisé apparaîtra dans l'application. Outlook affiche le ruban dans l'interface utilisateur principale de l'application et dans les fenêtres qui s'ouvrent lorsque les utilisateurs effectuent certaines tâches, telles que la création de messages électroniques. Ces fenêtres d'application sont appelées inspecteurs.  
  
 ![lien vers la vidéo](../vsto/media/playvideo.gif "lien vidéo") pour une démonstration vidéo connexe, consultez [comment faire : utiliser le Concepteur de ruban pour personnaliser le ruban dans Outlook ?](http://go.microsoft.com/fwlink/?LinkID=130312).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="adding-a-custom-ribbon-to-the-main-application-ui"></a>Ajout d'un ruban personnalisé à l'interface utilisateur de l'application principale  
 L'interface utilisateur de l'application principale dans Outlook est appelée l'Explorateur. Si vous utilisez la **ruban (Concepteur visuel)** élément, vous pouvez ajouter un ruban à l’Explorateur en cliquant sur le **RibbonType** propriété du ruban dans le **propriétés** fenêtre, puis en sélectionnant **Microsoft.Outlook.Explorer**.  
  
## <a name="assigning-a-ribbon-to-an-inspector"></a>Affectation d'un ruban à un inspecteur  
 Pour identifier l'inspecteur que vous souhaitez personnaliser, vous spécifiez le type de ruban qui correspond à la classe de message de l'inspecteur.  
  
 Si vous utilisez la **ruban (Concepteur visuel)** , cliquez sur le **RibbonType** propriété du ruban dans le **propriétés** fenêtre et puis sélectionnez un ou plusieurs ID à partir du ruban la liste de valeurs.  
  
 Vous pouvez ajouter plusieurs rubans à un projet. Si plusieurs rubans partagent un ID de ruban, substituez la méthode CreateRibbonExtensibilityObject dans la `ThisAddin` classe de votre projet pour spécifier le ruban à afficher au moment de l’exécution. Pour plus d’informations, consultez [vue d’ensemble du ruban](../vsto/ribbon-overview.md). Pour plus d’informations sur chaque type de ruban, consultez l’article technique [personnalisation du ruban dans Outlook 2007](http://msdn.microsoft.com/en-us/946e97ea-f556-4e84-8fac-01cd9214e170).  
  
## <a name="specifying-the-ribbon-type-by-using-ribbon-xml"></a>Spécification du type de ruban à l'aide du code XML du ruban  
 Si vous utilisez la **ruban (XML)** d’élément, vérifiez la valeur de la *ribbonID* paramètre dans le <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> méthode et retournez le ruban approprié.  
  
 La méthode <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> est automatiquement générée par Visual Studio dans le fichier de code du ruban. Le *ribbonID* paramètre est une chaîne qui identifie l’Explorateur ou un type spécifique d’inspecteur. Pour obtenir la liste complète des valeurs possibles de la *ribbonID* paramètre, consultez l’article technique [personnalisation du ruban dans Outlook 2007](http://msdn.microsoft.com/en-us/946e97ea-f556-4e84-8fac-01cd9214e170).  
  
 L'exemple de code suivant montre comment afficher un ruban personnalisé uniquement dans l' inspecteur `Microsoft.Outlook.Mail.Compose`. Il s'agit de l'inspecteur qui s'affiche lorsqu'un utilisateur crée un message électronique. Le ruban à afficher est spécifié dans le `GetResourceText()` (méthode), qui est généré dans le **ruban** classe. Pour plus d’informations sur la **ruban** de classe, consultez [ruban XML](../vsto/ribbon-xml.md).  
  
 [!code-csharp[Trin_RibbonOutlookBasic#1](../vsto/codesnippet/CSharp/Trin_RibbonOutlookBasic/Ribbon1.cs#1)]
 [!code-vb[Trin_RibbonOutlookBasic#1](../vsto/codesnippet/VisualBasic/Trin_RibbonOutlookBasic/Ribbon1.vb#1)]  
  
## <a name="see-also"></a>Voir aussi  
 [Accessing the Ribbon at Run Time](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Vue d’ensemble du ruban](../vsto/ribbon-overview.md)   
 [Concepteur de ruban](../vsto/ribbon-designer.md)   
 [Élément XML Ribbon](../vsto/ribbon-xml.md)  
  
  