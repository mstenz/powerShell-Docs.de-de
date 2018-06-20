---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC-Ressourcen
ms.openlocfilehash: 27e16c39699bb96b2829744b5700f75f59f8802f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219809"
---
# <a name="dsc-resources"></a>DSC-Ressourcen

>Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0

DSC-Ressourcen sind die Bausteine einer DSC-Konfiguration. Eine Ressource macht Eigenschaften verfügbar, die konfiguriert werden können (Schema), und enthält die PowerShell-Skriptfunktionen, die der lokale Konfigurations-Manager wie gewünscht ausführt.

Mit einer Ressource kann etwas Allgemeines wie eine Datei oder Spezifisches wie eine IIS-Servereinstellung modelliert werden.  Gruppen ähnlicher Ressourcen werden in einem DSC-Modul kombiniert, das alle erforderlichen Dateien in einer Struktur organisiert, die portierbar ist und Metadaten zum Bestimmen des Zwecks der Ressourcen enthält.

In den folgenden Themen werden DSC-Ressourcen beschrieben:

- [Integrierte DSC-Ressourcen](builtInResource.md)
- [Erstellen benutzerdefinierter DSC-Ressourcen](authoringResource.md)
- [Integrierte DSC-Ressourcen für Linux](lnxBuiltInResources.md)