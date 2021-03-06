---
title: Définir une propriété Automation unique pour les contrôles UWP à des fins de test dans Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- uwp
author: gewarren
ms.openlocfilehash: ce916f181a6694eabc91cdb7c6a7dec9a8f5e5ac
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="set-a-unique-automation-property-for-uwp-controls-for-testing"></a>Définir une propriété Automation unique pour les contrôles UWP à des fins de test

Si vous voulez exécuter des tests codés de l’interface utilisateur pour vos applications UWP en XAML, vous devez définir une propriété Automation unique qui identifie chaque contrôle.

 Vous pouvez assigner une propriété Automation unique selon le type de contrôle XAML dans votre application. Voilà comment assigner cette propriété Automation unique dans les situations suivantes :

-   [Définition XAML statique des contrôles](#UniquePropertyWindowsStoreControlsStaticXAML)

-   [Assigner des propriétés Automation uniques à l’aide de Visual Studio ou Blend pour Visual Studio](#UniquePropertyWindowsStoreControlsExpressionBlend)

-   [Utiliser un modèle de données](#UniquePropertyWindowsStoreControlsDataTemplate)

-   [Utiliser un modèle de contrôle](#UniquePropertyWindowsStoreControlsControlTemplate)

-   [Contrôles dynamiques](#UniquePropertyWindowsStoreControlsDynamicControls)

## <a name="use-methods-to-assign-a-unique-automation-property"></a>Utilisez des méthodes permettant d’assigner une propriété Automation unique

###  <a name="UniquePropertyWindowsStoreControlsStaticXAML"></a> Définition XAML statique
 Pour spécifier une propriété Automation unique pour un contrôle défini dans votre fichier XAML, vous pouvez définir la valeur AutomationProperties.AutomationId ou AutomationProperties.Name implicitement ou explicitement, comme indiqué dans les exemples suivants. La définition de l’une ou l’autre de ces valeurs affecte au contrôle une propriété Automation unique qui peut être utilisée pour identifier ce contrôle lorsque vous créez un test codé de l’interface utilisateur ou un enregistrement des actions.

 **Définir la propriété implicitement**

Affectez à AutomationProperties.AutomationId la valeur **ButtonX** à l’aide de la propriété Name dans le code XAML du contrôle.

```xaml
<Button Name="ButtonX" Height="31" HorizontalAlignment="Left" Margin="23,26,0,0"  VerticalAlignment="Top" Width="140" Click="ButtonX_Click" />
```

Affectez à AutomationProperties.Name la valeur **ButtonY** à l’aide de la propriété Content dans le code XAML du contrôle.

```xaml
<Button Content="ButtonY" Height="31" HorizontalAlignment="Left" Margin="23,76,0,0" VerticalAlignment="Top" Width="140" Click="ButtonY_Click" />
```

 **Définir la propriété explicitement**

 Affectez à AutomationProperties.AutomationId la valeur **ButtonX** de façon explicite dans le code XAML du contrôle.

```xaml
<Button AutomationProperties.AutomationId="ButtonX" Height="31" HorizontalAlignment="Left" Margin="23,26,0,0"  VerticalAlignment="Top" Width="140" Click="ButtonX_Click" />
```

 Affectez à AutomationProperties.Name la valeur **ButtonY** de façon explicite dans le code XAML du contrôle.

```
<Button AutomationProperties.Name="ButtonY" Height="31" HorizontalAlignment="Left" Margin="23,76,0,0" VerticalAlignment="Top" Width="140" Click="ButtonY_Click" />
```

###  <a name="UniquePropertyWindowsStoreControlsExpressionBlend"></a> Assigner des propriétés Automation uniques à l’aide de Visual Studio ou Blend pour Visual Studio
 Vous pouvez utiliser Visual Studio ou Blend pour Visual Studio pour affecter des noms uniques à des éléments interactifs, comme des boutons, des zones de liste, des zones de liste modifiable et des zones de texte. Cela permet d’affecter au contrôle une valeur unique pour AutomationProperties.Name.

 **Visual Studio :** dans le menu **Outils**, pointez sur **Options**, choisissez **Éditeur de texte**, **XAML**, puis **Divers**.

 Cochez la case **Nommer automatiquement les éléments interactifs lors de la création**, puis cliquez sur **OK**.

 ![Options XAML diverses](../test/media/cuit_windowsstoreapp_b.png "CUIT_WindowsStoreApp_B")

 **Blend pour Visual Studio :** utilisez l’une des méthodes suivantes pour réaliser cela depuis Blend pour Visual Studio.

> [!NOTE]
> Vous pouvez utiliser cette méthode uniquement pour les contrôles créés de manière statique à l’aide du code XAML.


 **Pour affecter un nom unique à des contrôles existants**

 Dans le menu **Outils**, choisissez **Nommer les éléments interactifs**, comme illustré ci-dessous :

 ![Choisir Nommer les éléments interactifs dans le menu Outils ](../test/media/cuit_windowsstoreproperty_blend_1.png "CUIT_WindowsStoreProperty_Blend_1")

 **Pour affecter automatiquement un nom unique aux contrôles que vous créez**

 Dans le menu **Outils**, pointez sur **Options**, puis choisissez **Projet**. Cochez la case **Nommer automatiquement les éléments interactifs lors de la création**, puis cliquez sur **OK**, comme illustré ici :

 ![Définir le projet de manière à nommer les éléments interactifs](../test/media/cuit_windowsstoreproeprty_blend_2.png "CUIT_WindowsStoreProeprty_Blend_2")

###  <a name="UniquePropertyWindowsStoreControlsDataTemplate"></a> Utiliser un modèle de données
 Vous pouvez définir un modèle simple à l’aide d’un élément ItemTemplate pour lier les valeurs d’une zone de liste à des variables à l’aide du code XAML suivant.

```xaml
<ListBox Name="listBox1" ItemsSource="{Binding Source={StaticResource employees}}">
   <ListBox.ItemTemplate>
      <DataTemplate>
         <StackPanel Orientation="Horizontal">
            <TextBlock Text="{Binding EmployeeName}" />
            <TextBlock Text="{Binding EmployeeID}" />
         </StackPanel>
      </DataTemplate>
   </ListBox.ItemTemplate>
</ListBox>
```

 Vous pouvez également utiliser un modèle avec ItemContainerStyle pour lier les valeurs à des variables avec le code XAML suivant :

```xaml
      <ListBox Name="listBox1" ItemsSource="{Binding Source={StaticResource employees}}">
            <ListBox.ItemContainerStyle>
                <Style TargetType="ListBoxItem">
                    <Setter Property="Template">
                        <Setter.Value>
                            <ControlTemplate TargetType="ListBoxItem">
                                <Grid>
                                    <Button Content="{Binding EmployeeName}" AutomationProperties.AutomationId="{Binding EmployeeID}"/>
                                </Grid>
                            </ControlTemplate>
                        </Setter.Value>
                    </Setter>
                </Style>
            </ListBox.ItemContainerStyle>
        </ListBox>
```

 Pour ces deux exemples, vous devez remplacer la méthode ToString() de la méthode ItemSource en utilisant l’exemple de code suivant. Ce code vérifie que la valeur pour AutomationProperties.Name est définie et unique, car vous ne pouvez pas définir une propriété Automation unique pour chaque élément de liste lié aux données à l’aide de la liaison. Dans ce cas, la définition d’une valeur unique pour Automation Properties.Name est suffisante.

> [!NOTE]
> Cette approche permet également d’affecter au contenu interne de l’élément de liste une chaîne dans la classe Employee via la liaison. Comme indiqué dans l’exemple, un ID Automation unique (ID d’employé) est affecté au contrôle de bouton situé au sein de chaque élément de la liste.

```csharp
Employee[] employees = new Employee[]
{
   new Employee("john", "4384"),
   new Employee("margaret", "7556"),
   new Employee("richard", "8688"),
   new Employee("george", "1293")
};

listBox1.ItemsSource = employees;

public override string ToString()
{
    return EmployeeName + EmployeeID; // Unique Identification to be set as the AutomationProperties.Name
}
```

###  <a name="UniquePropertyWindowsStoreControlsControlTemplate"></a> Utiliser un modèle de contrôle

Vous pouvez utiliser un modèle de contrôle afin que chaque instance d’un type donné puisse obtenir une propriété Automation unique lorsqu’elle est définie dans le code. Créez le modèle de sorte qu’une liaison soit établie entre AutomationProperty et un ID unique dans l’instance de contrôle. Le code XAML suivant illustre une approche permettant de créer cette liaison avec un modèle de contrôle.

```xaml
<Style x:Key="MyButton" TargetType="Button">
<Setter Property="Template">
   <Setter.Value>
<ControlTemplate TargetType="Button">
   <Grid>
      <CheckBox HorizontalAlignment="Left" AutomationProperties.AutomationId="{TemplateBinding Content}"></CheckBox>
      <Button Width="90" HorizontalAlignment="Right" Content="{TemplateBinding Content}" AutomationProperties.AutomationId="{TemplateBinding Content}"></Button>
   </Grid>
</ControlTemplate>
   </Setter.Value>
</Setter>
</Style>
```

 Quand vous définissez deux instances d’un bouton à l’aide de ce modèle de contrôle, la chaîne de contenu unique est affectée à l’ID Automation pour les contrôles du modèle, comme indiqué dans le code XAML suivant :

```xaml
<Button Content="Button1" Style="{StaticResource MyButton}" Width="140"/>
<Button Content="Button2" Style="{StaticResource MyButton}" Width="140"/>
```

###  <a name="UniquePropertyWindowsStoreControlsDynamicControls"></a> Contrôles dynamiques
 Si vous avez des contrôles qui sont créés de façon dynamique à partir de votre code et qui ne sont pas créés de façon statique ni via des modèles dans des fichiers XAML, vous devez définir les propriétés Content ou Name pour ces contrôles. Cela permet de garantir qu’une propriété Automation unique est affectée à chaque contrôle dynamique. Par exemple, si une case à cocher doit être affichée lorsque vous sélectionnez un élément de liste, définissez ces propriétés comme indiqué ici :

```csharp
private void CreateCheckBox(string txt, StackPanel panel)
   {
      CheckBox cb = new CheckBox();
      cb.Content = txt; // Sets the AutomationProperties.Name
      cb.Height = 50;
      cb.Width = 100;
      cb.Name = "DynamicCheckBoxAid"+ txt; // Sets the AutomationProperties.AutomationId
      panel.Children.Add(cb);
    }
```

## <a name="see-also"></a>Voir aussi

- [Test des applications Windows UWP avec des tests codés de l’interface utilisateur](../test/test-windows-store-8-1-apps-with-coded-ui-tests.md)
