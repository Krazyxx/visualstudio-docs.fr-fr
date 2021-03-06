---
title: 'CA2230 : Utilisez le mot clé params pour les arguments de variables'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseParamsForVariableArguments
- CA2230
helpviewer_keywords:
- CA2230
- UseParamsForVariableArguments
ms.assetid: bf98b733-4855-4110-9f16-eba5a9e79421
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 70492152e75d3d257b63e014e854c4b0b431d2ec
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="ca2230-use-params-for-variable-arguments"></a>CA2230 : Utilisez le mot clé params pour les arguments de variables
|||
|-|-|
|TypeName|UseParamsForVariableArguments|
|CheckId|CA2230|
|Category|Microsoft.Usage|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un type public ou protégé contient une méthode publique ou protégée qui utilise le `VarArgs` convention d’appel.

## <a name="rule-description"></a>Description de la règle
 Le `VarArgs` convention d’appel est utilisée avec certaines définitions de méthode qui acceptent un nombre variable de paramètres. Une méthode à l’aide de la `VarArgs` convention d’appel n’est pas Common Language Specification (CLS) conforme et ne peut pas être accessible entre les langages de programmation.

 En c#, le `VarArgs` convention d’appel est utilisé lors de la liste de paramètres d’une méthode se termine par le `__arglist` (mot clé). Visual Basic ne prend pas en charge la `VarArgs` convention d’appel et Visual C++ permet son utilisation uniquement dans le code non managé qui utilise les points de suspension `...` notation.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle en c#, utilisez le [params](/dotnet/csharp/language-reference/keywords/params) (mot clé) au lieu de `__arglist`.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 L’exemple suivant montre deux méthodes, qui enfreint la règle et qui satisfait à la règle.

 [!code-csharp[FxCop.Usage.UseParams#1](../code-quality/codesnippet/CSharp/ca2230-use-params-for-variable-arguments_1.cs)]

## <a name="see-also"></a>Voir aussi
 <xref:System.Reflection.CallingConventions?displayProperty=fullName> [Indépendance du langage et composants indépendants du langage](/dotnet/standard/language-independence-and-language-independent-components)