---
title: 'CA2153 : éviter la gestion des exceptions d’état endommagé'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3ca36093afa0915352c6c6d90995bde99fb655c8
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="ca2153-avoid-handling-corrupted-state-exceptions"></a>CA2153 : éviter la gestion des exceptions d’état endommagé

|||
|-|-|
|TypeName|AvoidHandlingCorruptedStateExceptions|
|CheckId|CA2153|
|Category|Microsoft.Security|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

[Endommagé des Exceptions d’état (CSE)](https://msdn.microsoft.com/magazine/dd419661.aspx) indiquent que la mémoire endommagées dans votre processus. Le fait d’intercepter ces exceptions au lieu d’autoriser le processus à se bloquer peut engendrer des failles de sécurité si une personne malveillante réussit à placer une attaque dans la région de la mémoire endommagée.

## <a name="rule-description"></a>Description de la règle
 Les CSE indiquent que l’état d’un processus a été endommagé et qu’il n’a pas été intercepté par le système. Dans un scénario d’état endommagé, un gestionnaire général intercepte uniquement l’exception si votre méthode est marquée au moyen de l’attribut `HandleProcessCorruptedStateExceptions` approprié. Par défaut, le [Common Language Runtime (CLR)](/dotnet/standard/clr) n’appelle pas de gestionnaires catch pour les extensions côté client.

 L’option la plus sûre consiste à autoriser le blocage du processus sans intercepter ces types d’exceptions, dans la mesure où même le code de journalisation peut permettre à des personnes malveillantes d’exploiter les bogues d’endommagement de la mémoire.

 Cet avertissement se déclenche lors de l’interception de CSE au moyen d’un gestionnaire général qui intercepte toutes les exceptions, notamment catch(exception) ou catch(aucune exception spécifiée).

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour résoudre cet avertissement, vous devez effectuer l’une des opérations suivantes :

 1. Supprimer le `HandleProcessCorruptedStateExceptions` attribut. Cela a pour effet de rétablir le comportement du runtime par défaut selon lequel les CSE ne sont pas passées aux gestionnaires catch.

 2. Supprimer le gestionnaire catch général et privilégier les gestionnaires qui interceptent des types d’exceptions spécifiques.  Cela peut inclure des CSE si le code du gestionnaire arrive à les gérer en toute sécurité (ce qui est très rare).

 3. Lever à nouveau l’exception CSE dans le gestionnaire catch pour garantir le passage de l’exception à l’appelant et l’arrêt consécutif du processus en cours d’exécution.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="pseudo-code-example"></a>Exemple de pseudo-code

### <a name="violation"></a>Violation
 Le pseudo-code suivant illustre le modèle détecté par cette règle.

```
[HandleProcessCorruptedStateExceptions]
//method to handle and log CSE exceptions
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle error
    }
}
```

### <a name="solution-1"></a>Solution 1
 Supprimez l’attribut HandleProcessCorruptedExceptions pour faire en sorte que les exceptions ne soient pas gérées.

```
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (IOException e)
    {
        // Handle error
    }
    catch (UnauthorizedAccessException e)
    {
        // Handle error
    }
}
```

### <a name="solution-2"></a>Solution 2
 Supprimez le gestionnaire catch général et interceptez uniquement des types d’exceptions spécifiques.

```
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (IOException e)
    {
        // Handle error
    }
    catch (UnauthorizedAccessException e)
    {
        // Handle error
    }
}
```

### <a name="solution-3"></a>Solution 3
 Levez à nouveau l’exception.

```
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle error
        throw;
    }
}
```