---
title: -Edit (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /edit switch
- /Edit Devenv swtich
ms.assetid: 02b3d6e7-a2b1-4d83-a747-aa8c2fb758b7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c071d225ebd2ac5032da3b5aed095bef6cafe352
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="edit-devenvexe"></a>/Edit (devenv.exe)
Ouvre le fichier spécifié dans une instance existante de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="syntax"></a>Syntaxe

```
Devenv /edit [file1[ file2]]
```

## <a name="arguments"></a>Arguments
 `file1`

 Facultative. Fichier à ouvrir dans une instance existante de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Si aucune instance de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] n’existe, une instance est créée avec une disposition de fenêtre simplifiée et `file1` est ouvert dans la nouvelle instance.

 `file2`

 Facultative. Un ou plusieurs fichiers supplémentaires à ouvrir dans l’instance existante de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="remarks"></a>Notes
 Si aucun fichier n’est spécifié et qu’il existe une instance de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], l’instance existante de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] reçoit le focus. Si aucun fichier n’est spécifié et qu’il n’y a aucune instance existante de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], une instance de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] est créée avec une disposition de fenêtre simplifiée.

 Si l’instance existante de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] est dans un état modal, par exemple si la [boîte de dialogue Options](../../ide/reference/options-dialog-box-visual-studio.md) est ouverte, le fichier s’ouvre dans l’instance existante quand [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] quitte l’état modal.

## <a name="example"></a>Exemple
 Cet exemple ouvre le fichier `MyFile.cs` dans une instance existante de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ou dans une nouvelle instance de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] s’il n’en existe pas déjà une.

```
devenv /edit MyFile.cs
```

## <a name="see-also"></a>Voir aussi

- [Commutateurs de la ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)