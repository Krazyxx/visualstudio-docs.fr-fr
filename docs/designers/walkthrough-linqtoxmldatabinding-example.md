---
title: 'Procédure pas à pas : exemple LinqToXmlDataBinding'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: aedf42e8-896c-48fa-88df-7f7c9536aa69
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3aa99324969f7fedfea7596dce55f9167ad6bb9a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-linqtoxmldatabinding-example"></a>Procédure pas à pas : exemple LinqToXmlDataBinding
Cette procédure pas à pas décrit l'exemple LinqToXmlDataBinding et fournit des explications concernant les aspects les plus intéressants du contenu des deux principaux fichiers sources, L2DBForm.xaml et L2DBForm.xaml.cs.

## <a name="prerequisites"></a>Conditions préalables
 Avant de lire cette procédure pas à pas, nous vous conseillons vivement de générer et d’exécuter le programme LinqToXmlDataBinding décrit dans [Guide pratique pour générer et exécuter l’exemple LinqToXmlDataBinding](../designers/how-to-build-and-run-the-linqtoxmldatabinding-example.md).

## <a name="remarks"></a>Notes
 Le programme LinqToXmlDataBinding est une application WPF (Windows Presentation Foundation) composée de fichiers sources C# et XAML. Il contient un document XML incorporé qui définit une liste de livres et permet à l'utilisateur d'afficher, d'ajouter, de supprimer et de modifier ces entrées. Il est constitué des deux principaux fichiers sources suivants :

-   L2DBForm.xaml contient le code de déclaration XAML pour l'interface utilisateur de la fenêtre principale. Il contient également une section de ressources de fenêtre qui définit un fournisseur de données et un document XML incorporé pour les listes de livres.

-   L2DBForm.xaml.cs contient les méthodes d'initialisation et de gestion d'événements associées à l'interface utilisateur.

 La fenêtre principale est composée des quatre sections d'interface utilisateur verticales suivantes :

-   **XML** affiche la source XML brute de la liste de livres incorporée.

-   **Book List** affiche les entrées de livres au format texte standard et permet à l’utilisateur de sélectionner et de supprimer des entrées.

-   **Edit Selected Book** permet à l’utilisateur de modifier les valeurs associées à l’entrée de livre sélectionnée.

-   **Add New Book** permet la création d’une nouvelle entrée de livre sur la base des valeurs entrées par l’utilisateur.

## <a name="in-this-section"></a>Dans cette section

|Rubrique|Description|
|-----------|-----------------|
|[Code source L2DBForm.xaml](../designers/l2dbform-xaml-source-code.md)|Présente le contenu et la description du code XAML dans le fichier L2DBForm.xaml.|
|[Code source L2DBForm.xaml.cs](../designers/l2dbform-xaml-cs-source-code.md)|Présente le contenu et la description du code source C# dans le fichier L2DBForm.xaml.cs.|

## <a name="see-also"></a>Voir aussi

- [Exemple de liaison de données WPF à l’aide de LINQ to XML](../designers/wpf-data-binding-using-linq-to-xml-example.md)
- [Procédure : générer et exécuter l’exemple LinqToXmlDataBinding](../designers/how-to-build-and-run-the-linqtoxmldatabinding-example.md)