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
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056395"
---
# <a name="how-to-override-input-processing-methods"></a><span data-ttu-id="dc578-102">Überschreiben von Eingabeverarbeitungsmethoden</span><span class="sxs-lookup"><span data-stu-id="dc578-102">How to Override Input Processing Methods</span></span>

<span data-ttu-id="dc578-103">Diese Beispiele zeigen, wie Sie die eingabeverarbeitungsmethoden innerhalb eines Cmdlets zu überschreiben.</span><span class="sxs-lookup"><span data-stu-id="dc578-103">These examples show how to overwrite the input processing methods within a cmdlet.</span></span> <span data-ttu-id="dc578-104">Diese Methoden werden verwendet, um die folgenden Vorgänge auszuführen:</span><span class="sxs-lookup"><span data-stu-id="dc578-104">These methods are used to perform the following operations:</span></span>

- <span data-ttu-id="dc578-105">Die [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) Methode dient zum Ausführen von einmaligen Start-Vorgängen, die für alle Objekte, die vom Cmdlet verarbeiteten gültig sind.</span><span class="sxs-lookup"><span data-stu-id="dc578-105">The [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method is used to perform one-time startup operations that are valid for all the objects processed by the cmdlet.</span></span> <span data-ttu-id="dc578-106">Die Windows PowerShell-Laufzeit ruft diese Methode nur einmal aus.</span><span class="sxs-lookup"><span data-stu-id="dc578-106">The Windows PowerShell runtime calls this method only once.</span></span>

- <span data-ttu-id="dc578-107">Die [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) Methode wird verwendet, um die Objekte, die an das Cmdlet zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="dc578-107">The [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is used to process the objects passed to the cmdlet.</span></span> <span data-ttu-id="dc578-108">Die Windows PowerShell-Laufzeit ruft diese Methode für jedes Objekt, das an das Cmdlet übergeben.</span><span class="sxs-lookup"><span data-stu-id="dc578-108">The Windows PowerShell runtime calls this method for each object passed to the cmdlet.</span></span>

- <span data-ttu-id="dc578-109">Die [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) Methode wird verwendet, um einmalige Post Verarbeitungsvorgänge auszuführen.</span><span class="sxs-lookup"><span data-stu-id="dc578-109">The [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method is used to perform one-time post processing operations.</span></span> <span data-ttu-id="dc578-110">Die Windows PowerShell-Laufzeit ruft diese Methode nur einmal aus.</span><span class="sxs-lookup"><span data-stu-id="dc578-110">The Windows PowerShell runtime calls this method only once.</span></span>

## <a name="to-override-the-beginprocessing-method"></a><span data-ttu-id="dc578-111">Überschreiben Sie die BeginProcessing-Methode</span><span class="sxs-lookup"><span data-stu-id="dc578-111">To override the BeginProcessing method</span></span>

- <span data-ttu-id="dc578-112">Deklarieren Sie eine geschützte Überschreibung der [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) Methode.</span><span class="sxs-lookup"><span data-stu-id="dc578-112">Declare a protected override of the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method.</span></span>

<span data-ttu-id="dc578-113">Die folgende Klasse gibt eine Beispielnachricht an.</span><span class="sxs-lookup"><span data-stu-id="dc578-113">The following class prints a sample message.</span></span> <span data-ttu-id="dc578-114">Um diese Klasse verwenden, ändern Sie die Verb- und in der Cmdlet-Attribut, ändern Sie den Namen der Klasse entsprechend den neuen Verb- und und dann die Funktionalität, die Sie benötigen die Überschreibung der Hinzufügen der [System.Management.Automation.Cmdlet.BeginProcessing ](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) Methode.</span><span class="sxs-lookup"><span data-stu-id="dc578-114">To use this class, change the verb and noun in the Cmdlet attribute, change the name of the class to reflect the new verb and noun, and then add the functionality you require to the override of the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method.</span></span>

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

## <a name="to-override-the-processrecord-method"></a><span data-ttu-id="dc578-115">So überschreiben Sie die ProcessRecord-Methode</span><span class="sxs-lookup"><span data-stu-id="dc578-115">To override the ProcessRecord method</span></span>

- <span data-ttu-id="dc578-116">Deklarieren Sie eine geschützte Überschreibung der [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) Methode.</span><span class="sxs-lookup"><span data-stu-id="dc578-116">Declare a protected override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

<span data-ttu-id="dc578-117">Die folgende Klasse gibt eine Beispielnachricht an.</span><span class="sxs-lookup"><span data-stu-id="dc578-117">The following class prints a sample message.</span></span> <span data-ttu-id="dc578-118">Um diese Klasse verwenden, ändern Sie die Verb- und in der Cmdlet-Attribut, ändern Sie den Namen der Klasse entsprechend den neuen Verb- und und dann die Funktionalität, die Sie benötigen die Überschreibung der Hinzufügen der [System.Management.Automation.Cmdlet.ProcessRecord ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) Methode.</span><span class="sxs-lookup"><span data-stu-id="dc578-118">To use this class, change the verb and noun in the Cmdlet attribute, change the name of the class to reflect the new verb and noun, and then add the functionality you require to the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

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

## <a name="to-override-the-endprocessing-method"></a><span data-ttu-id="dc578-119">So überschreiben Sie die EndProcessing-Methode</span><span class="sxs-lookup"><span data-stu-id="dc578-119">To override the EndProcessing method</span></span>

- <span data-ttu-id="dc578-120">Deklarieren Sie eine geschützte Überschreibung der [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) Methode.</span><span class="sxs-lookup"><span data-stu-id="dc578-120">Declare a protected override of the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span>

<span data-ttu-id="dc578-121">Die folgende Klasse gibt ein Beispiel aus.</span><span class="sxs-lookup"><span data-stu-id="dc578-121">The following class prints a sample.</span></span> <span data-ttu-id="dc578-122">Um diese Klasse verwenden, ändern Sie die Verb- und in der Cmdlet-Attribut, ändern Sie den Namen der Klasse entsprechend den neuen Verb- und und dann die Funktionalität, die Sie benötigen die Überschreibung der Hinzufügen der [System.Management.Automation.Cmdlet.EndProcessing ](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) Methode.</span><span class="sxs-lookup"><span data-stu-id="dc578-122">To use this class, change the verb and noun in the Cmdlet attribute, change the name of the class to reflect the new verb and noun, and then add the functionality you require to the override of the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="dc578-123">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="dc578-123">See Also</span></span>

[<span data-ttu-id="dc578-124">System.Management.Automation.Cmdlet.BeginProcessing</span><span class="sxs-lookup"><span data-stu-id="dc578-124">System.Management.Automation.Cmdlet.BeginProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="dc578-125">System.Management.Automation.Cmdlet.EndProcessing</span><span class="sxs-lookup"><span data-stu-id="dc578-125">System.Management.Automation.Cmdlet.EndProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="dc578-126">System.Management.Automation.Cmdlet.ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="dc578-126">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="dc578-127">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="dc578-127">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
