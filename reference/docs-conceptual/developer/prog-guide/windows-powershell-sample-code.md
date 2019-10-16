---
title: Windows PowerShell-Beispiel Code | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1106829a-8ddc-454e-bbdd-ade15d4bffb4
caps.latest.revision: 7
ms.openlocfilehash: e9df44b17453e9f73f6eb388d9cbc8a69fce4ba2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366419"
---
# <a name="windows-powershell-sample-code"></a>Windows PowerShell-Beispielcode

Windows PowerShell-® Beispiele sind über die Windows SDK verfügbar. Dieser Abschnitt enthält den Beispielcode, der in den Windows SDK Beispielen enthalten ist.

> [!NOTE]
> Wenn die Windows SDK installiert ist, wird ein **Samples** -Verzeichnis erstellt, in dem alle Windows PowerShell-Beispiele zur Verfügung gestellt werden. Ein typisches Installationsverzeichnis ist **c:\Programme\Microsoft SDKs\Windows\v6.0**.
> Starten Sie Windows PowerShell, und geben Sie **"CD samples\sysmgmt\powershell"** ein, um das Windows PowerShell Samples-Verzeichnis zu suchen. In diesem Dokument wird das Windows PowerShell-Beispiel Verzeichnis als **\<powershell-Beispiele >** bezeichnet.

## <a name="sample-code-listing"></a>Beispiel Code Auflistung

