---
title: Windows PowerShell-Formatierungs Dateien | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d4c8f84-ebd2-4405-bb10-cfc5400d4ad6
caps.latest.revision: 6
ms.openlocfilehash: 3ec127d5ff60754de5d7f1ac73f2965524228b9c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365009"
---
# <a name="windows-powershell-formatting-files"></a>Windows PowerShell-Formatierungsdateien

Windows PowerShell bietet mehrere Formatierungs Dateien (. Format. ps1xml), die sich im-Installationsverzeichnis (`$pshome`) befinden. Jede dieser Dateien definiert die Standard Anzeige für einen bestimmten Satz von .NET-Objekten. Diese Dateien sollten nie geändert werden. Sie können Sie jedoch als Referenz verwenden, um eigene benutzerdefinierte Formatierungs Dateien zu erstellen.

`Certificate.Format.ps1xml` definiert die Anzeige von Objekten im Zertifikat Speicher, z. b. x. 509-Zertifikate und Zertifikat Speicher.

`DotNetTypes.Format.ps1xml` definiert die Anzeige verschiedener .NET-Objekte, z. b. CultureInfo-, FileVersionInfo-und EventLogEntry-Objekte.

`FileSystem.Format.ps1xml` definiert die Anzeige von Dateisystemobjekten, wie z. b. Datei-und Verzeichnisobjekte.

`Help.Format.ps1xml` definiert die verschiedenen Sichten, die vom Cmdlet " [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) " verwendet werden, z. b. die detaillierten, vollständigen, Parameter und Beispiel Ansichten.

`PowerShellCore.Format.ps1xml` definiert die Anzeige der von Windows PowerShell Core-Cmdlets generierten Objekte, wie z. b. die von den Cmdlets " [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) " und " [Get-History](/powershell/module/Microsoft.PowerShell.Core/Get-History) " zurückgegebenen Objekte.

`PowerShellTrace.Format.ps1xml` definiert die Anzeige von Ablauf Verfolgungs Objekten, wie z. b. die, die vom [Trace-Command-](/powershell/module/Microsoft.PowerShell.Utility/Trace-Command) Cmdlet generiert werden.

`Registry.Format.ps1xml` definiert die Anzeige von Registrierungs Objekten, wie z. b. Key-und Entry-Objekte.

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Windows PowerShell-Cmdlets](../cmdlet/writing-a-windows-powershell-cmdlet.md)
