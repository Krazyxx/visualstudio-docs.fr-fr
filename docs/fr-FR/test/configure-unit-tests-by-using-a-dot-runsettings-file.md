---
title: Configurer des tests unitaires dans Visual Studio à l’aide d’un fichier .runsettings
ms.date: 02/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 97d270704196b3656f89d0177f615826dcbef2af
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="configure-unit-tests-by-using-a-runsettings-file"></a>Configurer des tests unitaires à l’aide d’un fichier *.runsettings*

Les tests unitaires dans Visual Studio peuvent être configurés à l’aide d’un fichier *.runsettings*. Par exemple, vous pouvez changer la version du .NET Framework sur laquelle les tests sont exécutés, le répertoire des résultats des tests ou les données collectées pendant une série de tests.

> [!NOTE]
> Le nom du fichier n’a pas d’importance, à condition d’utiliser l’extension « .runsettings ».

Si vous n’avez pas besoin d’une configuration spéciale, un fichier *.runsettings* n’est pas nécessaire. L’utilisation la plus courante d’un fichier *.runsettings* est de personnaliser [l’analyse de la couverture du code](../test/customizing-code-coverage-analysis.md).

## <a name="customize-tests"></a>Personnaliser des tests

1. Ajoutez un fichier XML à votre solution Visual Studio et renommez-le *test.runsettings*.

1. Remplacez le contenu du fichier par le code XML de l’exemple qui suit, puis personnalisez-le selon vos besoins.

1. Dans le menu **Test**, choisissez **Paramètres de test** > **Sélectionner le fichier de paramètres des tests**.

Vous pouvez créer plusieurs fichiers *.runsettings* dans votre solution, et les activer ou les désactiver à différents moments via le menu **Paramètres de test**.

![Activation d’un fichier de paramètres d’exécution](../test/media/runsettings-1.png)

## <a name="example-runsettings-file"></a>Exemple de fichier *.runsettings*

Voici un fichier *.runsettings* classique. Chaque élément du fichier est facultatif, car chaque valeur est définie par défaut.

```xml
<?xml version="1.0" encoding="utf-8"?>
<RunSettings>
  <!-- Configurations that affect the Test Framework -->
  <RunConfiguration>
    <MaxCpuCount>1</MaxCpuCount>
    <!-- Path relative to solution directory -->
    <ResultsDirectory>.\TestResults</ResultsDirectory>

    <!-- x86 or x64
      - You can also change it from menu Test, Test Settings, Default Processor Architecture -->
    <TargetPlatform>x86</TargetPlatform>

    <!-- Framework35 | [Framework40] | Framework45 -->
    <TargetFrameworkVersion>Framework40</TargetFrameworkVersion>

    <!-- Path to Test Adapters -->
    <TestAdaptersPaths>%SystemDrive%\Temp\foo;%SystemDrive%\Temp\bar</TestAdaptersPaths>

     <!--TestSessionTimeout is only available with Visual Studio 2017 version 15.5 and higher -->
     <!-- Specify timeout in milliseconds. A valid value should be greater than 0 -->
     <TestSessionTimeout>10000</TestSessionTimeout>
  </RunConfiguration>

  <!-- Configurations for data collectors -->
  <DataCollectionRunSettings>
    <DataCollectors>
      <DataCollector friendlyName="Code Coverage" uri="datacollector://Microsoft/CodeCoverage/2.0" assemblyQualifiedName="Microsoft.VisualStudio.Coverage.DynamicCoverageDataCollector, Microsoft.VisualStudio.TraceCollector, Version=11.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a">
        <Configuration>
          <CodeCoverage>
            <ModulePaths>
              <Exclude>
                <ModulePath>.*CPPUnitTestFramework.*</ModulePath>
              </Exclude>
            </ModulePaths>

            <!-- We recommend you do not change the following values: -->
            <UseVerifiableInstrumentation>True</UseVerifiableInstrumentation>
            <AllowLowIntegrityProcesses>True</AllowLowIntegrityProcesses>
            <CollectFromChildProcesses>True</CollectFromChildProcesses>
            <CollectAspDotNet>False</CollectAspDotNet>

          </CodeCoverage>
        </Configuration>
      </DataCollector>

      <!--Video data collector is only available with Visual Studio 2017 version 15.5 and higher -->
      <DataCollector uri="datacollector://microsoft/VideoRecorder/1.0" assemblyQualifiedName="Microsoft.VisualStudio.TestTools.DataCollection.VideoRecorder.VideoRecorderDataCollector, Microsoft.VisualStudio.TestTools.DataCollection.VideoRecorder, Version=15.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" friendlyName="Screen and Voice Recorder">
      </DataCollector>

    </DataCollectors>
  </DataCollectionRunSettings>

  <!-- Parameters used by tests at runtime -->
  <TestRunParameters>
    <Parameter name="webAppUrl" value="http://localhost" />
    <Parameter name="webAppUserName" value="Admin" />
    <Parameter name="webAppPassword" value="Password" />
  </TestRunParameters>

  <!-- Adapter Specific sections -->

  <!-- MSTest adapter -->
  <MSTest>
    <MapInconclusiveToFailed>True</MapInconclusiveToFailed>
    <CaptureTraceOutput>false</CaptureTraceOutput>
    <DeleteDeploymentDirectoryAfterTestRunIsComplete>False</DeleteDeploymentDirectoryAfterTestRunIsComplete>
    <DeploymentEnabled>False</DeploymentEnabled>
    <AssemblyResolution>
      <Directory Path="D:\myfolder\bin\" includeSubDirectories="false"/>
    </AssemblyResolution>
  </MSTest>

</RunSettings>
```

