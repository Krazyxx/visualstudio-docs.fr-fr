---
title: 'Erreur : le processus de travail de site Web a été interrompu par IIS | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.web_server_process_terminated
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ca76a0e66073d0102adb97d8cc4ca35087399297
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
---
# <a name="error-web-site-worker-process-has-been-terminated-by-iis"></a>Erreur : le processus de travail de site web a été interrompu par IIS.
Le débogueur a arrêté l’exécution du code sur le site web. Résultat : Internet Information Services (IIS) a supposé que le processus de travail avait cessé de répondre. Par conséquent, IIS a mis fin au processus de traitement.  
  
 Pour continuer le débogage, vous devez configurer IIS de sorte qu'il autorise la poursuite du processus de traitement. Ce message d'erreur n'apparaît pas avec les versions d'IIS antérieures à IIS 7.  
  
### <a name="to-configure-iis-7-to-allow-the-worker-process-to-continue"></a>Pour configurer IIS 7 afin qu'il permette la poursuite du processus de travail  
  
1.  Ouvrez le **outils d’administration** fenêtre.  
  
    1.  Cliquez sur **Démarrer**, puis choisissez **le panneau de configuration**.  
  
    2.  Dans **le panneau de configuration**, choisissez **basculer vers l’affichage classique**, si nécessaire, puis double-cliquez sur **outils d’administration**.  
  
2.  Dans le **outils d’administration** fenêtre, double-cliquez sur **Gestionnaire des Services Internet (IIS)**.  
  
     Le Gestionnaire des services IIS s'ouvre.  
  
3.  Dans le **connexions** volet, développez le \<nom de l’ordinateur > nœud si nécessaire.  
  
4.  Sous le \<nom de l’ordinateur > nœud, cliquez sur **Pools d’applications**.  
  
5.  Dans le **Pools d’applications** liste, cliquez sur le nom du pool exécuté par votre application, puis cliquez sur **paramètres avancés**.  
  
6.  Dans le **paramètres avancés** boîte de dialogue, recherchez le **modèle de processus** section et effectuez l’une des actions suivantes :  
  
    -   Définissez **Ping activé** à **False**.  
  
    -   Définissez **Ping des temps de réponse Maximum** à une valeur qui est supérieure à 90 secondes.  
  
     Paramètre **Ping activé** à **False** , IIS cesse de vérifier si le processus de travail est en cours d’exécution et maintient le processus de travail actif jusqu'à ce que vous arrêtiez votre processus débogué. Paramètre **Ping des temps de réponse Maximum** une valeur élevée autorise IIS à continuer à surveiller le processus de travail.  
  
7.  Cliquez sur **OK** pour fermer la **paramètres avancés** boîte de dialogue.  
  
8.  Fermez le Gestionnaire IIS et le **outils d’administration** fenêtre.  
  
## <a name="see-also"></a>Voir aussi  
 [Erreurs et résolution des problèmes du débogage distant](../debugger/remote-debugging-errors-and-troubleshooting.md)