---
title: Élément ItemDefinitionGroup (MSBuild) | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ItemDefinitionGroup
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ItemDefinitionGroup Element [MSBuild]
- <ItemDefinitionGroup> Element [MSBuild]
ms.assetid: 4e9fb04b-5148-4ae5-a394-42861dd62371
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c064f3398ac29cfa4187c19139e9264e2925689f
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="itemdefinitiongroup-element-msbuild"></a>ItemDefinitionGroup, élément (MSBuild)
L’élément `ItemDefinitionGroup` vous permet de définir un ensemble de définitions d’élément, correspondant à des valeurs de métadonnées appliquées par défaut à tous les éléments du projet. ItemDefinitionGroup évite d’avoir à utiliser les tâches [CreateItem](../msbuild/createitem-task.md) et [CreateProperty](../msbuild/createproperty-task.md). Pour plus d’informations, consultez l’article [Item Definitions (Définitions des éléments)](../msbuild/item-definitions.md).  

 \<Project>  
 \<ItemDefinitionGroup>  

## <a name="syntax"></a>Syntaxe  

```  
<ItemDefinitionGroup Condition="'String A' == 'String B'">  
    <Item1>... </Item1>  
    <Item2>... </Item2>  
</ItemDefinitionGroup>  
```  

## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  

### <a name="attributes"></a>Attributs  

|Attribut|Description|  
|---------------|-----------------|  
|`Condition`|Attribut facultatif. Condition à évaluer. Pour plus d’informations, consultez l’article [Conditions (Conditions MSBuild)](../msbuild/msbuild-conditions.md).|  

### <a name="child-elements"></a>Éléments enfants  

|Élément|Description|  
|-------------|-----------------|  
|[Item](../msbuild/item-element-msbuild.md)|Définit les entrées du processus de génération. Un élément `ItemDefinitionGroup` peut ne contenir aucun élément `Item` ou en contenir plusieurs.|  

### <a name="parent-elements"></a>Éléments parents  

|Élément|Description|  
|-------------|-----------------|  
|[Projet](../msbuild/project-element-msbuild.md)|Élément racine requis d'un fichier projet [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] .|  

## <a name="example"></a>Exemple  
 L’exemple de code suivant définit deux éléments de métadonnées, m et n, dans un élément ItemDefinitionGroup. Dans cet exemple, les métadonnées par défaut « m » sont appliquées à l’élément « i », car les métadonnées « m » ne sont pas explicitement définies par l’élément « i ». Cependant, les métadonnées par défaut « n » ne sont pas appliquées à l’élément « i », car les métadonnées « n » sont déjà définies par l’élément « i ».  

```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemDefinitionGroup>  
        <i>  
            <m>m1</m>  
            <n>n1</n>  
        </i>        
    </ItemDefinitionGroup>  
    <ItemGroup>  
        <i Include="a">  
            <o>o1</o>  
            <n>n2</n>  
        </i>  
    </ItemGroup>  
    ...  
</Project>  
```  

## <a name="see-also"></a>Voir aussi  
 [Référence du schéma de fichier projet](../msbuild/msbuild-project-file-schema-reference.md)   
 [Éléments](../msbuild/msbuild-items.md)
