---
title: Conditions préalables au déploiement de application | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, platform detection
- ClickOnce deployment, prerequisites
- ClickOnce deployment, dependencies
- prerequisites, ClickOnce
- dependencies, ClickOnce
ms.assetid: fc6e047e-ad94-44e8-8ff5-b6d1f4ca7735
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 48f72640bdf8efc53b278e4600c6b262dc1a26bf
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="application-deployment-prerequisites"></a>Composants requis pour le déploiement d'applications
Pour vous assurer que votre application sera installée et exécutée correctement, vérifiez que tous les composants dont dépend votre application sont déjà installés sur l'ordinateur cible. Par exemple, la plupart des applications créées à l'aide de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ont une dépendance par rapport au [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] ; la version appropriée du Common Language Runtime doit être présente sur l'ordinateur de destination avant que l'application ne soit installée.  
  
 Vous pouvez sélectionner ces composants requis dans le **boîte de dialogue composants requis** et installer le .NET Framework et autres composants redistribuables dans le cadre de votre installation. Cette pratique est appelée *amorçage*. Ensuite, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] génère un programme exécutable Windows nommé Setup.exe, également appelé un *programme d’amorçage*. Le programme d'amorçage effectue l'installation des composants requis avant que votre application ne s'exécute. Pour plus d’informations sur la sélection de ces conditions préalables, consultez [boîte de dialogue composants requis](../ide/reference/prerequisites-dialog-box.md).  
  
 Chaque composant requis est un package de programme d'amorçage. Un package de programme d'amorçage est un groupe de répertoires et de fichiers qui contiennent des fichiers manifeste qui décrivent la façon dont le composant requis doit être installé. Si vos composants requis d’application ne sont pas répertoriées dans le **boîte de dialogue composants requis**, vous pouvez créer des packages de programme d’amorçage personnalisés et les ajouter à Visual Studio. Vous pouvez ensuite sélectionner les composants requis dans le **boîte de dialogue composants requis**. Pour plus d’informations, consultez [création de Packages de programme d’amorçage](../deployment/creating-bootstrapper-packages.md).  
  
 Par défaut, l'amorçage est activé pour le déploiement ClickOnce. Le programme d'amorçage généré pour le déploiement ClickOnce est signé. Vous pouvez désactiver l'amorçage d'un composant. Toutefois, ne le faites que si vous êtes sûr que la version appropriée du composant est déjà installée sur tous les ordinateurs cibles.  
  
## <a name="bootstrapping-and-clickonce-deployment"></a>Amorçage et déploiement ClickOnce  
 Avant l'installation d'une application sur un ordinateur client, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] examine le client pour s'assurer qu'il répond à certaines conditions requises spécifiées dans le manifeste de l'application. Notamment :  
  
-   La version minimale requise du Common Language Runtime, spécifiée en tant que dépendance d'assembly dans le manifeste de l'application.  
  
-   La version minimale du système d'exploitation Windows requis par l'application, spécifiée dans le manifeste de l'application via l'élément `<osVersionInfo>` (Consultez [ \<dépendance > élément](../deployment/dependency-element-clickonce-application.md))  
  
-   La version minimale des assemblys qui doivent être préinstallés dans le Global Assembly Cache (GAC), conformément aux déclarations de dépendance d'assembly du manifeste de l'assembly.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] peut détecter les composants requis manquants, et vous pouvez installer les composants requis à l’aide d’un programme d’amorçage. Pour plus d’informations, consultez [Comment : installer les composants requis avec une Application ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md).  
  
