---
title: Lier des contrôles WPF à un service de données WCF
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 8823537c-82f0-41f7-bf30-705f0e5e59fd
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 8152a02df8f335a92024134dde89b45d2f3e115a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="bind-wpf-controls-to-a-wcf-data-service"></a>Lier des contrôles WPF à un service de données WCF

Dans cette procédure pas à pas, vous allez créer une application WPF qui contient des contrôles liés aux données. Les contrôles sont liés aux enregistrements client encapsulés dans un [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)]. Vous allez aussi ajouter des boutons utilisables par les clients pour afficher et mettre à jour des enregistrements.

Cette procédure pas à pas décrit les tâches suivantes :

- Création d'un Entity Data Model généré à partir des données de l'exemple de base de données AdventureWorksLT.

- Création d’un [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] qui expose les données de l’Entity Data Model à une application WPF.

- Création d’un ensemble de contrôles liés aux données en faisant glisser des éléments depuis la **des Sources de données** fenêtre vers le Concepteur WPF.

- Création de boutons permettant d'avancer et de reculer dans les enregistrements client.

- Création d’un bouton qui enregistre les modifications apportées aux données dans les contrôles à le [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] et la source de données sous-jacente.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>Prérequis
Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :

-   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]

-   Accès à une instance en cours d'exécution de SQL Server ou SQL Server Express à laquelle est attaché l'exemple de base de données AdventureWorksLT. Vous pouvez télécharger la base de données AdventureWorksLT à partir de la [site CodePlex Web](http://go.microsoft.com/fwlink/?linkid=87843).

La connaissance préalable des concepts suivants s'avère également utile, mais n'est pas obligatoire pour suivre cette procédure pas à pas :

-   Services de données WCF. Pour plus d’informations, consultez [vue d’ensemble](/dotnet/framework/data/wcf/wcf-data-services-overview).

-   Modèles de données dans les [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)].

-   Entity Data Models et ADO.NET Entity Framework. Pour plus d’informations, consultez [présentation d’Entity Framework](/dotnet/framework/data/adonet/ef/overview).

-   Liaison de données WPF. Pour plus d’informations, consultez [Vue d’ensemble de la liaison de données](/dotnet/framework/wpf/data/data-binding-overview).

## <a name="create-the-service-project"></a>Créer le projet de service
Commencez cette procédure pas à pas par la création d'un projet pour un [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].

### <a name="to-create-the-service-project"></a>Pour créer le projet de service

1.  Démarrez Visual Studio.

2.  Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.

3.  Développez **Visual C#** ou **Visual Basic**, puis sélectionnez **Web**.

4.  Sélectionnez le modèle de projet **Application web ASP.NET**.

5.  Dans le **nom** , tapez `AdventureWorksService` et cliquez sur **OK**.

     Visual Studio crée le `AdventureWorksService` projet.

6.  Dans **l’Explorateur de solutions**, avec le bouton droit **Default.aspx** et sélectionnez **supprimer**. Ce fichier n'est pas nécessaire dans cette procédure pas à pas.

## <a name="create-an-entity-data-model-for-the-service"></a>Créer un Entity Data Model pour le service
Pour exposer les données à une application à l'aide d'un [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)], vous devez définir un modèle de données pour le service. Le [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] prend en charge deux types de modèles de données : Entity Data Models et modèles de données personnalisés qui sont définies à l’aide des objets common language runtime (CLR) qui implémentent la <xref:System.Linq.IQueryable%601> interface. Dans cette procédure pas à pas, vous allez créer un Entity Data Model comme modèle de données.

### <a name="to-create-an-entity-data-model"></a>Pour créer un Entity Data Model

1.  Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.

2.  Dans la liste des modèles installés, cliquez sur **données**, puis sélectionnez le **ADO.NET Entity Data Model** élément de projet.

3.  Remplacez le nom par `AdventureWorksModel.edmx`, puis cliquez sur **ajouter**.

     Le **Entity Data Model** Assistant s’ouvre.

4.  Sur le **choisir le contenu du modèle** , cliquez sur **générer à partir de la base de données**, puis cliquez sur **suivant**.

5.  Sur le **choisir votre connexion de données** page, sélectionnez une des options suivantes :

    -   Si une connexion de données à l’exemple de base de données AdventureWorksLT est disponible dans la liste déroulante, sélectionnez-la.

    -   Cliquez sur **nouvelle connexion**et créer une connexion à la base de données AdventureWorksLT.

