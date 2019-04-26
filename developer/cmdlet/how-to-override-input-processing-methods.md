---
title: 'Gewusst wie: Überschreiben von Eingabeverarbeitungsmethoden | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1a1ad921-5816-4937-acf1-ed4760fae740
caps.latest.revision: 8
ms.openlocfilehash: cfee55576518cf9ce38501192872ce94054f5213
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067942"
---
# <a name="how-to-override-input-processing-methods"></a>Überschreiben von Eingabeverarbeitungsmethoden

Diese Beispiele zeigen, wie Sie die eingabeverarbeitungsmethoden innerhalb eines Cmdlets zu überschreiben. Diese Methoden werden verwendet, um die folgenden Vorgänge auszuführen:

- Die [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) Methode dient zum Ausführen von einmaligen Start-Vorgängen, die für alle Objekte, die vom Cmdlet verarbeiteten gültig sind. Die Windows PowerShell-Laufzeit ruft diese Methode nur einmal aus.

- Die [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) Methode wird verwendet, um die Objekte, die an das Cmdlet zu verarbeiten. Die Windows PowerShell-Laufzeit ruft diese Methode für jedes Objekt, das an das Cmdlet übergeben.

- Die [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) Methode wird verwendet, um einmalige Post Verarbeitungsvorgänge auszuführen. Die Windows PowerShell-Laufzeit ruft diese Methode nur einmal aus.

## <a name="to-override-the-beginprocessing-method"></a>Überschreiben Sie die BeginProcessing-Methode

- Deklarieren Sie eine geschützte Überschreibung der [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) Methode.

Die folgende Klasse gibt eine Beispielnachricht an. Um diese Klasse verwenden, ändern Sie die Verb- und in der Cmdlet-Attribut, ändern Sie den Namen der Klasse entsprechend den neuen Verb- und und dann die Funktionalität, die Sie benötigen die Überschreibung der Hinzufügen der [System.Management.Automation.Cmdlet.BeginProcessing ](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) Methode.

```csharp
[Cmdlet(VerbsDiagnostic.Test, "BeginProcessingClass")]
public class TestBeginProcessingClassTemplate : Cmdlet
{
  // Override the BeginProcessing method to add preprocessing
  //operations to the cmdlet.
  protected override void BeginProcessing()
  {
    // Replace the WriteObject method with the logic required
    // by your cmdlet. It is used here to generate the following
    // output:
    // "This is a test of the BeginProcessing template."
    WriteObject("This is a test of the BeginProcessing template.");
  }
}
```

## <a name="to-override-the-processrecord-method"></a>So überschreiben Sie die ProcessRecord-Methode

- Deklarieren Sie eine geschützte Überschreibung der [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) Methode.

Die folgende Klasse gibt eine Beispielnachricht an. Um diese Klasse verwenden, ändern Sie die Verb- und in der Cmdlet-Attribut, ändern Sie den Namen der Klasse entsprechend den neuen Verb- und und dann die Funktionalität, die Sie benötigen die Überschreibung der Hinzufügen der [System.Management.Automation.Cmdlet.ProcessRecord ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) Methode.

```csharp
[Cmdlet(VerbsDiagnostic.Test, "ProcessRecordClass")]
public class TestProcessRecordClassTemplate : Cmdlet
{
    // Override the ProcessRecord method to add processing
    //operations to the cmdlet.
    protected override void ProcessRecord()
    {
        // Replace the WriteObject method with the logic required
        // by your cmdlet. It is used here to generate the following
        // output:
        // "This is a test of the ProcessRecord template."
        WriteObject("This is a test of the ProcessRecord template.");
    }
}

```

## <a name="to-override-the-endprocessing-method"></a>So überschreiben Sie die EndProcessing-Methode

- Deklarieren Sie eine geschützte Überschreibung der [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) Methode.

Die folgende Klasse gibt ein Beispiel aus. Um diese Klasse verwenden, ändern Sie die Verb- und in der Cmdlet-Attribut, ändern Sie den Namen der Klasse entsprechend den neuen Verb- und und dann die Funktionalität, die Sie benötigen die Überschreibung der Hinzufügen der [System.Management.Automation.Cmdlet.EndProcessing ](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) Methode.

```csharp
[Cmdlet(VerbsDiagnostic.Test, "EndProcessingClass")]
public class TestEndProcessingClassTemplate : Cmdlet
{
  // Override the EndProcessing method to add postprocessing
  //operations to the cmdlet.
  protected override void EndProcessing()
  {
    // Replace the WriteObject method with the logic required
    // by your cmdlet. It is used here to generate the following
    // output:
    // "This is a test of the BeginProcessing template."
    WriteObject("This is a test of the EndProcessing template.");
  }
}
```

## <a name="see-also"></a>Weitere Informationen

[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
