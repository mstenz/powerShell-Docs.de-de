---
title: Schreiben eines Windows PowerShell-Moduls | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bfbccc5b-2b2b-432a-a971-9f8ab503cdc3
caps.latest.revision: 17
ms.openlocfilehash: 3c6d8e410427d6cfaa1c15db421b3fe935f7d322
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857936"
---
# <a name="writing-a-windows-powershell-module"></a>Schreiben eines Windows PowerShell-Moduls

Dieses Dokument richtet sich an Administratoren, Skriptentwickler und Cmdlet-Entwickler, die zum Verpacken und verteilen ihre Windows PowerShell-Cmdlets müssen. Mit Windows PowerShell-Module, können Sie verpacken und verteilen Ihre Windows PowerShell-Lösungen ohne Verwendung einer kompilierten Sprache.

Windows PowerShell-Module ermöglichen Ihnen die Partition, organisieren und abstrahieren von Ihren Windows PowerShell-Code in eigenständige, wieder verwendbaren Einheiten. Mit diesen wieder verwendbaren Einheiten können Sie ganz einfach Ihre Module direkt für andere Benutzer freigeben. Wenn Sie ein Skriptentwickler sind, können Sie auch von Drittanbietern Module zum Erstellen von benutzerdefinierter Skript basierende Anwendungen erneut verpacken. Module, wie Module, die in anderen Skriptsprachen wie Perl und Python, bietet produktionsbereite skriptlösungen, die wiederverwendbare verteilbare Komponenten mit den zusätzlichen Vorteil, sodass Sie neu zu verpacken und mehrere Komponenten für das abstrakte Erstellen Sie benutzerdefinierte Lösungen.

Auf die grundlegendste Windows PowerShell behandelt alle gültigen Windows PowerShell-Skriptcode, die in einer psm1-Datei als Modul gespeichert. PowerShell behandelt jede Assembly binäre Cmdlet auch automatisch als Modul. Sie können jedoch auch ein Modul (oder genauer gesagt, ein modulmanifest) zum Bündeln einer gesamten Projektmappe verwenden. Die folgenden Szenarien beschreiben typische Verwendungen für Windows PowerShell-Module.

### <a name="libraries"></a>Bibliotheken

Module können verwendet werden, Verpacken und verteilen zusammenhängende Bibliotheken mit Funktionen, die allgemeine Aufgaben ausführen. Im Allgemeinen haben die Namen dieser Funktionen eine oder mehrere Nomen, die die häufige Aufgabe widerspiegeln, der sie verwendet werden. Diese Funktionen können auch wie .NET Framework-Klassen sein, dass sie die öffentlichen und privaten Member besitzen können. Beispielsweise kann eine Bibliothek eine Reihe von Funktionen für die Übertragung von Dateien enthalten. In diesem Fall das Nomen reflektieren die Aufgabe "Datei". möglicherweise

### <a name="configuration"></a>Konfiguration

Module können verwendet werden, um Ihre Umgebung anzupassen, durch das Hinzufügen von bestimmten Cmdlets, Anbieter, Funktionen und Variablen.

### <a name="compiled-code-development-and-distribution"></a>Kompilierter Code-Entwicklung und Verteilung

Cmdlet- und Anbieternamen-Entwickler können die Module verwenden, um zu testen und Verteilen ihrer kompilierten Code ohne-Snap-ins erstellen zu müssen. Sie können die Assembly mit den kompilierten Code als Modul (einem binären Modul) importieren, ohne zum Erstellen und registrieren-Snap-ins.

## <a name="see-also"></a>Weitere Informationen

[Grundlegendes zu einem Windows PowerShell-Modul](./understanding-a-windows-powershell-module.md)

[Gewusst wie: Schreiben ein PowerShell-Skript-Moduls](./how-to-write-a-powershell-script-module.md)

[Gewusst wie: Schreiben ein Moduls für PowerShell-Binärdateien](./how-to-write-a-powershell-binary-module.md)

[Gewusst wie: Schreiben Sie ein PowerShell-Modulmanifest](http://msdn.microsoft.com/en-us/abe4c24b-e64e-4a61-81d5-18c4fceba0b6)

[Ändern den PSModulePath-Installationspfad](./modifying-the-psmodulepath-installation-path.md)

[Importieren eines PowerShell-Moduls](./importing-a-powershell-module.md)

[Installieren eines PowerShell-Moduls](./installing-a-powershell-module.md)
