---
title: "Exemple d'extension Excel : classe PropertyProvider"
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: sample
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: e4a1e96fc666275d83cf0f32edf00f0fc2f6c03c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="sample-excel-extension-propertyprovider-class"></a>Exemple d'extension Excel : classe PropertyProvider
Cette classe interne étend la classe <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> et fournit des services de propriétés pour des éléments [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] afin d’enregistrer et de lire des tests d’interface utilisateur.

## <a name="getcontrolsupportlevel-method"></a>Méthode GetControlSupportLevel
 La méthode <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetControlSupportLevel%2A> retourne un nombre qui indique le niveau de prise en charge que le fournisseur de propriétés peut offrir pour le contrôle fourni. Plus la valeur retournée est élevée, plus le fournisseur de propriétés peut prendre en charge le contrôle. Dans ce cas, la méthode vérifie la valeur de la propriété <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IUITechnologyElement.TechnologyName%2A> du contrôle fourni. Si la valeur est « Excel » et que <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IUITechnologyElement.ControlTypeName%2A> indique qu’il s’agit d’un `CellElement`, la méthode retourne la valeur la plus élevée. Sinon, elle retourne zéro, ce qui indique l’absence de prise en charge.

## <a name="getpropertynames-method"></a>Méthode GetPropertyNames
 Retourne un dictionnaire de noms de propriétés et de descripteurs de propriétés pour les propriétés prises en charge d’un contrôle Cell Excel.

## <a name="getpropertydescriptor-method"></a>Méthode GetPropertyDescriptor
 Cette méthode est appelée par le framework de test pour obtenir le descripteur de propriété prédéfini du nom de propriété fourni.

## <a name="getpropertyvalue-and-setpropertyvalue-methods"></a>Méthodes GetPropertyValue et SetPropertyValue
 La méthode `GetPropertyValue` utilise la classe `Communicator` de cette extension pour retourner la valeur de propriété à partir d’Excel. La méthode `SetPropertyValue` utilise la classe <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard> et le composant `Communicator` pour définir la valeur de propriété. Ces méthodes sont appelées par le framework de test.

## <a name="code-generation-customization-methods"></a>Méthodes de personnalisation de la génération de code
 Ces méthodes ne sont pas implémentées pour cette extension. Par conséquent, elles retournent `null` ou lèvent <xref:System.NotImplementedException>.

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>
- <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard>
- [Extension des tests codés de l’interface utilisateur et des enregistrements des actions pour prendre charge Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
