---
title: Concepteur de flux de travail - Concepteur d’activités TransactedReceiveScope
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.ServiceModel.Activities.TransactedReceiveScope.UI
ms.assetid: 7ca93aad-4e83-4d81-90f4-998ee114d9b6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c7f5c4cd48cc98d58da278ac53c1a829d15c43cd
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="transactedreceivescope-activity-designer"></a>Concepteur d'activités TransactedReceiveScope

Le **TransactedReceiveScope** concepteur est utilisé pour créer et configurer un <xref:System.ServiceModel.Activities.TransactedReceiveScope> activité.

## <a name="the-transactedreceivescope-activity"></a>Activité TransactedReceiveScope

L'activité <xref:System.ServiceModel.Activities.TransactedReceiveScope> vous permet de transmettre une transaction dans des transactions de serveur créées par un workflow ou un répartiteur.

### <a name="using-the-transactedreceivescope-activity-designer"></a>Utilisation du concepteur d'activités TransactedReceiveScope
 Le **TransactedReceiveScope** Concepteur d’activités peut être trouvé dans le **messagerie** catégorie de la **boîte à outils**, qui est accessible en cliquant sur les **boîte à outils**  onglet sur le Concepteur de flux de travail (ou bien, sélectionnez **barre d’outils** à partir de la **vue** menu ou CTRL + ALT + X.)

 Le **TransactedReceiveScope** Concepteur d’activités peut être déplacé de la **boîte à outils** et déposés dans l’aire du Concepteur de flux de travail où les activités sont généralement placées. Cette opération crée un <xref:System.ServiceModel.Activities.TransactedReceiveScope> activité avec une valeur par défaut **DisplayName** de TransactedReceiveScope. Le <xref:System.Activities.Activity.DisplayName%2A> peuvent être modifiées dans l’en-tête de la **TransactedReceiveScope** Concepteur d’activités ou dans le **DisplayName** zone de la grille des propriétés.

 Le **TransactedReceiveScope** concepteur contient **demande** et **corps** cases. Celles-ci sont utilisées pour configurer la propriété <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>, laquelle spécifie une activité <xref:System.ServiceModel.Activities.Receive>, et une propriété <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>, laquelle spécifie un autre objet <xref:System.Activities.Activity>. La propriété <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> crée une transaction. La transaction est ensuite rendue ambiante pour l'étendue de la propriété <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> afin que toute activité dans cette étendue s'exécute à l'intérieur de cette transaction.

### <a name="the-transactedreceivescope-properties"></a>Propriétés de TransactedReceiveScope
 Le tableau suivant présente les propriétés de <xref:System.ServiceModel.Activities.TransactedReceiveScope> et décrit comment elles sont utilisées dans le concepteur. Ces <xref:System.Activities.Activity.DisplayName%2A> propriété peut être modifiée dans la grille des propriétés ou sur l’aire du Concepteur de flux de travail, mais les autres doivent être modifiées dans l’aire de conception.

|Nom de la propriété|Obligatoire|Utilisation|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial facultatif de l'activité <xref:System.ServiceModel.Activities.TransactedReceiveScope>. La valeur par défaut est TransactedReceiveScope.<br /><br /> Bien que le nom de la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, la meilleure pratique consiste à l'utiliser.|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>|True|Supprime un <xref:System.ServiceModel.Activities.Receive> l’activité dans le **demande** bloc sur l’aire du Concepteur d’activité.|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>|False|Supprime un <xref:System.Activities.Activity> dans les **corps** bloc sur l’aire du Concepteur d’activité.|

## <a name="see-also"></a>Voir aussi

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Réception](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Envoyer](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)