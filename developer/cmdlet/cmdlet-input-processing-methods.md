---
title: -Cmdlet Eingabeverarbeitungsmethoden | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- virtual methods (PowerShell SDK]
ms.assetid: b0bb8172-c9fa-454b-9f1b-57c3fe60671b
caps.latest.revision: 12
ms.openlocfilehash: a28c8d3df19bc72bf338d6abc4e02768c5097209
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068486"
---
# <a name="cmdlet-input-processing-methods"></a>Cmdlet-Eingabeverarbeitungsmethoden

Cmdlets muss es sich um eine oder mehrere der in diesem Thema für ihre Arbeit beschriebenen eingabeverarbeitungsmethoden überschreiben.
Diese Methoden ermöglichen das-Cmdlet zum Ausführen von Vorgängen der vorverarbeitung, Eingabeverarbeitung und nach der Verarbeitung.
Diese Methoden ermöglichen auch das Cmdlet-Verarbeitung zu beenden.
Ein ausführlicheres Beispiel zur Verwendung dieser Methoden finden Sie unter [SelectStr Tutorial](selectstr-tutorial.md).

## <a name="pre-processing-operations"></a>Vorab verarbeitete Vorgänge

Cmdlets sollten außer Kraft setzen der [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) Methode, um alle vorverarbeitungsoperationen hinzuzufügen, die für alle Datensätze gültig sind, die später vom Cmdlet verarbeitet werden.
Wenn PowerShell über eine Befehlspipeline verarbeitet, ruft PowerShell diese Methode einmal für jede Instanz des-Cmdlets in der Pipeline.
Weitere Informationen dazu, wie PowerShell die Befehlspipeline aufruft, finden Sie unter [Cmdlet Verarbeitung Lebenszyklus](/previous-versions/ms714429(v=vs.85)).

Der folgende Code zeigt eine Implementierung der BeginProcessing-Methode.

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the BeginProcessing template.");
}
```

## <a name="input-processing-operations"></a>Geben Sie die Verarbeitung von Vorgängen

Cmdlets können außer Kraft setzen der [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) Methode, um die Eingabe zu verarbeiten, die an das-Cmdlet gesendet wird.
Wenn PowerShell über eine Befehlspipeline verarbeitet, ruft PowerShell diese Methode für jeden Eingabedatensatz, die vom Cmdlet verarbeitet wird.
Weitere Informationen dazu, wie PowerShell die Befehlspipeline aufruft, finden Sie unter [Cmdlet Verarbeitung Lebenszyklus](/previous-versions/ms714429(v=vs.85)).

Der folgende Code zeigt eine Implementierung der ProcessRecord-Methode.

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the ProcessRecord template.");
}
```

## <a name="post-processing-operations"></a>Nachträglich verarbeitete Vorgänge

Cmdlets sollten außer Kraft setzen der [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) Methode, um alle nachträglich verarbeiteten Vorgänge hinzuzufügen, die für alle Datensätze gültig sind, die vom Cmdlet verarbeitet wurden.
Z. B. Ihr Cmdlet möglicherweise Objektvariablen bereinigen, wenn der Prozess beendet wird verarbeitet.

Wenn PowerShell über eine Befehlspipeline verarbeitet, ruft PowerShell diese Methode einmal für jede Instanz des-Cmdlets in der Pipeline.
Allerdings ist es wichtig zu beachten, dass die PowerShell-Laufzeit nicht die EndProcessing-Methode aufgerufen wird, wenn das Cmdlet über die Verarbeitung von Benutzereingaben Zielpfads abgebrochen wird, oder wenn ein Fehler mit Abbruch in jedem Teil des Cmdlets auftritt.
Aus diesem Grund sollte ein Cmdlet, das Objekt Bereinigung erfordert die vollständige implementieren [System.IDisposable](/dotnet/api/System.IDisposable) Muster, einschließlich von einem Finalizer, damit die Laufzeit sowohl die EndProcessing aufrufen kann und [ System.IDisposable.Dispose](/dotnet/api/System.IDisposable.Dispose) Methoden am Ende der Verarbeitung.
Weitere Informationen dazu, wie PowerShell die Befehlspipeline aufruft, finden Sie unter [Cmdlet Verarbeitung Lebenszyklus](/previous-versions/ms714429(v=vs.85)).

Der folgende Code zeigt eine Implementierung der EndProcessing-Methode.

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the EndProcessing template.");
}
```

## <a name="see-also"></a>Weitere Informationen

[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[SelectStr-Tutorial](selectstr-tutorial.md)

[System.IDisposable](/dotnet/api/System.IDisposable)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