6.  Sur le **choisir votre connexion de données** , assurez-vous que le **enregistrer les paramètres de connexion de l’entité dans App.Config en tant que** option est sélectionnée, puis cliquez sur **suivant**.

7.  Sur le **choisir vos objets de base de données** page, développez **Tables**, puis sélectionnez le **SalesOrderHeader** table.

8.  Cliquez sur **Terminer**.

## <a name="create-the-service"></a>Créer le service
Créer un [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] pour exposer les données dans l’Entity Data Model à une application WPF.

### <a name="to-create-the-service"></a>Pour créer le service

1.  Sur le **projet** menu, sélectionnez **ajouter un nouvel élément**.

2.  Dans la liste des modèles installés, cliquez sur **Web**, puis sélectionnez le **Service de données WCF** élément de projet.

3.  Dans le **nom** , tapez `AdventureWorksService.svc`, puis cliquez sur **ajouter**.

     Visual Studio ajoute le `AdventureWorksService.svc` au projet.

## <a name="configure-the-service"></a>Configurer le service
Vous devez configurer le service pour qu'il fonctionne sur l'Entity Data Model que vous avez créé.

### <a name="to-configure-the-service"></a>Pour configurer le service

1.  Dans le `AdventureWorks.svc` fichier de code, remplacez le `AdventureWorksService` classe déclaration avec le code suivant.

     [!code-csharp[Data_WPFWCF#1](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_1.cs)]
     [!code-vb[Data_WPFWCF#1](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_1.vb)]

     Ce code met à jour la `AdventureWorksService` classe, afin qu’elle dérive un <xref:System.Data.Services.DataService%601> qui fonctionne sur le `AdventureWorksLTEntities` de l’objet classe de contexte dans votre Entity Data Model. Il met également à jour la méthode `InitializeService` pour accorder aux clients du service un accès complet en lecture/écriture à l'entité `SalesOrderHeader`.

2.  Générez le projet et vérifiez qu'aucune erreur ne se produit.

## <a name="create-the-wpf-client-application"></a>Créer l’application cliente WPF
Pour afficher les données du [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)], créez une application WPF avec une source de données basée sur le service. Plus loin dans cette procédure pas à pas, vous allez ajouter à l'application des contrôles liés aux données.

### <a name="to-create-the-wpf-client-application"></a>Pour créer l'application cliente WPF

1.  Dans **l’Explorateur de solutions**, cliquez sur le nœud solution, cliquez sur **ajouter**, puis sélectionnez **nouveau projet**.

2.  Dans le **nouveau projet** boîte de dialogue, développez **Visual C#** ou **Visual Basic**, puis sélectionnez **Windows**.

3.  Sélectionnez le **Application WPF** modèle de projet.

4.  Dans le **nom** , tapez `AdventureWorksSalesEditor`, puis cliquez sur **OK**.

     Visual Studio ajoute le `AdventureWorksSalesEditor` projet à la solution.

5.  Dans le menu **Données** , cliquez sur **Afficher les sources de données**.

     Le **des Sources de données** fenêtre s’ouvre.

6.  Dans la fenêtre **Sources de données** , cliquez sur **Ajouter une nouvelle source de données**.

     Le **Configuration de Source de données** Assistant s’ouvre.

7.  Dans le **choisir un Type de Source de données** page de l’Assistant, sélectionnez **Service**, puis cliquez sur **suivant**.

8.  Dans le **ajouter une référence de Service** boîte de dialogue, cliquez sur **Discover**.

     Visual Studio recherche la solution actuelle pour les services disponibles et ajoute `AdventureWorksService.svc` à la liste des services disponibles dans le **Services** boîte.

9. Dans le **Namespace** , tapez `AdventureWorksService`.

10. Dans le **Services** , cliquez sur **AdventureWorksService.svc**, puis cliquez sur **OK**.

     Visual Studio télécharge les informations de service et renvoie à la **Configuration de Source de données** Assistant.

11. Dans le **ajouter une référence de Service** , cliquez sur **Terminer**.

     Visual Studio ajoute des nœuds qui représentent les données retournées par le service pour le **des Sources de données** fenêtre.

## <a name="define-the-user-interface-of-the-window"></a>Définir l’interface utilisateur de la fenêtre
Ajoutez plusieurs boutons à la fenêtre en modifiant le code XAML dans le Concepteur WPF. Plus loin dans cette procédure pas à pas, vous allez ajouter du code permettant aux utilisateurs d'afficher et de mettre à jour les enregistrements de vente à l'aide de ces boutons.

### <a name="to-create-the-window-layout"></a>Pour créer la disposition de fenêtre

1.  Dans **l’Explorateur de solutions**, double-cliquez sur **MainWindow.xaml**.

     La fenêtre s'ouvre dans le Concepteur WPF.

2.  Dans la vue [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] du concepteur, ajoutez le code suivant entre les balises `<Grid>` :

    ```xaml
    <Grid.RowDefinitions>
        <RowDefinition Height="75" />
        <RowDefinition Height="525" />
    </Grid.RowDefinitions>
    <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>
    <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>
    <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>
    ```

3.  Générez le projet.

## <a name="create-the-data-bound-controls"></a>Créer des contrôles liés aux données
Créer des contrôles qui affichent les enregistrements client en faisant glisser le `SalesOrderHeaders` nœud à partir de la **des Sources de données** fenêtre vers le concepteur.

### <a name="to-create-the-data-bound-controls"></a>Pour créer des contrôles liés aux données

1.  Dans le **des Sources de données** fenêtre, cliquez sur le menu déroulant pour le **SalesOrderHeaders** nœud et sélectionnez **détails**.

2.  Développez le **SalesOrderHeaders** nœud.

3.  Pour cet exemple, certains champs n’apparaissent pas, par conséquent, cliquez sur le menu déroulant en regard des nœuds suivants et sélectionnez **aucun**:

    -   **CreditCardApprovalCode**

    -   **ModifiedDate**

    -   **OnlineOrderFlag**

    -   **RevisionNumber**

    -   **ROWGUID**

    Cette action empêche Visual Studio de créer des contrôles liés aux données pour ces nœuds à l'étape suivante. Pour cette procédure pas à pas, supposons que l’utilisateur final n’avez pas besoin d’afficher ces données.

4.  À partir de la **des Sources de données** fenêtre, faites glisser le **SalesOrderHeaders** nœud à la ligne de la grille sous la ligne qui contient les boutons.

     Visual Studio génère du XAML et code qui crée un ensemble de contrôles liés aux données dans le **produit** table. Pour plus d’informations sur le XAML et le code généré, consultez [WPF de lier des contrôles aux données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

5.  Dans le concepteur, cliquez sur la zone de texte en regard du **ID de client** étiquette.

6.  Dans le **propriétés** fenêtre, sélectionnez la case à cocher à côté du **IsReadOnly** propriété.

7.  Définir le **IsReadOnly** propriété pour chacune des zones de texte suivantes :

    -   **Numéro de bon de commande**

    -   **ID de commande**

    -   **Numéro de commande client**

## <a name="load-the-data-from-the-service"></a>Charger les données à partir du service
Utilisez l’objet proxy de service pour charger les données de ventes à partir du service. Puis assignez les données retournées à la source de données pour la <xref:System.Windows.Data.CollectionViewSource> dans la fenêtre WPF.

### <a name="to-load-the-data-from-the-service"></a>Pour charger les données du service

1.  Dans le concepteur, pour créer le `Window_Loaded` Gestionnaire d’événements, double-cliquez sur le texte : **MainWindow**.

2.  Remplacez le gestionnaire d'événements par le code suivant. Assurez-vous que vous remplacez le *localhost* adresse dans ce code avec l’adresse d’hôte local sur votre ordinateur de développement.

     [!code-csharp[Data_WPFWCF#2](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_2.cs)]
     [!code-vb[Data_WPFWCF#2](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_2.vb)]

## <a name="navigate-sales-records"></a>Parcourir les enregistrements de ventes
Ajoutez le code qui permet aux utilisateurs de faire défiler les enregistrements de vente à l’aide de la **\<** et **>** boutons.

### <a name="to-enable-users-to-navigate-sales-records"></a>Pour permettre aux utilisateurs de parcourir les enregistrements de vente

1.  Dans le concepteur, double-cliquez sur le **<** bouton sur la surface de la fenêtre.

     Visual Studio ouvre le fichier code-behind et crée un nouveau `backButton_Click` Gestionnaire d’événements pour le <xref:System.Windows.Controls.Primitives.ButtonBase.Click> événement.

2.  Ajoutez le code suivant au gestionnaire d'événements `backButton_Click` généré :

     [!code-csharp[Data_WPFWCF#3](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_3.cs)]
     [!code-vb[Data_WPFWCF#3](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_3.vb)]

3.  Revenez dans le concepteur, double-cliquez sur le **>** bouton.

     Visual Studio ouvre le fichier code-behind et crée un nouveau `nextButton_Click` Gestionnaire d’événements pour le <xref:System.Windows.Controls.Primitives.ButtonBase.Click> événement.

4.  Ajoutez le code suivant au gestionnaire d'événements `nextButton_Click` généré :

     [!code-csharp[Data_WPFWCF#4](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_4.cs)]
     [!code-vb[Data_WPFWCF#4](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_4.vb)]

## <a name="saving-changes-to-sales-records"></a>Enregistrement des modifications apportées aux enregistrements de vente
Ajoutez le code qui permet aux utilisateurs d’afficher et enregistrer les modifications apportées aux enregistrements de vente à l’aide de la **enregistrer les modifications** bouton.

### <a name="to-add-the-ability-to-save-changes-to-sales-records"></a>Pour ajouter la possibilité d'enregistrer les modifications apportées aux enregistrements de vente

1.  Dans le concepteur, double-cliquez sur le **enregistrer les modifications** bouton.

     Visual Studio ouvre le fichier code-behind et crée un nouveau `saveButton_Click` Gestionnaire d’événements pour le <xref:System.Windows.Controls.Primitives.ButtonBase.Click> événement.

2.  Ajoutez le code ci-après au gestionnaire d'événements `saveButton_Click`.

     [!code-csharp[Data_WPFWCF#5](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_5.cs)]
     [!code-vb[Data_WPFWCF#5](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_5.vb)]

## <a name="testing-the-application"></a>Test de l'application
Générez et exécutez l'application pour vérifier que vous pouvez afficher et mettre à jour les enregistrements client.

### <a name="to-test-the-application"></a>Pour tester l'application

1.  Sur **générer** menu, cliquez sur **générer la Solution**. Vérifiez que la solution se génère sans erreur.

2.  Appuyez sur **Ctrl + F5**.

     Visual Studio démarre le **AdventureWorksService** projet, sans le déboguer.

3.  Dans **l’Explorateur de solutions**, cliquez sur le **AdventureWorksSalesEditor** projet.

4.  Dans le menu contextuel, sous **déboguer**, cliquez sur **démarrer une nouvelle instance**.

     L'application s'exécute. Vérifiez ce qui suit :

    -   Les zones de texte affichent différents champs de données du premier enregistrement de client, ce qui a l’ID de commande **71774**.

    -   Vous pouvez cliquer sur le **>** ou **<** boutons pour parcourir les autres enregistrements de vente.

5.  Dans un des enregistrements de ventes, tapez du texte dans le **commentaire** zone, puis cliquez sur **enregistrer les modifications**.

6.  Fermez l'application, puis redémarrez-la à partir de Visual Studio.

7.  Accédez à l'enregistrement de vente que vous avez modifié et vérifiez que la modification est toujours présente après avoir fermé et réouvert l'application.

8.  Fermez l'application.

## <a name="next-steps"></a>Étapes suivantes

Une fois cette procédure pas à pas terminée, vous pouvez effectuer les tâches associées suivantes :

-   Découvrez comment utiliser le **des Sources de données** contrôle de fenêtre dans Visual Studio pour lier WPF à d’autres types de sources de données. Pour plus d’informations, consultez [WPF de lier des contrôles à un jeu de données](../data-tools/bind-wpf-controls-to-a-dataset.md).

-   Découvrez comment utiliser le **des Sources de données** fenêtre dans Visual Studio pour afficher les données associées (autrement dit, les données dans une relation parent-enfant) dans des contrôles WPF. Pour plus d’informations, consultez [procédure pas à pas : affichage des données connexes dans une Application WPF](../data-tools/display-related-data-in-wpf-applications.md).

## <a name="see-also"></a>Voir aussi

- [Lier des contrôles WPF à des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [Lier des contrôles WPF à un dataset](../data-tools/bind-wpf-controls-to-a-dataset.md)
- [Vue d’ensemble WCF (.NET Framework)](/dotnet/framework/data/wcf/wcf-data-services-overview)
- [Présentation d’Entity Framework (.NET Framework)](/dotnet/framework/data/adonet/ef/overview)
- [Vue d’ensemble (.NET Framework) de liaison de données](/dotnet/framework/wpf/data/data-binding-overview)