---
title: Guide pratique pour créer un héritage entre les types (Concepteur de classes)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.inheritanceline
helpviewer_keywords:
- inheritance, relationship defining
- relationships, defining inheritance
ms.assetid: 3786a21c-8022-4bf5-9d13-740fd354e93c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 13f89a15b0ec734e29e27fe652ee7e71b791db50
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-inheritance-between-types-class-designer"></a>Guide pratique pour créer l’héritage entre les types (Concepteur de classes)

Pour créer une relation d’héritage entre deux types sur un diagramme de classes à l’aide du **Concepteur de classes**, connectez le type de base à son ou ses types dérivés. Vous pouvez avoir une relation d'héritage entre deux classes, entre une classe et une interface ou entre deux interfaces.

## <a name="to-create-an-inheritance-between-types"></a>Pour créer un héritage entre des types

1.  À partir de votre projet affiché dans **l’Explorateur de solutions**, ouvrez le fichier du diagramme de classes (.cd).

     Si vous n'avez pas de diagramme de classes, créez-en un. Consultez [Guide pratique pour ajouter des diagrammes de classes aux projets](how-to-add-class-diagrams-to-projects.md).

2.  Dans la **boîte à outil**, sous **Concepteur de classes**, cliquez sur **Héritage**.

3.  Dans le diagramme de classes, dessinez une ligne d'héritage entre les types de votre choix, depuis :

    -   une classe dérivée vers la classe de base ;

    -   une classe d'implémentation vers l'interface implémentée ;

    -   une interface d'extension vers l'interface étendue.

4.  Éventuellement, dans le cas d'un type dérivé d'un type générique, cliquez sur la ligne d'héritage. Dans la fenêtre **Propriétés**, définissez la propriété **Arguments de type** sur le type souhaité pour le type générique.

    > [!NOTE]
    > Si une classe abstraite parente contient au moins un membre abstrait, tous les membres abstraits sont implémentés en tant que classes d'héritage non abstraites.
    >
    >  Bien que vous puissiez visualiser les types génériques existants, vous ne pouvez pas créer de types génériques. En outre, vous ne pouvez pas modifier les paramètres des types génériques existants.

## <a name="see-also"></a>Voir aussi

- [Héritage](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)
- [Éléments fondamentaux de l’héritage](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)
- [Guide pratique pour afficher l’héritage entre des types](how-to-view-inheritance-between-types.md)
- [Classes de Visual C++ dans le concepteur de classes](visual-cpp-classes.md)