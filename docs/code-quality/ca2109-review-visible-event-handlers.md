---
title: 'CA2109 : Passez en revue les gestionnaires d’événements visibles'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2109
- ReviewVisibleEventHandlers
helpviewer_keywords:
- ReviewVisibleEventHandlers
- CA2109
ms.assetid: 8f8fa0ee-e94e-400e-b516-24d8727725d7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 481f03cc9f1699a794c0f34159afd7faa6a50c3d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="ca2109-review-visible-event-handlers"></a>CA2109 : Passez en revue les gestionnaires d’événements visibles
|||
|-|-|
|TypeName|ReviewVisibleEventHandlers|
|CheckId|CA2109|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Une méthode de gestion d'événements publique ou protégée a été détectée.

## <a name="rule-description"></a>Description de la règle
 Une méthode visible de l’extérieur de la gestion des événements présente un problème de sécurité qui requiert une révision.

 Les méthodes de gestion d’événements ne doivent pas être exposées sauf nécessité absolue. Un gestionnaire d’événements, un type délégué, qui appelle la méthode exposée peut être ajouté à n’importe quel événement tant que les signatures de gestionnaire et les événements correspondent. Les événements peuvent potentiellement être déclenchés par n’importe quel code et sont souvent déclenchés par le code de confiance système en réponse aux actions de l’utilisateur en cliquant sur un bouton. Ajout d’une vérification de sécurité à une méthode de gestion d’événements n’empêche pas le code de l’inscription d’un gestionnaire d’événements qui appelle la méthode.

 Une demande ne peut pas protéger de manière fiable une méthode appelée par un gestionnaire d’événements. Demandes de sécurité contribuent protéger le code contre les appelants non fiables en examinant les appelants sur la pile des appels. Code qui ajoute un gestionnaire d’événements à un événement n’est pas nécessairement présent sur la pile des appels lorsque les méthodes du Gestionnaire d’événements s’exécutent. Par conséquent, la pile des appels peut avoir uniquement hautement approuvé appelants lorsque la méthode de gestionnaire d’événements est appelée. Cela entraîne des demandes faites par la méthode de gestionnaire d’événements réussisse. En outre, l’autorisation demandée peut être déclarée lorsque la méthode est appelée. Pour ces raisons, le risque de correction d’une violation de cette règle ne peut être évalué après avoir examiné la méthode de gestion d’événements. Lorsque vous examinez votre code, considérez les points suivants :

-   Votre gestionnaire d’événements effectue des opérations dangereuses ou exploitables, telles que la déclaration d’autorisations ou la suppression des autorisations de code non managé ?

-   Quelles sont les menaces de sécurité vers et depuis votre code, car il peut s’exécuter à tout moment avec uniquement hautement approuvé appelants sur la pile ?

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, examinez la méthode et évaluez les éléments suivants :

-   Vous pouvez rendre la méthode de gestion d’événements non publics ?

-   Vous pouvez déplacer toutes les fonctionnalités dangereuses hors du Gestionnaire d’événements ?

-   Si une demande de sécurité est imposée, il est possible d’une autre manière ?

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Supprimez un avertissement de cette règle uniquement après un examen minutieux de la sécurité pour vous assurer que votre code ne constitue pas une menace pour la sécurité.

## <a name="example"></a>Exemple
 Le code suivant montre une méthode de gestion d’événements qui permettre être utilisés à mauvais escient par du code malveillant.

 [!code-csharp[FxCop.Security.EventSecLib#1](../code-quality/codesnippet/CSharp/ca2109-review-visible-event-handlers_1.cs)]

## <a name="see-also"></a>Voir aussi
 <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName> <xref:System.EventArgs?displayProperty=fullName>
