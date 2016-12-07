---
title: "Integrierte PowerShell DSC-Ressourcen für Linux"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: 6b001c12885022006003ef3ffe91b7aede07bd17
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="built-in-desired-state-configuration-resources-for-linux"></a>Integrierte PowerShell DSC-Ressourcen für Linux

Ressourcen sind Bausteine zum Schreiben eines PowerShell DSC-Skripts. DSC für Linux bietet verschiedene integrierte Funktionen für das Konfigurieren von Ressourcen wie Dateien und Ordnern, Paketen, Umgebungsvariablen sowie Diensten und Prozessen.

## <a name="built-in-resources"></a>Integrierte Ressourcen 

Die folgende Tabelle bietet eine Liste dieser Ressourcen sowie Links zu Themen, in denen diese Ressourcen ausführlich beschrieben werden.

* [nxArchive Ressource](lnxArchiveResource.md): Bietet einen Mechanismus zum Entpacken von Archivdateien (.tar, .zip) in einem bestimmten Pfad.
* [nxEnvironment Ressource](lnxEnvironmentResource.md): Verwaltet Umgebungsvariablen auf Zielknoten. 
* [nxFile Ressource](lnxFileResource.md): Verwaltet Linux-Dateien und -Verzeichnisse. 
* [nxFileLine Ressource](lnxFileLineResource.md): Verwaltet einzelne Zeilen in einer Linux-Datei. 
* [nxGroup Ressource](lnxGroupResource.md): Verwaltet lokale Linux-Gruppen. 
* [nxPackage Ressource](lnxPackageResource.md): Verwaltet Pakete auf Linux-Knoten.
* [nxScript Ressource ](lnxScriptResource.md): Führt Skripts auf Zielknoten aus.
* [nxService Ressource](lnxServiceResource.md): Verwaltet Linux-Dienste (Daemons).
* [nxSshAuthorizedKeys Ressource](lnxSshAuthorizedKeysResource.md): Verwaltet öffentliche SSH-Schlüssel für einen Linux-Benutzer. 
* [nxUser Ressource](lnxUserResource.md): Verwaltet lokale Linux-Benutzer. 
  
