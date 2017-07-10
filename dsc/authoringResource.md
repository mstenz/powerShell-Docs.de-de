---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Erstellen von benutzerdefinierten Windows PowerShell DSC-Ressourcen
ms.openlocfilehash: 75b494db4ee6e381491decb11d35b60105217a0f
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
<a id="build-custom-windows-powershell-desired-state-configuration-resources" class="xliff"></a>
# Erstellen von benutzerdefinierten Windows PowerShell DSC-Ressourcen

> Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0

Windows PowerShell DSC verfügt über integrierte Ressourcen, mit denen Sie Ihre Umgebung konfigurieren können (Weitere Informationen finden Sie unter [Integrierte Windows PowerShell DSC-Ressourcen](builtInResource.md).) Dieses Thema enthält einen Überblick über die Entwicklung von Ressourcen sowie Links zu Themen mit speziellen Informationen und Beispielen.

<a id="dsc-resource-components" class="xliff"></a>
## Komponenten der DSC-Ressourcen

Eine DSC-Ressource ist ein Windows PowerShell-Modul. Das Modul enthält das Schema (die Definition der konfigurierbaren Eigenschaften) und die Implementierung (den Code, der die eigentliche durch eine Konfiguration angegebene Arbeit ausführt) für die Ressource. Ein DSC-Ressourcenschema kann in einer MOF-Datei definiert werden, und die Implementierung erfolgt durch ein Skriptmodul. Beginnend mit der Unterstützung von PowerShell-Klassen in Version 5 können das Schema und die Implementierung in einer Klasse definiert werden. Die folgenden Themen beschreiben ausführlicher, wie Sie DSC-Ressourcen erstellen.

* [Schreiben einer benutzerdefinierten DSC-Ressource mit MOF](authoringResourceMOF.md) 
* [Implementieren einer DSC-Ressource in C#](authoringResourceMofCS.md) 
* [Schreiben einer benutzerdefinierten DSC-Ressource mit PowerShell-Klassen](authoringResourceClass.md) 
* [Zusammengesetzte Ressourcen: Verwenden einer DSC-Konfiguration als Ressource](authoringResourceComposite.md) 
* [Verwenden des Ressourcen-Designers](authoringResourceMofDesigner.md) 