Le fichier *.runsettings* est également utilisé pour configurer [l’analyse de la couverture du code](../test/customizing-code-coverage-analysis.md).

Le reste de cet article décrit le contenu du fichier.

## <a name="edit-your-runsettings-file"></a>Modifier votre fichier *.runsettings*

Les sections qui suivent détaillent les éléments d’un fichier *.runsettings*.

### <a name="test-run-configuration"></a>Configuration de série de tests

|Nœud|Par défaut|Valeurs|
|----------|-------------|------------|
|`ResultsDirectory`||Répertoire où les résultats des tests sont placés.|
|`TargetFrameworkVersion`|Framework40|Framework35, Framework40, Framework45<br /><br /> Ce paramètre spécifie la version du framework de tests unitaires qui est utilisée pour découvrir et exécuter les tests. Elle peut être différente de la version de la plateforme .NET. que vous spécifiez dans les propriétés de génération du projet de test unitaire.|
|`TargetPlatform`|x86|x86, x64|
|`TreatTestAdapterErrorsAsWarnings`|False|false, true|
|`TestAdaptersPaths`||Un ou plusieurs chemins au répertoire où se trouvent les TestAdapters|
|`MaxCpuCount`|1|Ce paramètre permet de contrôler le degré d’exécution de tests parallèles lors des tests unitaires, en utilisant les cœurs disponibles sur la machine. Le moteur d’exécution des tests démarre en tant que processus distinct sur chaque cœur disponible et donne à chaque cœur un conteneur de tests à exécuter. Un conteneur peut être un assembly, une DLL ou un artefact approprié. Le conteneur de test est l’unité de planification. Dans chaque conteneur, les tests sont exécutés en fonction du framework de test configuré. S’il y a beaucoup de conteneurs, chaque processus reçoit le conteneur disponible suivant dès qu’il a terminé l’exécution des tests d’un conteneur.<br /><br /> Valeur possible pour MaxCpuCount :<br /><br /> n, où 1 < = n < = nombre de cœurs : jusqu’à n processus peuvent être lancés.<br /><br /> n, où n = toute autre valeur : le nombre de processus lancés dépend du nombre de cœurs disponibles sur la machine.|
|`TestSessionTimeout`||Permet aux utilisateurs de mettre fin à une session de test lorsque celle-ci dépasse le délai spécifié. La définition d’un délai d’expiration garantit que les ressources sont consommées et que les sessions de test sont limitées à une durée spécifique. Le paramètre est disponible dans **Visual Studio 2017 versions 15.5** et ultérieures.

### <a name="diagnostic-data-adapters-data-collectors"></a>Diagnostic des adaptateurs de données (collecteurs de données)

L’élément `DataCollectors` spécifie les paramètres des adaptateurs de données de diagnostic. Les adaptateurs de données de diagnostic rassemblent des informations supplémentaires sur l’environnement et sur l’application testée. Chaque adaptateur a des paramètres par défaut. Il vous suffit de fournir des paramètres si vous ne souhaitez pas utiliser les valeurs par défaut.

#### <a name="code-coverage-adapter"></a>Adaptateur de couverture du code

Le collecteur de données de couverture du code crée un journal des parties du code d’application qui ont été testées. Pour plus d’informations sur la personnalisation des paramètres pour la couverture du code, consultez [Personnalisation de l’analyse de la couverture du code](../test/customizing-code-coverage-analysis.md).

#### <a name="video-data-collector"></a>Collecteur de données vidéo

Le collecteur de données vidéo capture un enregistrement de l’écran quand des tests sont exécutés. Cet enregistrement est utile pour résoudre les problèmes des tests d’interface utilisateur. Le collecteur de données vidéo est disponible dans **Visual Studio 2017 versions 15.5** et ultérieures.

Pour personnaliser un autre type d’adaptateur de données de diagnostic, vous devez utiliser un [fichier de paramètres de test](../test/collect-diagnostic-information-using-test-settings.md).

### <a name="testrunparameters"></a>TestRunParameters

