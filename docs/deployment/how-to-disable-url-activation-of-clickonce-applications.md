---
title: 'Comment : suspendre l’Activation des URL des Applications ClickOnce | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- disallowUrlActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: db31a16b-960f-4264-91d7-c7c40f876068
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 652060d639f5e516500cdc2b9de9fa7a4a45ee9f
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-disable-url-activation-of-clickonce-applications"></a>Comment : suspendre l'activation des URL des applications ClickOnce
En règle générale, une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] se lance automatiquement immédiatement après son installation à partir d'un serveur web. Pour des raisons de sécurité, vous pouvez décider de désactiver ce comportement et inviter les utilisateurs à lancer l’application à partir de la **Démarrer** menu à la place. La procédure suivante décrit comment désactiver l'activation d'URL.  
  
 Cette technique peut être utilisée uniquement pour les applications [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] installées sur l'ordinateur de l'utilisateur à partir d'un serveur web. Elle ne peut pas être utilisée pour les applications en ligne uniquement, qui peuvent être lancées uniquement à l'aide de leur URL. Pour plus d’informations sur la différence entre les applications en ligne uniquement et installées, consultez [choix d’une stratégie de déploiement ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 Cette procédure utilise le [ ! INCLURE[winsdklong](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client). Vous pouvez également effectuer cette procédure avec [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="procedure"></a>Procédure  
  
#### <a name="to-disable-url-activation-for-your-application"></a>Pour désactiver l'activation d'URL pour votre application  
  
1.  Ouvrez votre manifeste de déploiement dans MageUI.exe. Si vous n’en n'avez pas encore créé un, suivez les étapes de [procédure pas à pas : déploiement manuel d’une Application ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
2.  Sélectionnez le **Options de déploiement** onglet.  
  
3.  Désactivez le **exécuter automatiquement l’application après l’installation de** case à cocher.  
  
4.  Enregistrez et signez le manifeste.  
  
## <a name="see-also"></a>Voir aussi  
 [Publication d’applications ClickOnce](../deployment/publishing-clickonce-applications.md)