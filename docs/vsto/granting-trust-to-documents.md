---
title: Accorder la confiance à des Documents | Documents Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], trust
- inclusion lists [Office development in Visual Studio], about inclusion lists
- trust [Office development in Visual Studio], 2007 Office system
- granting trust [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e8556f77b74ee1dab6a257f5ed3634da4bf798cd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="granting-trust-to-documents"></a>Granting Trust to Documents
  Un projet au niveau du document présente les mêmes exigences de sécurité que les projets au niveau de l’application : il convient de signer les manifestes à l’aide d’un certificat ou de cliquer sur l’invite d’approbation. En outre, le document ou le classeur doit se trouver dans un répertoire désigné comme emplacement approuvé.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="trusted-locations"></a>Emplacements approuvés  
 Dans les applications [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] et Office 2010 disposent de centres de confiance dans lequel les utilisateurs peuvent configurer les paramètres de sécurité, telles que des emplacements approuvés. Pour les solutions Office, l’ordinateur local est considéré comme un emplacement approuvé. Toutefois, en raison de risques plus élevés, certains répertoires ne peuvent jamais être approuvés, tels que les dossiers temporaires système propres à chaque utilisateur et à Internet Explorer.  
  
 Pour plus d’informations sur le centre de gestion, consultez [sécurité et les stratégies et les paramètres dans Office 2010](http://go.microsoft.com/fwlink/?LinkId=89202). Pour plus d’informations sur la façon de créer, gérer, supprimer et configurer des dossiers approuvés, consultez [configurer les paramètres des emplacements et éditeurs approuvés dans Office system 2007](http://go.microsoft.com/fwlink/?LinkId=89203) et [créer, supprimer ou modifier un emplacement de vos fichiers approuvé](https://support.office.com/en-au/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).  
  
## <a name="security-considerations-for-office-solutions"></a>Considérations spécifiques à la sécurité pour les solutions Office  
 Plusieurs problèmes de sécurité se posent quand vous déterminez les dossiers à ajouter aux emplacements approuvés :  
  
-   Les dossiers locaux sont considérés plus sécurisés et ils sont approuvés de manière implicite. Les emplacements distants tels que les partages de fichiers doivent être désignés comme emplacements approuvés.  
  
-   Quand vous ajoutez un répertoire aux emplacements approuvés, vous accordez une confiance totale aux solutions Office, mais également au code VBA et ActiveX. Par conséquent, le répertoire racine et le dossier Mes documents ne doivent pas être désignés comme approuvés.  
  
-   Le document lui-même est approuvé en utilisant les emplacements approuvés. Toutefois, des autorisations supplémentaires sont requises pour approuver la personnalisation. Vous pouvez accorder une confiance totale à la personnalisation en signant les manifestes avec un certificat, en cliquant sur l'invite d'approbation ou en installant la solution Office dans le répertoire Program Files.  
  
-   Vous pouvez stocker le document ou le classeur d'une solution au niveau du document dans le même répertoire que l'assembly ou dans un répertoire différent. Par exemple, le document peut être situé sur un serveur SharePoint et l'assembly dans un partage de fichiers réseau. Pour plus d’informations, consultez [Comment : publier une Solution d’Office au niveau du Document sur un serveur SharePoint à l’aide de ClickOnce](http://msdn.microsoft.com/en-us/2408e809-fb78-42a1-9152-00afa1522e58).  
  
## <a name="see-also"></a>Voir aussi  
 [Accorder la confiance à des Solutions Office](../vsto/granting-trust-to-office-solutions.md)   
 [Résolution des problèmes de sécurité des solutions Office](../vsto/troubleshooting-office-solution-security.md)   
 [Sécurisation de solutions Office](../vsto/securing-office-solutions.md)  
  
  