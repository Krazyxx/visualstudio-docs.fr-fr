---
title: Marqueurs du visualiseur concurrentiel | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.markersui
ms.assetid: c4692d17-6cd2-4ad1-8590-d7275c771c70
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a1e713292421613e835697037d5298a4a2c854f6
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="concurrency-visualizer-markers"></a>Marqueurs du visualiseur concurrentiel
Dans le visualiseur concurrentiel, les marqueurs sont des icônes qui représentent les événements d’une application.  En règle générale, l’application génère ces événements pour désigner les phases ou les occurrences d’une application.  Les événements peuvent être générés par l’application ou par les bibliothèques et les runtimes qu’utilise l’application.  
  
## <a name="kinds-of-markers"></a>Types de marqueurs  
 Le visualiseur concurrentiel utilise trois types de marqueurs pour représenter les événements d’application : des indicateurs, des messages et des intervalles.  
  
1.  Utilisez un *indicateur* pour indiquer un point dans le temps présentant un intérêt particulier dans votre application.  Par exemple, vous pouvez utiliser un indicateur pour montrer qu’une valeur de variable a atteint un certain seuil, ou qu’une exception a été levée.  
  
2.  Un *message* marque également un point dans le temps, mais il peut aussi être utilisé pour le suivi des journaux.  Par exemple, les données autrefois vidées dans un fichier journal peuvent désormais être encapsulées dans un appel de message, pour que vous puissiez les suivre et les afficher dans le visualiseur concurrentiel. Vous pouvez également utiliser le visualiseur concurrentiel pour exporter ces données vers un fichier CSV.  
  
3.  Un *intervalle* représente un intervalle de temps au sein de votre application, par exemple, l’une de ses phases.  
  
## <a name="marker-linkage-to-threads"></a>Liaison d’un marqueur à un thread  
 Chaque thread qui génère des marqueurs dispose d’un canal chronologique distinct.  L’ID du thread qui est chargé de générer les événements de marqueur est indiqué à côté de la description du canal de marqueur.  L’ID qui est affiché à gauche du canal de marqueur correspond à l’ID d’un autre thread dans le processus en cours.  
  
## <a name="marker-importance"></a>Importance des marqueurs  
 Les marqueurs peuvent avoir l’un des quatre niveaux d’importance suivants : bas, normal, élevé et critique.  Vous pouvez filtrer les sources des marqueurs selon leur niveau d’importance.  Par exemple, si vous voulez afficher uniquement les marqueurs provenant d’une source dont l’importance est normale ou critique, vous pouvez configurer un filtre dans la boîte de dialogue [Paramètres avancés](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md). L’importance d’un marqueur s’affiche dans son info-bulle et dans le [rapport Marqueurs](../profiling/markers-report.md).  
  
## <a name="marker-category"></a>Catégorie de marqueur  
 Une catégorie de marqueur correspond à un groupe d’événements de marqueurs provenant d’une même source.  Le visualiseur concurrentiel utilise un système de couleurs pour distinguer les différentes catégories d’indicateurs et d’intervalles. Vous pouvez configurer le visualiseur concurrentiel afin qu’il utilise des catégories pour filtrer les événements de marqueurs provenant d’un même fournisseur d’événements.  Utilisez la boîte de dialogue [Paramètres avancés](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) pour configurer le filtre.  
  
## <a name="known-sources-of-markers"></a>Sources connues de marqueurs  
 Tous les fournisseurs ETW peuvent générer des marqueurs, tant qu’ils respectent certaines contraintes. Vous pouvez configurer le visualiseur concurrentiel pour qu’il écoute d’autres sources d’événements de marqueurs. Par défaut, le visualiseur écoute les sources d’événements suivantes :  
  
-   [Kit SDK du visualiseur concurrentiel](../profiling/concurrency-visualizer-sdk.md)  
  
-   [La bibliothèque parallèle de tâches](/dotnet/standard/parallel-programming/task-parallel-library-tpl)  
  
-   [Le flux de données](/dotnet/standard/parallel-programming/dataflow-task-parallel-library)  
  
-   [Parallel LINQ (PLINQ)](/dotnet/standard/parallel-programming/parallel-linq-plinq)  
  
-   [Le runtime d’accès concurrentiel](/cpp/parallel/concrt/concurrency-runtime)  
  
-   [Les marqueurs Scenario](http://msdn.microsoft.com/en-us/e3b55bc2-b451-4214-ae00-0c7f5a5baec8)  
  
-   [C++ AMP (C++ Accelerated Massive Parallelism)](/cpp/parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism)  
  
 Vous pouvez utiliser l’onglet Marqueurs de la boîte de dialogue [Paramètres avancés](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) pour contrôler l’affichage des marqueurs provenant de différentes sources dans le visualiseur concurrentiel, et pour filtrer les marqueurs en fonction de leur importance et de leur catégorie.  
  
## <a name="markers-from-eventsource"></a>Marqueurs EventSource  
 Le visualiseur concurrentiel peut également afficher des événements EventSource.  Pour plus d’informations, consultez [Visualisation des événements EventSource en tant que marqueurs](../profiling/visualizing-eventsource-events-as-markers.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Marqueurs indicateurs](../profiling/flag-markers.md)   
 [Marqueurs de messages](../profiling/message-markers.md)   
 [Marqueurs d’intervalles](../profiling/span-markers.md)   
 [Visualisation des événements EventSource en tant que marqueurs](../profiling/visualizing-eventsource-events-as-markers.md)