> [!NOTE]
>  Pour changer les valeurs dans les manifestes générés par des outils tels que [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et MageUI.exe, vous devez changer le manifeste de l'application dans un éditeur de texte, puis signer à nouveau les manifestes de l'application et de déploiement. Pour plus d'informations, consultez [Comment : signer de nouveau des manifestes d'application et de déploiement](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
 Si vous utilisez Visual Studio et ClickOnce pour déployer votre application, les packages de programme d'amorçage sélectionnés par défaut dépendent de la version du .NET Framework de la solution. Toutefois, si vous modifiez la version du .NET Framework cible, vous devez mettre à jour les options de la **boîte de dialogue composants requis** manuellement.  
  
|.NET Framework cible|Packages de programme d'amorçage sélectionnés|  
|---------------------------|------------------------------------|  
|.NET Framework 4 Client Profile|.NET Framework 4 Client Profile<br /><br /> Windows Installer 3.1|  
|.NET Framework 4|.NET Framework 4<br /><br /> Windows Installer 3.1|  
  
 Avec le déploiement [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], la page Publish.htm générée par l'Assistant Publication [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pointe soit vers un lien qui installe uniquement l'application, soit vers un lien qui installe à la fois l'application et les composants d'amorçage.  
  
 Si vous générez le programme d'amorçage à l'aide de l'Assistant Publication ClickOnce ou de la page Publish dans Visual Studio, le fichier Setup.exe est automatiquement signé. Toutefois, si vous souhaitez utiliser le certificat de votre client pour signer le programme d'amorçage, vous pouvez signer le fichier plus tard.  
  
## <a name="bootstrapping-and-msbuild"></a>Amorçage et MSBuild  
 Si vous n'utilisez pas [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], mais que vous compilez vos applications sur la ligne de commande, vous pouvez créer l'application d'amorçage [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] à l'aide d'une tâche Microsoft Build Engine (MSBuild). Pour plus d’informations, consultez [GenerateBootstrapper, tâche](../msbuild/generatebootstrapper-task.md).  
  
 À la place de l'amorçage, vous pouvez prédéployer les composants à l'aide d'un système électronique de distribution de logiciels, par exemple Microsoft Systems Management Server (SMS).  
  
## <a name="bootstrapper-setupexe-command-line-arguments"></a>Arguments de ligne de commande du programme d'amorçage  
 Le fichier Setup.exe généré par [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et les tâches MSBuild prend en charge le petit ensemble suivant d'arguments de ligne de commande. Tous les autres arguments fournis à l'application d'amorçage sont transmis au programme d'installation de l'application.  
  
 Si vous changez les options du programme d'amorçage, vous devez changer le programme d'amorçage non signé, puis signer plus tard le fichier du programme d'amorçage.  
  
|Argument de ligne de commande|Description|  
|---------------------------|-----------------|  
|**- ?, -h, - aide**|Affiche une boîte de dialogue d'aide.|  
|**-url, - componentsurl**|Affiche l'URL stockée et l'URL des composants pour cette installation.|  
|**-url =** `location`|Définit l'URL où Setup.exe doit chercher l'application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].|  
|**-componentsurl =** `location`|Définit l'URL où Setup.exe doit chercher les dépendances, par exemple le [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].|  
|**-homesite =** `true`**&#124;** `false`|Lorsque `true`, télécharge les dépendances à partir de l’emplacement par défaut sur le site du fournisseur. Cela remplace le **- componentsurl** paramètre. Lorsque `false`, télécharge les dépendances à partir de l’URL spécifiée par **- componentsurl**.|  
  
## <a name="operating-system-support"></a>Système d'exploitation pris en charge  
 Le programme d'amorçage Visual Studio n'est pas pris en charge sur Windows Server 2008 Server Core ou Windows Server 2008 R2 Server Core, qui fournissent un environnement serveur à maintenance réduite avec des fonctionnalités limitées. Par exemple, comme l’option d’installation Server Core ne prend en charge que le profil .NET Framework 3.5 Server Core, les fonctionnalités Visual Studio qui dépendent du .NET Framework complet ne peuvent pas s’exécuter.  
  
## <a name="see-also"></a>Voir aussi  
 [Choix d’une stratégie de déploiement ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [Sécurité et déploiement ClickOnce](../deployment/clickonce-security-and-deployment.md)