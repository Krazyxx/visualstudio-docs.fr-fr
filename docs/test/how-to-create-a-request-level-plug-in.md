---
title: Créer un plug-in de niveau de requête pour les tests de performances web dans Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- request-level plug-in, creating
- Web performance tests, requests
ms.assetid: d0b5b23c-7e94-4637-be6c-2620a5442d46
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: ea574f2f0c9b4d3f0f6da029433b5b600a400702
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-a-request-level-plug-in"></a>Comment : créer un plug-in de niveau demande

Les *requêtes* sont les instructions déclaratives qui constituent les tests de performances web. Les plug-ins de tests de performances de site Web vous permettent d'isoler et de réutiliser du code en dehors des principales instructions déclaratives de votre test de performances de site Web. Vous pouvez créer des plug-ins et les ajouter à une requête individuelle aussi bien qu'au test de performances de site Web qui la contient. Un *plug-in de requête* personnalisé permet d’appeler du code quand une requête particulière est exécutée dans un test de performances web.

Chaque plug-in de requête de test de performances de site Web comporte une méthode PreRequest et une méthode PostRequest. Après avoir joint un plug-in de requête à une requête HTTP particulière, l'événement PreRequest est déclenché avant l'émission de la requête et l'événement PostRequest après la réception de la réponse.

Vous pouvez créer un plug-in de requête de test de performances de site Web personnalisé en dérivant votre propre classe de la classe de base <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>.

En outre, vous pouvez utiliser des plug-ins de requête de test de performances de site Web personnalisés avec des tests de performances de site Web enregistrés. Les plug-ins de requête de test de performances de site Web personnalisés vous permettent de minimiser le code à écrire pour arriver à mieux contrôler vos tests de performances de site Web. Toutefois, vous pouvez également les utiliser avec des tests de performances de site web codés. Consultez [Générer et exécuter un test de performances web codé](../test/generate-and-run-a-coded-web-performance-test.md).

## <a name="to-create-a-request-level-plug-in"></a>Pour créer un plug-in de niveau demande

1.  Dans l'Explorateur de solutions, cliquez avec le bouton droit sur la solution, sélectionnez **Ajouter**, puis choisissez **Nouveau projet**.

     La boîte de dialogue **Ajouter un nouveau projet** s’affiche.

2.  Sous **Modèles installés**, sélectionnez **Visual C#**.

3.  Dans la liste des modèles, sélectionnez **Bibliothèque de classes**.

4.  Dans la zone de texte **Nom**, tapez un nom pour votre classe, puis choisissez **OK**.

     Le nouveau projet de bibliothèque de classes est ajouté à l'Explorateur de solutions et la nouvelle classe s'affiche dans l'éditeur de code.

5.  Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le dossier **Références** de la nouvelle bibliothèque de classes, puis sélectionnez **Ajouter une référence**.

     La boîte de dialogue **Ajouter une référence** s’affiche.

6.  Choisissez l’onglet **.NET**, faites défiler la liste vers le bas, sélectionnez **Microsoft.VisualStudio.QualityTools.WebTestFramework**, puis cliquez sur **OK**

     La référence à **Microsoft.VisualStudio.QualityTools.WebTestFramework** est ajoutée au dossier **Référence** dans l’Explorateur de solutions.

7.  Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le nœud supérieur du projet de test de performances Web et de charge auquel vous souhaitez ajouter le plug-in du test de demande de test de performances Web. Sélectionnez **Ajouter une référence**.

     La boîte de dialogue **Ajouter une référence** s’affiche.

8.  Choisissez l’onglet **Projets**, sélectionnez le projet de bibliothèque de classes, puis choisissez **OK**.

9. Dans l'éditeur Code, écrivez le code de votre plug-in. Commencez par créer une classe publique qui dérive de <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>.

10. Implémentez le code à l'intérieur d'un des gestionnaires d'événements <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin.PreRequest*> et <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin.PostRequest*>. Pour un exemple d'implémentation, reportez-vous à la section suivante.

