---
title: 'CA1055 : Les valeurs de retour Uri ne doivent pas être des chaînes'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1055
- UriReturnValuesShouldNotBeStrings
helpviewer_keywords:
- UriReturnValuesShouldNotBeStrings
- CA1055
ms.assetid: 40e39873-7872-4988-8195-9eb0ade9ece0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dafaccd310d2122c4e00c12e73675ef1778d25b6
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="ca1055-uri-return-values-should-not-be-strings"></a>CA1055 : Les valeurs de retour Uri ne doivent pas être des chaînes
|||
|-|-|
|TypeName|UriReturnValuesShouldNotBeStrings|
|CheckId|CA1055|
|Category|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Le nom d’une méthode contient « uri », « Uri », « urn », « Urn », « url » ou « Url », et la méthode retourne une chaîne.

## <a name="rule-description"></a>Description de la règle
 Cette règle fractionne le nom de méthode en jetons basés sur la convention de casse Pascal et vérifie si chaque jeton est égal à « uri », « Uri », « urn », « Urn », « url » ou « Url ». Il existe une correspondance, la règle considère que la méthode retourne un identificateur de ressource uniforme (URI). Une représentation sous forme de chaîne d'un URI est sujette aux erreurs d'analyse et d'encodage, et peut entraîner des failles de sécurité. La <xref:System.Uri?displayProperty=fullName> classe fournit ces services de manière sûre et sécurisée.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, modifiez le type de retour à un <xref:System.Uri>.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle si la valeur de retour ne représente pas un URI.

## <a name="example"></a>Exemple
 L’exemple suivant présente un type, `ErrorProne`, qui enfreint cette règle et un type, `SaferWay`, qui satisfait à la règle.

 [!code-csharp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1055-uri-return-values-should-not-be-strings_1.cs)]
 [!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1055-uri-return-values-should-not-be-strings_1.vb)]
 [!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1055-uri-return-values-should-not-be-strings_1.cpp)]

## <a name="related-rules"></a>Règles associées
 [CA1056 : Les propriétés d’URI ne doivent pas être des chaînes](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1054 : Les paramètres d’URI ne doivent pas être des chaînes](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA2234 : Passez des objets System.Uri au lieu de chaînes](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1057 : Les surcharges d’URI de chaîne appellent des surcharges de System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)