---
title: Avertissements VSInstr | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- instrumentation, VSInstr tool
- warnings
- VSInstr tool
- warnings, VSInstr tool
- performance tools, VSInstr tool
ms.assetid: 47512bc9-a8e9-4628-883a-d9888edab786
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 60ea2bcf1770e8c20db61c93a2b4ed6516b0daff
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="vsinstr-warnings"></a>Avertissements VSInstr
Le tableau suivant répertorie les avertissements émis par l’outil VSInstr.exe. Vous pouvez utiliser l’option NOWARN avec les numéros d’avertissement pour empêcher l’affichage de l’avertissement.  
  
|Numéro d’avertissement|Description|  
|--------------------|-----------------|  
|**VSP2000**|Erreur interne. Impossible d’obtenir le nom de fichier du module de cet exécutable.|  
|**VSP2001**|\<nom_assembly> est un assembly à nom fort. Vous devrez le resigner avant de l’exécuter.<br /><br /> Cet avertissement se produit quand un assembly signé est instrumenté. Vous pouvez utiliser l’outil sn.exe pour resigner le fichier binaire ou désactiver temporairement la spécification de nom fort. Pour plus d’informations, consultez [Sn.exe (Strong Name Tool)](/dotnet/framework/tools/sn-exe-strong-name-tool).|  
|**VSP2002**|Impossible de trouver la fonction \<nom_fonction> dans le fichier \<nom_fichier><br /><br /> Cet avertissement se produit si une fonction est introuvable dans le fichier spécifié.|  
|**VSP2003**|Impossible de trouver des sauts croisés vers la fonction \<nom_fonction> dans le fichier \<nom_fichier>.<br /><br /> Cet avertissement se produit si VSInstr ne peut pas annuler les sauts croisés. Les sauts croisés sont utilisés pour optimiser le code.|  
|**VSP2004**|La fonction \<nom_fonction> a été exclue à l’aide du commutateur de ligne de commande EXCLUDE mais était requise parce qu’elle contenait un saut croisé.<br /><br /> Cet avertissement se produit quand une fonction exigée pendant le processus d’instrumentation est exclue à l’aide de l’option EXCLUDE. Le profileur inclut automatiquement la fonction exigée.|  
|**VSP2005**|Erreur d’instrumentation interne \<texte_erreur><br /><br /> Cet avertissement est émis si l’instrumentation ne peut pas être exécutée. Passez en revue le texte d’erreur pour déterminer si l’erreur peut être corrigée.|  
|**VSP2006**|Impossible de trouver le fichier PDB de \<nom><br /><br /> Cet avertissement se produit si le fichier PDB n’existe pas dans le chemin de recherche ou ne correspond pas au binaire.|  
|**VSP2007**|\<nom_fichier> ne contient aucun code instrumentable.<br /><br /> Cet avertissement est émis si les fonctions du fichier binaire ont été toutes exclues ou si le fichier spécifié ne contient que des ressources.|  
|**VSP2008**|Impossible d’obtenir les attributs de sécurité de \<nom>. Code d’erreur \<code><br /><br /> Cet avertissement se produit si l’utilisateur n’a pas l’autorisation READ_DAC. Durant le processus d’instrumentation, le profileur tente de conserver la liste DACL d’origine du binaire. Étant donné que le binaire d’origine est remplacé par un nouveau binaire, la liste DACL du binaire d’origine doit être copiée et appliquée au nouveau binaire. Cette opération peut échouer si l’utilisateur n’a pas l’accès READ_DAC sur le binaire d’origine.|  
|**VSP2009**|Impossible de définir les attributs de sécurité dans \<nom>. Code d’erreur \<numéro_erreur><br /><br /> Cet avertissement se produit si l’utilisateur n’a pas l’autorisation WRITE_DAC. Durant le processus d’instrumentation, le profileur tente de conserver la liste DACL d’origine du binaire. Étant donné que le binaire d’origine est remplacé par un nouveau binaire, la liste DACL du binaire d’origine doit être copiée et appliquée au nouveau binaire. Cette opération peut échouer si l’utilisateur n’a pas l’accès WRITE_DAC sur le nouveau binaire.|  
|**VSP2010**|Aucune fonction n’a été sélectionnée pour l’instrumentation en raison des options /INCLUDE ou /EXCLUDE|  
|**VSP2011**|La fonction funcspec Include/Exclude \<nom> ne correspond à aucune fonction|  
|**VSP2012**|L’image ne renferme aucun code susceptible d’être instrumenté pour une couverture du code.<br /><br /> Le profileur n’instrumente pas le type de code suivant :<br /><br /> -   Fonctions CRT statiques<br />-   Méthodes managées attribuées avec NonUserCodeAttribute<br />-   Méthodes managées attribuées avec DebuggerHiddenAttribute<br />-   Blocs MASM<br /><br /> Cet avertissement est généré si, après ce filtrage, il ne reste aucun code.|  
|**VSP2013**|Vous devez exécuter cette image en tant que processus 32 bits pour pouvoir l’instrumenter. Les indicateurs dans l’en-tête CLR ont été mis à jour pour en tenir compte.<br /><br /> Le profileur modifie le binaire pour que les systèmes d’exploitation 64 bits puissent ouvrir le processus 32 bits dans l’émulateur WOW64. Pour les bibliothèques (DLL), cette opération peut échouer en cas de chargement dans un processus 64 bits existant. Cet avertissement notifie l’utilisateur de la dépendance.|  
|**VSP2014**|L’image instrumentée obtenue ne semble pas valide et risque de ne pas s’exécuter.<br /><br /> Ce message se produit quand l’assembly instrumenté final a un en-tête PE non valide.|  
  
## <a name="see-also"></a>Voir aussi  
 [VSInstr](../profiling/vsinstr.md)