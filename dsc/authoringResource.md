---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Erstellen von benutzerdefinierten Windows PowerShell DSC-Ressourcen
ms.openlocfilehash: 4751bcaab1996ee3164bd2a2f430c3b188712860
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/17/2018
---
# <a name="build-custom-windows-powershell-desired-state-configuration-resources"></a>Erstellen von benutzerdefinierten Windows PowerShell DSC-Ressourcen

> Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0

Windows PowerShell DSC verfügt über integrierte Ressourcen, mit denen Sie Ihre Umgebung konfigurieren können (Weitere Informationen finden Sie unter [Integrierte Windows PowerShell DSC-Ressourcen](builtInResource.md).) Dieses Thema enthält einen Überblick über die Entwicklung von Ressourcen sowie Links zu Themen mit speziellen Informationen und Beispielen.

## <a name="dsc-resource-components"></a>Komponenten der DSC-Ressourcen

Eine DSC-Ressource ist ein Windows PowerShell-Modul. Das Modul enthält das Schema (die Definition der konfigurierbaren Eigenschaften) und die Implementierung (den Code, der die eigentliche durch eine Konfiguration angegebene Arbeit ausführt) für die Ressource. Ein DSC-Ressourcenschema kann in einer MOF-Datei definiert werden, und die Implementierung erfolgt durch ein Skriptmodul. Beginnend mit der Unterstützung von PowerShell-Klassen in Version 5 können das Schema und die Implementierung in einer Klasse definiert werden. Die folgenden Themen beschreiben ausführlicher, wie Sie DSC-Ressourcen erstellen.

* [Schreiben einer benutzerdefinierten DSC-Ressource mit MOF](authoringResourceMOF.md)
* [Implementieren einer DSC-Ressource in C#](authoringResourceMofCS.md)
* [Schreiben einer benutzerdefinierten DSC-Ressource mit PowerShell-Klassen](authoringResourceClass.md)
* [Zusammengesetzte Ressourcen: Verwenden einer DSC-Konfiguration als Ressource](authoringResourceComposite.md)
* [Verwenden des Ressourcen-Designers](authoringResourceMofDesigner.md)

