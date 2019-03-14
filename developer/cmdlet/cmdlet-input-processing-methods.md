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
ms.openlocfilehash: 7f8d25e03707052b1d5b62e245caae360da11d0b
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794942"
---
# <a name="cmdlet-input-processing-methods"></a>Cmdlet-Eingabeverarbeitungsmethoden

Cmdlets muss es sich um eine oder mehrere der in diesem Thema für ihre Arbeit beschriebenen eingabeverarbeitungsmethoden überschreiben. Diese Methoden ermöglichen das-Cmdlet zum Ausführen von vorab verarbeitete Vorgänge, die Eingabe verarbeitet und nach der Verarbeitung von Vorgängen. Diese Methoden ermöglichen auch das Cmdlet-Verarbeitung zu beenden.

## <a name="pre-processing-tasks"></a>Vorab verarbeitete Tasks

Cmdlets sollten außer Kraft setzen der [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) Methode, um alle vorverarbeitungsoperationen hinzuzufügen, die für alle Datensätze gültig sind, die später vom Cmdlet verarbeitet werden. Wenn Windows PowerShell über eine Befehlspipeline verarbeitet, ruft Windows PowerShell diese Methode einmal für jede Instanz des-Cmdlets in der Pipeline. Weitere Informationen dazu, wie Windows PowerShell den Befehlspipeline aufruft, finden Sie unter [Cmdlet Verarbeitung Lebenszyklus](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).

Der folgende Code zeigt eine Implementierung der [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) Methode.

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the BeginProcessing template."
  WriteObject("This is a test of the BeginProcessing template.");
}
```

Ein ausführlicheres Beispiel zur Verwendung der [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) -Methode finden Sie unter [SelectStr Tutorial](./selectstr-tutorial.md). In diesem Tutorial die **Select-Str** Cmdlet verwendet die [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) Methode, um den regulären Ausdruck zu generieren, die verwendet wird, um die Eingabe, die Datensätze verarbeitet werden zu suchen.

## <a name="input-processing-tasks"></a>Geben Sie die Verarbeitung von Aufgaben

Cmdlets können außer Kraft setzen der [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) Methode, um die Eingabe zu verarbeiten, die an das-Cmdlet gesendet wird. Wenn Windows PowerShell über eine Befehlspipeline verarbeitet, ruft Windows PowerShell diese Methode für jeden Eingabedatensatz, die vom Cmdlet verarbeitet wird. Weitere Informationen dazu, wie Windows PowerShell den Befehlspipeline aufruft, finden Sie unter [Cmdlet Verarbeitung Lebenszyklus](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).

Der folgende Code zeigt eine Implementierung der [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) Methode.

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the ProcessRecord template."
  WriteObject("This is a test of the ProcessRecord template.");
}
```

Ein ausführlicheres Beispiel zur Verwendung der [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) -Methode finden Sie unter [SelectStr Tutorial](./selectstr-tutorial.md).

## <a name="post-processing-tasks"></a>Nach der Verarbeitung von Aufgaben

Cmdlets sollten außer Kraft setzen der [System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) Methode, um alle nachträglich verarbeiteten Vorgänge hinzuzufügen, die für alle Datensätze gültig sind, die vom Cmdlet verarbeitet wurden. Z. B. Ihr Cmdlet möglicherweise Objektvariablen bereinigen, wenn der Prozess beendet wird verarbeitet.

Wenn Windows PowerShell über eine Befehlspipeline verarbeitet, ruft Windows PowerShell diese Methode einmal für jede Instanz des-Cmdlets in der Pipeline. Allerdings ist es wichtig zu beachten, dass die Windows PowerShell-Laufzeit nicht Ruft die [System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) Methode, wenn das-Cmdlet über die Verarbeitung von Benutzereingaben Zielpfads abgebrochen wird oder wenn ein Abbruch tritt Fehler in einem beliebigen Teil des Cmdlets auf. Aus diesem Grund sollte ein Cmdlet, das Objekt Bereinigung erfordert die vollständige implementieren [System.Idisposable](/dotnet/api/System.IDisposable) Muster, einschließlich von einem Finalizer, damit die Laufzeit sowohl aufrufen kann die [ System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) und [System.Idisposable.Dispose*](/dotnet/api/System.IDisposable.Dispose) Methoden am Ende der Verarbeitung. Weitere Informationen dazu, wie Windows PowerShell den Befehlspipeline aufruft, finden Sie unter [Cmdlet Verarbeitung Lebenszyklus](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).

Der folgende Code zeigt eine Implementierung der [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) Methode.

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the EndProcessing template."
  WriteObject("This is a test of the EndProcessing template.");
}
```

Ein ausführlicheres Beispiel zur Verwendung der [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) -Methode finden Sie unter [SelectStr Tutorial](./selectstr-tutorial.md).

## <a name="see-also"></a>Weitere Informationen

[System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0)

[System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0)

[System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0)

[System.Idisposable](/dotnet/api/System.IDisposable)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
