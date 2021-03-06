---
title: 'Comment : rechercher un Message dans la vue Messages | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Message Search dialog box
- Messages view
- messages, searching for
ms.assetid: 732b7ccc-54ea-41db-823b-2b96e3e4083e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 368d10f2285c94f053e536da77966e9b2fb26da9
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-search-for-a-message-in-messages-view"></a>Comment : rechercher un message dans la vue Messages
Vous pouvez rechercher un message spécifique dans la vue Messages à l’aide de son handle, un type ou un ID de message comme critère de recherche. L’une de ces, ou une combinaison, sera le critère de recherche valide. La direction initiale de la recherche peut également être spécifiée. Les champs dans la boîte de dialogue sont préchargés avec les attributs du message actuellement sélectionné.  
  
### <a name="to-search-for-a-message-in-messages-view"></a>Pour rechercher un message dans la vue Messages  
  
1.  Fenêtres ainsi que Spy ++ et qu’une [vue Messages](../debugger/messages-view.md) fenêtre sont visibles.  
  
2.  À partir de la **recherche** menu, choisissez **rechercher le Message**.  
  
     Le [boîte de dialogue de recherche de Message](../debugger/message-search-dialog-box.md) s’ouvre.  
  
3.  Faites glisser le **outil recherche** sur la fenêtre souhaitée. Lorsque vous faites glisser l’outil, le **recherche d’un Message** boîte de dialogue affiche des informations sur la fenêtre sélectionnée.  
  
     - ou  
  
     Si vous avez le handle de la fenêtre dont vous souhaitez examiner les messages, tapez-le dans la **gérer** zone de texte.  
  
     - ou  
  
     Si vous connaissez le type de message et/ou le code de message, les sélectionner à partir de la **Type** et **Message** menus déroulants et désactivez la **gérer** zone de texte.  
  
4.  Désactivez tous les champs pour lesquels vous ne souhaitez pas spécifier de valeurs.  
  
    > [!TIP]
    >  Pour réduire l’encombrement de l’écran, sélectionnez le **Masquer Spy ++** option. Cette option masque la fenêtre Spy ++ principale, en laissant uniquement le **rechercher une fenêtre** boîte de dialogue visible au-dessus de vos autres applications. La fenêtre principale Spy ++ est restaurée lorsque vous cliquez sur **OK** ou **Annuler**, ou lorsque vous désactivez le **Masquer Spy ++** option.  
  
5.  Choisissez **des** ou **vers le bas** pour la direction initiale de la recherche.  
  
6.  Cliquez sur **OK**.  
  
 Si un message correspondant est trouvé, il est mis en surbrillance dans la fenêtre d’affichage des Messages. Consultez [la vue Messages](../debugger/messages-view.md).