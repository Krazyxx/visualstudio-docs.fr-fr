---
title: Concepteur de flux de travail - Concepteur d’activités Sequence
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Sequence.UI
ms.assetid: 51c8d3cb-4d43-458f-9631-b63755f9ac94
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0e72c5b5e43ca037a6d65e3e4980fdb0f89f000f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="sequence-activity-designer"></a>Concepteur d'activités Sequence

L'activité <xref:System.Activities.Statements.Sequence> contient une collection ordonnée d'activités enfants qu'elle exécute dans l'ordre.

Une autre façon d'exécuter un ensemble d'activités dans l'ordre consiste à utiliser une activité <xref:System.Activities.Statements.Flowchart>. Envisagez d’utiliser le [organigramme](../workflow-designer/flowchart-activity-designer.md) lorsque vous avez un branchement simple ou un bouclage des flux de programme que vous souhaitez modéliser diagramme.

## <a name="using-the-sequence-activity-designer"></a>Utilisation du concepteur d'activités Sequence

Pour ajouter un <xref:System.Activities.Statements.Sequence> activité, faites glisser le **séquence** Concepteur d’activités à partir de la **boîte à outils** et déposez-le dans l’aire du Concepteur de flux de travail Windows. Pour ajouter une activité enfant à cette <xref:System.Activities.Statements.Sequence> activité, faites glisser une autre activité de la **boîte à outils** et déposez-le sur le triangle dans la zone avec le texte d’indication « Déposer l’activité ici ».

### <a name="sequence-activity-properties-in-the-workflow-designer"></a>Propriétés de l'activité Sequence dans le concepteur de workflow

Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.Sequence> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la grille des propriétés ou dans l'aire du concepteur.

|Nom de la propriété|Obligatoire|Utilisation|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Spécifie le nom convivial du concepteur d'activités <xref:System.Activities.Statements.Sequence> dans l'en-tête. Sequence est la valeur par défaut. La valeur peut être modifiée dans la grille Propriétés ou directement dans l'en-tête du concepteur d'activités.<br /><br /> Bien que la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|

## <a name="see-also"></a>Voir aussi

- [Organigramme](../workflow-designer/flowchart-activity-designer.md)
- [Flux de contrôle](../workflow-designer/control-flow-activity-designers.md)