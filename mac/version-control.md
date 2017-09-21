---
title: Gestion de version
description: Utilisation de Git et de Subversion dans Visual Studio pour Mac.
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 49917483-28AA-4598-A847-71F1F2E0DCB5
ms.translationtype: HT
ms.sourcegitcommit: e2b7ff9126e1cc38ac2e58d6be339b656a024e7f
ms.openlocfilehash: a63ebdccc2a7cbde18715291a65ada613dc2c00e
ms.contentlocale: fr-fr
ms.lasthandoff: 08/11/2017

---

# <a name="version-control"></a>Gestion de version

La gestion de version est un système de gestion de fichiers sur plusieurs versions auquel contribuent de nombreux développeurs, notamment dans le cadre du développement de logiciels. L’objectif principal d’un système de gestion de version (_VCS_ (Version Control System) est de trouver une solution qui permet à tous les utilisateurs de travailler sur le codebase en même temps.

Au cœur d’un système de gestion de version se trouve un _dépôt_, qui sert de banque de données centrale pour tous les fichiers, à l’instar d’un serveur de fichiers. Toutefois, contrairement à un serveur de fichiers, le dépôt contient l’historique complet du projet et toutes les révisions qui ont été apportées.

Si le dépôt est la banque de données centrale, il est logique que chaque utilisateur dispose d’une banque locale des données pour pouvoir les modifier. Cela s’appelle une _copie de travail_. Dans Visual Studio pour Mac, votre copie de travail s’affiche comme un répertoire local sur votre ordinateur, ce qui vous permet de lire et écrire n’importe quel fichier. Toutefois, parce que Visual Studio pour Mac intègre un système de gestion de version, vous pouvez tirer parti de la puissance de Subversion et de Git sans quitter l’IDE.

Subversion est un système de gestion de version centralisé. Cela signifie qu’il existe un seul serveur contenant tous les fichiers et révisions, à partir duquel les utilisateurs peuvent extraire n’importe quelle version de n’importe quel fichier. Quand les fichiers sont extraits d’un dépôt Subversion distant, l’utilisateur obtient une capture instantanée du dépôt à ce point dans le temps.

Git est un système de gestion de versions distribué qui permet aux équipes de travailler simultanément sur les mêmes documents. Cela signifie qu’il existe un seul serveur contenant tous les fichiers, mais que quand un dépôt est extrait de cette source centrale, l’intégralité du dépôt est clonée localement sur votre machine.

# <a name="basic-concepts"></a>Concepts de base 

Visual Studio pour Mac prend en charge les systèmes de gestion de version Git et Subversion. Les guides dont les liens sont indiqués ci-dessous explorent la configuration des dépôts Git et Subversion dans Visual Studio pour Mac, ainsi que des fonctionnalités simples comme l’examen, la validation et la transmission des modifications.

* [Configuration d’un dépôt Git](~/set-up-git-repository.md) 
* [Utilisation de Git](~/working-with-git.md)
* [Configuration d’un dépôt Subversion](~/set-up-subversion-repository.md)
* [Utilisation de Subversion](~/working-with-subversion.md)