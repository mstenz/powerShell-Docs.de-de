---
title: Erstellen von benutzerdefinierten Windows PowerShell DSC-Ressourcen
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: fe2697de322be99e9b5dfe79090fda4082a73623
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="build-custom-windows-powershell-desired-state-configuration-resources"></a>Erstellen von benutzerdefinierten Windows PowerShell DSC-Ressourcen

> Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0

Windows PowerShell DSC verfügt über integrierte Ressourcen, mit denen Sie Ihre Umgebung konfigurieren können (Weitere Informationen finden Sie unter [Integrierte Windows PowerShell DSC-Ressourcen](builtInResource.md).) Dieses Thema enthält einen Überblick über die Entwicklung von Ressourcen sowie Links zu Themen mit speziellen Informationen und Beispielen.

## <a name="dsc-resource-components"></a>Komponenten der DSC-Ressourcen

Eine DSC-Ressource ist ein Windows PowerShell-Modul. Das Modul enthält das Schema (die Definition der konfigurierbaren Eigenschaften) und die Implementierung (den Code, der die eigentliche durch eine Konfiguration angegebene Arbeit ausführt) für die Ressource. Ein DSC-Ressourcenschema kann in einer MOF-Datei definiert werden, und die Implementierung erfolgt durch ein Skriptmodul. Beginnend mit der Unterstützung von PowerShell-Klassen in Version 5 können das Schema und die Implementierung in einer Klasse definiert werden. Die folgenden Themen beschreiben ausführlicher, wie Sie DSC-Ressourcen erstellen.

* [Schreiben einer benutzerdefinierten DSC-Ressource mit MOF](authoringResourceMOF.md) 
* [Implementieren einer DSC-Ressource in C#](authoringResourceMofCS.md) 
* [Schreiben einer benutzerdefinierten DSC-Ressource mit PowerShell-Klassen](authoringResourceClass.md) 
* [Zusammengesetzte Ressourcen: Verwenden einer DSC-Konfiguration als Ressource](authoringResourceComposite.md) 
* [Verwenden des Ressourcen-Designers](authoringResourceMofDesigner.md) 