|Beispiel Code|Description|
|-----------------|-----------------|
|[AccessDbProviderSample01-Code Beispiel](./accessdbprovidersample01-code-sample.md)|Dies ist der unter [Erstellen eines einfachen Windows PowerShell-Anbieters](./creating-a-basic-windows-powershell-provider.md)beschriebene Anbieter.|
|[AccessDbProviderSample02-Code Beispiel](./accessdbprovidersample02-code-sample.md)|Dies ist der Anbieter, der unter [Erstellen eines Windows PowerShell-Laufwerks Anbieters](./creating-a-windows-powershell-drive-provider.md)beschrieben wird.|
|[AccessDbProviderSample03-Code Beispiel](./accessdbprovidersample03-code-sample.md)|Dies ist der unter [Erstellen eines Windows PowerShell-Element Anbieters](./creating-a-windows-powershell-item-provider.md)beschriebene Anbieter.|
|[AccessDbProviderSample04-Code Beispiel](./accessdbprovidersample04-code-sample.md)|Dies ist der Anbieter, der unter [Erstellen eines Windows PowerShell-Container Anbieters](./creating-a-windows-powershell-container-provider.md)beschrieben wird.|
|[AccessDbProviderSample05-Code Beispiel](./accessdbprovidersample05-code-sample.md)|Dies ist der unter [Erstellen eines Windows PowerShell-navigationsanbieters](./creating-a-windows-powershell-navigation-provider.md)beschriebene Anbieter.|
|[AccessDbProviderSample06-Code Beispiel](./accessdbprovidersample06-code-sample.md)|Dies ist der unter [Erstellen eines Windows PowerShell-Inhalts Anbieters](./creating-a-windows-powershell-content-provider.md)beschriebene Anbieter.|
|[GetProc01-Code Beispiele](./getproc01-code-samples.md)|Dies ist das grundlegende `Get-Process`-Cmdlet-Beispiel, das unter [Erstellen des ersten Cmdlets](../cmdlet/creating-a-cmdlet-without-parameters.md)beschrieben wird.|
|[GetProc02-Code Beispiele](./getproc02-code-samples.md)|Dies ist das `Get-Process`-Cmdlet-Beispiel [, das unter Hinzufügen von Parametern zur Verarbeitung der Befehlszeilen Eingabe](../cmdlet/adding-parameters-that-process-command-line-input.md)beschrieben wird.|
|[GetProc03-Code Beispiele](./getproc03-code-samples.md)|Dies ist das `Get-Process`-Cmdlet-Beispiel [, das unter Hinzufügen von Parametern zum Verarbeiten von Pipeline Eingaben](../cmdlet/adding-parameters-that-process-pipeline-input.md)beschrieben wird|
|[GetProc04-Code Beispiele](./getproc04-code-samples.md)|Dies ist das `Get-Process`-Cmdlet-Beispiel [, das unter Hinzufügen von Fehlern bei der nicht abschließenden Fehlerberichterstattung zum Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md)beschrieben wird.|
|[GetProc05-Code Beispiele](./getproc05-code-samples.md)|Dieses Cmdlet "`Get-Process`" ähnelt dem Cmdlet, das unter [Hinzufügen von Fehlerberichten ohne Abbruch zum Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md)beschrieben wird.|
|[StopProc01-Code Beispiele](./stopproc01-code-samples.md)|Dies ist das `Stop-Process`-Cmdlet-Beispiel [, das unter Erstellen eines Cmdlets beschrieben wird, das das System ändert](../cmdlet/creating-a-cmdlet-that-modifies-the-system.md).|
|[StopProcessSample04-Code Beispiele](./stopprocesssample04-code-samples.md)|Dies ist das `Stop-Process`-Cmdlet-Beispiel [, das unter Hinzufügen von Parameter Sätzen zu einem Cmdlet](../cmdlet/adding-parameter-sets-to-a-cmdlet.md)beschrieben wird.|
|[Runspace01-Code Beispiele](./runspace01-code-samples.md)|Dies sind die Codebeispiele für den Runspace, der unter [Erstellen einer Konsolenanwendung beschrieben wird, die einen angegebenen Befehl ausführt](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program).|
|[Runspace02-Code Beispiele](./runspace02-code-samples.md)|In diesem Beispiel wird die [System. Management. Automation. runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) -Klasse verwendet, um das `Get-Process`-Cmdlet synchron auszuführen.|
|[RunSpace03-Code Beispiele](./runspace03-code-samples.md)|Dies sind die Codebeispiele für den Runspace, der unter "Erstellen einer Konsolenanwendung, die ein bestimmtes Skript ausführt" beschrieben wird.|
|[RunSpace04-Code Beispiele](./runspace04-code-samples.md)|Dies ist ein Codebeispiel für einen Runspace, der die [System. Management. Automation. runspacinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) -Klasse verwendet, um ein Skript auszuführen, das einen Abbruch Fehler generiert.|
|[RunSpace05-Code Beispiel](./runspace05-code-sample.md)|Dies ist der Quellcode für das Runspace05-Beispiel, das unter [Konfigurieren eines Runspace mithilfe von runspaceconfiguration](https://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2)beschrieben wird.|
|[RunSpace06-Code Beispiel](./runspace06-code-sample.md)|Dies ist der Quellcode für das Runspace06-Beispiel, das unter [Konfigurieren eines Runspace mithilfe eines Windows PowerShell-Snap-Ins](https://msdn.microsoft.com/en-us/a7289ee8-9732-49ee-91c7-d533e9538b83)beschrieben wird.|
|[RunSpace07-Code Beispiel](./runspace07-code-sample.md)|Dies ist der Quellcode für das Runspace07-Beispiel [, das unter Erstellen einer Konsolenanwendung beschrieben wird, mit der Befehle zu einer Pipeline hinzugefügt](https://msdn.microsoft.com/en-us/01eb7808-e97b-4905-80be-9e2fa38c262e)werden.|
|[RunSpace08-Code Beispiel](./runspace08-code-sample.md)|Dies ist der Quellcode für das Runspace08-Beispiel [, das unter Erstellen einer Konsolenanwendung beschrieben wird, mit der einem Befehl Parameter hinzugefügt](https://msdn.microsoft.com/en-us/848b2b46-60f1-4a86-b448-cfc7c0cccfba)werden.|
|[RunSpace09-Code Beispiel](./runspace09-code-sample.md)|Dies ist der Quellcode für das Runspace09-Beispiel [, das unter Erstellen einer Konsolenanwendung beschrieben wird, die asynchron eine Pipeline](https://msdn.microsoft.com/en-us/198c1c94-2a06-457e-93ce-c0d910618e47)aufruft.|
|[RunSpace10-Code Beispiel](./runspace10-code-sample.md)|Dies ist der Quellcode für das Runspace10-Beispiel, mit dem der [System. Management. Automation. Runspaces. runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) ein Cmdlet hinzugefügt und dann die geänderten Konfigurationsinformationen verwendet werden, um den Runspace zu erstellen.|

## <a name="see-also"></a>Weitere Informationen

[Windows PowerShell-Programmier Handbuch](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)