---
title: Concepteur de flux de travail - Concepteur d’activités PickBranch
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.PickBranch.UI
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7ea106a96a5d6b81ee0b0b898c881eb752582f8d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="pickbranch-activity-designer"></a>Concepteur d'activités PickBranch

L'objet <xref:System.Activities.Statements.PickBranch> fournit un chemin d'accès d'exécution basé sur les événements dans une activité <xref:System.Activities.Statements.Pick> qui peut être déclenchée par un événement entrant.

## <a name="pickbranch"></a>PickBranch

Les objets <xref:System.Activities.Statements.PickBranch> sont contenus dans la collection <xref:System.Activities.Statements.Pick.Branches%2A> d'une activité <xref:System.Activities.Statements.Pick>. Chaque <xref:System.Activities.Statements.PickBranch> est contenue dans une branche de l'activité <xref:System.Activities.Statements.Pick> et peut être exécutée en raison d'un événement entrant qui sert de déclencheur. De cette façon le Concepteur de flux de travail Windows fournit la modélisation de flux de contrôle basé sur les événements. Chaque <xref:System.Activities.Statements.PickBranch> contient une propriété <xref:System.Activities.Statements.PickBranch.Trigger%2A> et une propriété <xref:System.Activities.Statements.PickBranch.Action%2A>.

### <a name="how-to-use-the-pick-activity-designer"></a>Comment utiliser le concepteur d'activités Pick

Le **PickBranch** concepteur n’est trouvé dans le **flux de contrôle** catégorie de la **boîte à outils**, qui est accessible en cliquant sur le **boîte à outils** onglet sur le Concepteur de flux de travail (ou bien, sélectionnez **barre d’outils** à partir de la **vue** menu ou CTRL + ALT + X).

Vide deux <xref:System.Activities.Statements.PickBranch> affichent les noms des objets avec **Branch1** et **Branch2** sont créés par défaut comme éléments d’un <xref:System.Activities.Statements.Pick> activité lorsque le **choisir** Concepteur d’activités est initialement déposé sur le Concepteur de Workflow. Ces respectifs <xref:System.Activities.Statements.PickBranch.DisplayName%2A> les valeurs de propriété peuvent être modifiées dans le **PickBranch** en-tête du concepteur ou dans le **propriétés** fenêtre pour chaque branche.

Il existe deux façons d’ajouter <xref:System.Activities.Statements.PickBranch> objets à la collection d’un <xref:System.Activities.Statements.Pick> objet : glisser- déposer le **PickBranch** concepteur à partir de la **boîte à outils** ou à l’aide du menu contextuel dans dans le **choisir** aire de conception :

1.  Le **PickBranch** concepteur crée un <xref:System.Activities.Statements.PickBranch> lorsqu’il est déplacé depuis la **boîte à outils** et déposé dans une des branches d’un **choisir** Concepteur d’activités sur le Aire du Concepteur de flux de travail. Les nouveaux objets <xref:System.Activities.Statements.PickBranch> peuvent être placés dans le concepteur <xref:System.Activities.Statements.Pick> à gauche ou à droite des éléments <xref:System.Activities.Statements.PickBranch> existants déjà contenus dans la collection. Lorsque vous faites glisser un **PickBranch** concepteur sur le **choisir** concepteur avec une souris, le **choisir** concepteur utilise une bande bleu gris verticale pour indiquer l’endroit où le <xref:System.Activities.Statements.PickBranch> est ajouté pour un positionnement de souris donné.

2.  Bouton droit sur **choisir** Concepteur d’activités (mais pas à l’intérieur **PickBranch** concepteur) pour afficher un menu contextuel et sélectionnez **créer une branche** pour ajouter un nouveau <xref:System.Activities.Statements.PickBranch>. Notez que la nouvelle <xref:System.Activities.Statements.PickBranch> est ajouté à droite existants <xref:System.Activities.Statements.PickBranch> des objets dans le **choisir** concepteur.

 Le **PickBranch** concepteur peut être développé pour révéler le **déclencheur** et **Action** zones ou réduit en cliquant sur le double signe ^ à droite de leurs en-têtes. Modifier la <xref:System.Activities.Statements.PickBranch.Trigger%2A> et <xref:System.Activities.Statements.PickBranch.Action%2A> de chaque <xref:System.Activities.Statements.PickBranch> en déposant des activités dans le **déclencheur** et **Action** zones de leurs concepteurs.

 Le <xref:System.Activities.Statements.PickBranch> des objets dans le <xref:System.Activities.Statements.Pick.Branches%2A> collection d’un <xref:System.Activities.Statements.Pick> d’objet, peuvent être réorganisées par glisser- déposer à un nouvel emplacement dans le **choisir** concepteur. Le **choisir** concepteur utilise une bande bleu gris verticale pour indiquer l’endroit où le <xref:System.Activities.Statements.PickBranch> est ajouté pour un positionnement de souris donné.

 Il existe deux façons de supprimer un objet <xref:System.Activities.Statements.PickBranch> :

1.  Sélectionnez le **PickBranch** concepteur et supprimez-le.

2.  Sélectionnez le **PickBranch** concepteur, avec le bouton droit pour afficher le menu contextuel et sélectionnez **supprimer**.

 Veillez à sélectionner le **PickBranch** concepteur, comme en sélectionnant une activités à l’intérieur de son **déclencheur** ou **Action** zones supprime l’une de ces activités et non le <xref:System.Activities.Statements.PickBranch> objet.

### <a name="pickbranch-properties-in-the-workflow-designer"></a>Propriétés de PickBranch dans le concepteur de workflow
 Le tableau suivant présente les plus utiles <xref:System.Activities.Statements.PickBranch> propriétés et décrit comment les utiliser dans le Concepteur de flux de travail.

|Nom de la propriété|Obligatoire|Utilisation|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|False|Le nom convivial affiché dans l’en-tête de la **PickBranch** concepteur. La valeur par défaut est Branch.<br /><br /> Bien que la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|True|Chaque objet <xref:System.Activities.Statements.PickBranch> contient une action <xref:System.Activities.Statements.PickBranch.Trigger%2A> qui peut appeler la propriété <xref:System.Activities.Statements.PickBranch.Action%2A>.|
|<xref:System.Activities.Statements.PickBranch.Action%2A>|False|Chaque objet <xref:System.Activities.Statements.PickBranch> contient une propriété <xref:System.Activities.Statements.PickBranch.Action%2A> qui est exécutée en cas de déclenchement.|

## <a name="see-also"></a>Voir aussi

- [Flux de contrôle](../workflow-designer/control-flow-activity-designers.md)
- [Activité Pick](/dotnet/framework/windows-workflow-foundation/pick-activity)
- [Utilisation de l’activité Pick](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)