---
title: 'CA1025: Replace repetitive arguments with params array | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1025
- ReplaceRepetitiveArgumentsWithParamsArray
helpviewer_keywords:
- ReplaceRepetitiveArgumentsWithParamsArray
- CA1025
ms.assetid: f009b340-dea3-4459-8fe1-2143aa8b5d0b
caps.latest.revision: 14
author: stevehoag
ms.author: shoag
manager: wpickett
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: 149d34bcf1192fa93e6ee5416c8003e965f6fc3f
ms.contentlocale: fr-fr
ms.lasthandoff: 08/30/2017

---
# <a name="ca1025-replace-repetitive-arguments-with-params-array"></a>CA1025: Replace repetitive arguments with params array
|||  
|-|-|  
|TypeName|ReplaceRepetitiveArgumentsWithParamsArray|  
|CheckId|CA1025|  
|Category|Microsoft.Design|  
|Breaking Change|Non-breaking|  
  
## <a name="cause"></a>Cause  
 A public or protected method in a public type has more than three parameters, and its last three parameters are the same type.  
  
## <a name="rule-description"></a>Rule Description  
 Use a parameter array instead of repeated arguments when the exact number of arguments is unknown and the variable arguments are the same type, or can be passed as the same type. For example, the <xref:System.Console.WriteLine%2A> method provides a general-purpose overload that uses a parameter array to accept any number of <xref:System.Object> arguments.  
  
## <a name="how-to-fix-violations"></a>How to Fix Violations  
 To fix a violation of this rule, replace the repeated arguments with a parameter array.  
  
## <a name="when-to-suppress-warnings"></a>When to Suppress Warnings  
 It is always safe to suppress a warning from this rule; however, this design might cause usability issues.  
  
## <a name="example"></a>Example  
 The following example shows a type that violates this rule.  
  
 [!code-csharp[FxCop.Design.RepeatArgs#1](../code-quality/codesnippet/CSharp/ca1025-replace-repetitive-arguments-with-params-array_1.cs)]