---
title: 'Comment : créer par programme des Documents | Documents Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- templates [Office development in Visual Studio], custom document
- Word [Office development in Visual Studio], creating documents
- documents [Office development in Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1c07067614c47f56bc5f21456ebe70c74d6cf62b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-create-new-documents"></a>Comment : créer des documents par programmation
  Quand vous créez un document par programmation, le nouveau document est un objet <xref:Microsoft.Office.Interop.Word.Document>natif. Cet objet ne possède pas les fonctionnalités de liaison de données et les événements supplémentaires d'un élément hôte <xref:Microsoft.Office.Tools.Word.Document>. Pour plus d'informations, consultez [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Quand vous développez un projet au niveau du document, vous ne pouvez pas ajouter par programmation d'éléments hôtes <xref:Microsoft.Office.Tools.Word.Document> à votre projet. Dans un projet de complément VSTO, vous pouvez convertir tout objet <xref:Microsoft.Office.Interop.Word.Document> en un élément hôte <xref:Microsoft.Office.Tools.Word.Document> au moment de l'exécution. Pour plus d'informations, consultez [Extension de documents Word et de classeurs Excel dans des compléments VSTO au moment de l'exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
### <a name="to-create-a-new-document-based-on-the-normal-template"></a>Pour créer un nouveau document basé sur le modèle Normal  
  
-   Utilisez la méthode <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> de la collection <xref:Microsoft.Office.Interop.Word.Documents> pour créer un nouveau document basé sur le modèle Normal. Pour utiliser cet exemple de code, exécutez-le à partir de la classe `ThisDocument` ou `ThisAddIn` de votre projet.  
  
     [!code-vb[Trin_VstcoreWordAutomation#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#1)]
     [!code-csharp[Trin_VstcoreWordAutomation#1](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#1)]  
  
## <a name="using-custom-templates"></a>Utilisation de modèles personnalisés  
 Le <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> (méthode) comporte une option *modèle* argument pour créer un nouveau document basé sur un modèle autre que le modèle Normal. Vous devez fournir le nom de fichier et le chemin d'accès complet du modèle.  
  
#### <a name="to-create-a-new-document-based-on-a-custom-template"></a>Pour créer un nouveau document basé sur un modèle personnalisé  
  
-   Appelez la méthode <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> de la collection <xref:Microsoft.Office.Interop.Word.Documents> et spécifiez le chemin d'accès au modèle. Pour utiliser cet exemple de code, exécutez-le à partir de la classe `ThisDocument` ou `ThisAddIn` de votre projet.  
  
     [!code-vb[Trin_VstcoreWordAutomation#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#2)]
     [!code-csharp[Trin_VstcoreWordAutomation#2](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#2)]  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : ouvrir des Documents existants par programmation](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)   
 [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  