TestRunParameters fournit un moyen de définir des variables et des valeurs qui sont disponibles pour les tests au moment de l’exécution. Ces variables sont accessibles via l’objet [TestContext](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testcontext(v=vs.140).aspx).

```csharp
[TestMethod]
public void HomePageTest()
{
    string appURL = TestContext.Properties["webAppUrl"];
```

Pour utiliser TestContext, ajoutez un champ [TestContext](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testcontext(v=vs.140).aspx) privé et une propriété `TestContext` publique à votre classe de test.

### <a name="mstest-run-settings"></a>Paramètres d’exécution MSTest

Ces paramètres sont spécifiques à l’adaptateur de test qui exécute les méthodes de test disposant de l’attribut `[TestMethod]` .

|Configuration|Par défaut|Valeurs|
|-------------------|-------------|------------|
|ForcedLegacyMode|False|Dans Visual Studio 2012, l’adaptateur MSTest a été optimisé afin d’être plus rapide et plus scalable. Un comportement, tel que l’ordre dans lequel les tests sont exécutés, peut ne pas être exactement identique à celui d’éditions précédentes de Visual Studio. Attribuez la valeur `true` pour utiliser l’adaptateur de test le plus ancien.<br /><br /> Par exemple, vous pouvez utiliser ce paramètre si un fichier *app.config* est spécifié pour un test unitaire.<br /><br /> Il est recommandé d’envisager de refactoriser vos tests pour vous permettre d’utiliser le nouvel adaptateur.|
|IgnoreTestImpact|False|La fonctionnalité d’impact de test classe par priorité les tests affectés par des modifications récentes, lorsqu’ils sont exécutés dans MSTest ou à partir de Microsoft Test Manager. Ce paramètre désactive la fonctionnalité. Pour plus d’informations, consultez [Guide pratique pour collecter des données et vérifier les tests à exécuter après des modifications du code](http://msdn.microsoft.com/Library/2f921ea1-9bb0-4870-a30f-0521fc22cb47).|
|SettingsFile||Vous pouvez spécifier un fichier de paramètres de test à utiliser avec l’adaptateur MSTest ici. Vous pouvez également spécifier un fichier de paramètres de test via le menu **Test**, **Paramètres de test**, **Sélectionner le fichier de paramètres des tests**.<br /><br /> Si vous spécifiez cette valeur, vous devez également affecter à **ForcedlegacyMode** la valeur **true**.<br /><br /> `<RunSettings>   <MSTest>     <SettingsFile>my.testsettings</SettingsFile>      <ForcedLegacyMode>true</ForcedLegacyMode>    </MSTest> </RunSettings>`|
|KeepExecutorAliveAfterLegacyRun|False|Une fois qu’une série de tests est terminée, MSTest est arrêté. Tout processus qui est lancé dans le cadre du test est également terminé. Si vous souhaitez conserver l’exécuteur de test actif, définissez cette configuration sur true.<br /><br /> Par exemple, vous pouvez utiliser ce paramètre pour que le navigateur continue à s’exécuter entre des tests codés de l’interface utilisateur.|
|DeploymentEnabled|true|Si vous définissez cette valeur sur false, les éléments de déploiement que vous avez spécifiés dans votre méthode de test ne sont pas copiés dans le répertoire de déploiement.|
|CaptureTraceOutput|true|Vous pouvez écrire dans la trace du débogage à partir de votre méthode de test en utilisant Trace.WriteLine. Cette configuration vous permet de désactiver ces traces de débogage.|
|DeleteDeploymentDirectoryAfterTestRunIsComplete|true|Vous pouvez conserver le répertoire de déploiement après une série de tests en définissant cette valeur sur false.|
|MapInconclusiveToFailed|False|Si un test retourne un état Non concluant, il est généralement mappé à l’état Ignoré dans l’Explorateur de tests. Si vous voulez que les tests non concluants s’affichent comme ayant échoué, utilisez cette configuration.|
|InProcMode|False|Si vous souhaitez que vos tests soient exécutés dans le même processus que l’adaptateur de test Microsoft, définissez cette valeur sur True. Ce paramètre offre un gain de performances mineur. Mais si un test s’arrête à cause d’une exception, les autres tests s’arrêteront également.|
|AssemblyResolution|False|Vous pouvez spécifier des chemins d’assemblys supplémentaires pour la recherche et l’exécution des tests unitaires. Par exemple, utilisez ces chemins pour les assemblys de dépendance qui ne se trouvent pas dans le même répertoire que l’assembly de test. Pour spécifier un chemin, utilisez un élément « Directory Path ». Les chemins peuvent contenir des variables d’environnement.<br /><br /> `<AssemblyResolution>  <Directory Path="D:\myfolder\bin\" includeSubDirectories="false"/> </AssemblyResolution>`|

## <a name="see-also"></a>Voir aussi

- [Personnalisation de l’analyse de la couverture du code](../test/customizing-code-coverage-analysis.md)