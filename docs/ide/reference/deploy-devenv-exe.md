---
title: -Deploy (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /deploy switch
- deploy Devenv switch
- deploying applications [Visual Studio], after build
- /deploy Devenv switch
ms.assetid: e47c8723-df08-4645-aa2d-0c956e7ccca2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 368680321f8ff8ab908e79e075a5797ba9ecd598
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="deploy-devenvexe"></a>/Deploy (devenv.exe)
Déploie une solution après une génération ou une regénération. S’applique aux projets de code managé uniquement.

## <a name="syntax"></a>Syntaxe

```
devenv SolutionName /deploy SolnConfigName [/project ProjName] [/projectconfig ProjConfigName] [/out LogFileName]
```

## <a name="arguments"></a>Arguments
 `SolnConfigName`

 Obligatoire. Nom de la configuration de solution à utiliser pour générer la solution nommée dans `SolutionName`.

 `SolutionName`

 Obligatoire. Chemin complet et nom du fichier solution.

 /project `ProjName`

 Facultative. Chemin et nom d’un fichier projet dans la solution. Vous pouvez entrer un chemin relatif du dossier `SolutionName` vers le fichier projet, le nom d’affichage du projet ou encore le chemin complet et le nom du fichier projet.

 /projectconfig `ProjConfigName`

 Facultative. Nom d’une configuration de génération de projet à utiliser lors de la génération du `/project` nommé.

## <a name="remarks"></a>Notes
 Le projet spécifié doit être un projet de déploiement. Si ce n’est pas le cas, quand le projet généré est passé en vue de son déploiement, une erreur se produit et le déploiement échoue.

 Placez entre guillemets doubles les chaînes contenant des espaces.

 Vous pouvez afficher des informations récapitulatives sur les builds, y compris sur les erreurs, dans la fenêtre **Commande** ou dans tout fichier journal spécifié avec le commutateur `/out`.

## <a name="example"></a>Exemple
 Cet exemple déploie le projet `CSharpConsoleApp` en utilisant la configuration de build de projet `Release` dans la configuration de solution `Release` de `MySolution`.

```
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /deploy Release /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Release
```

## <a name="see-also"></a>Voir aussi

- [Commutateurs de la ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)