11. Après avoir écrit le code, générez le nouveau projet.

12. Ouvrez le test de performances de site Web auquel vous souhaitez ajouter le plug-in de requête.

13. Cliquez avec le bouton droit sur la requête à laquelle vous souhaitez ajouter le plug-in de requête, puis sélectionnez **Ajouter un plug-in de requête**.

     La boîte de dialogue **Ajouter un plug-in de requête de test web** s’affiche.

14. Sous **Sélectionner un plug-in**, sélectionnez votre nouveau plug-in.

15. Dans le volet **Propriétés du plug-in sélectionné**, définissez les valeurs initiales du plug-in à utiliser au moment de l’exécution.

    > [!NOTE]
    > Vous pouvez exposer autant de propriétés que vous souhaitez de vos plug-ins ; il suffit de les rendre publics, définissables et d'un type de base, tel qu'un entier, une valeur booléenne ou une chaîne. Vous pouvez également modifier ultérieurement les propriétés du plug-in de test de performances de site web dans la fenêtre Propriétés.

16. Cliquez sur **OK**.

     Le plug-in est ajouté au dossier **Plug-ins de requête**, qui est un dossier enfant de la requête HTTP.

    > [!WARNING]
    > Vous pouvez obtenir une erreur semblable au cas suivant lorsque vous exécutez un test de performances de site web ou un test de charge qui utilise votre plug-in :
    >
    > **Échec de la requête : exception dans le \<plug-in> événement : Impossible de charger le fichier ou l’assembly '\<"Nom du plug-in".dll>, Version=\<n.n.n.n>, Culture=neutral, PublicKeyToken=null' ou l’une de ses dépendances. Le système ne parvient pas à localiser le fichier spécifié.**
    >
    > Cela se produit si vous effectuez des modifications du code dans l’un de vos plug-ins et si vous créez une autre version de la DLL **(Version=0.0.0.0)**. Toutefois, le plug-in fait toujours référence à la version du plug-in d’origine. Pour résoudre ce problème, procédez comme suit :
    >
    > 1.  Dans votre projet de test de performances de site web et de charge, un message d'avertissement s'affiche dans les références. Supprimez et rajoutez la référence à la DLL de votre plug-in.
    > 2.  Supprimez le plug-in de votre test ou de l'emplacement approprié, puis rajoutez-le.

## <a name="example"></a>Exemple

Vous pouvez utiliser le code suivant pour créer un plug-in de test de performances de site Web personnalisé qui affiche deux boîtes de dialogue. La première boîte de dialogue affiche l'URL associée à la requête à laquelle vous joignez le complément de requête. La deuxième boîte de dialogue affiche le nom de l'ordinateur de l'agent.

> [!NOTE]
> Le code suivant requiert l'ajout d'une référence à System.Windows.Forms.

```csharp
using System;
using System.Collections.Generic;
using System.Windows.Forms;
using Microsoft.VisualStudio.TestTools.WebTesting;

namespace RequestPluginNamespace
{
    public class MyWebRequestPlugin : WebTestRequestPlugin
    {
        public override void PostRequest(object sender, PostRequestEventArgs e)
        {
            MessageBox.Show(e.WebTest.Context.AgentName);
        }
        public override void PreRequest(object sender, PreRequestEventArgs e)
        {
            MessageBox.Show(e.Request.Url);
        }
    }
}
```

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>
- [Créer du code et des plug-ins personnalisés pour les tests de charge](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Codage d’une règle d’extraction personnalisée pour un test de performances web](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
- [Codage d’une règle de validation personnalisée pour un test de performances web](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
- [Guide pratique pour créer un plug-in de test de charge](../test/how-to-create-a-load-test-plug-in.md)
- [Générer et exécuter un test de performances web codé](../test/generate-and-run-a-coded-web-performance-test.md)