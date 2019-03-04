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
ms.openlocfilehash: eff40a01b60985788ae0e21156fec7ec4e27fcf1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855916"
---
# <a name="how-to-override-input-processing-methods"></a><span data-ttu-id="a3eaf-102">Überschreiben von Eingabeverarbeitungsmethoden</span><span class="sxs-lookup"><span data-stu-id="a3eaf-102">How to Override Input Processing Methods</span></span>

<span data-ttu-id="a3eaf-103">Diese Beispiele zeigen, wie Sie die eingabeverarbeitungsmethoden innerhalb eines Cmdlets zu überschreiben.</span><span class="sxs-lookup"><span data-stu-id="a3eaf-103">These examples show how to overwrite the input processing methods within a cmdlet.</span></span> <span data-ttu-id="a3eaf-104">Diese Methoden werden verwendet, um die folgenden Vorgänge auszuführen:</span><span class="sxs-lookup"><span data-stu-id="a3eaf-104">These methods are used to perform the following operations:</span></span>

- <span data-ttu-id="a3eaf-105">Die [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) Methode dient zum Ausführen von einmaligen Start-Vorgängen, die für alle Objekte, die vom Cmdlet verarbeiteten gültig sind.</span><span class="sxs-lookup"><span data-stu-id="a3eaf-105">The [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method is used to perform one-time startup operations that are valid for all the objects processed by the cmdlet.</span></span> <span data-ttu-id="a3eaf-106">Die Windows PowerShell-Laufzeit ruft diese Methode nur einmal aus.</span><span class="sxs-lookup"><span data-stu-id="a3eaf-106">The Windows PowerShell runtime calls this method only once.</span></span>

- <span data-ttu-id="a3eaf-107">Die [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) Methode wird verwendet, um die Objekte, die an das Cmdlet zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="a3eaf-107">The [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is used to process the objects passed to the cmdlet.</span></span> <span data-ttu-id="a3eaf-108">Die Windows PowerShell-Laufzeit ruft diese Methode für jedes Objekt, das an das Cmdlet übergeben.</span><span class="sxs-lookup"><span data-stu-id="a3eaf-108">The Windows PowerShell runtime calls this method for each object passed to the cmdlet.</span></span>

- <span data-ttu-id="a3eaf-109">Die [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) Methode wird verwendet, um einmalige Post Verarbeitungsvorgänge auszuführen.</span><span class="sxs-lookup"><span data-stu-id="a3eaf-109">The [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method is used to perform one-time post processing operations.</span></span> <span data-ttu-id="a3eaf-110">Die Windows PowerShell-Laufzeit ruft diese Methode nur einmal aus.</span><span class="sxs-lookup"><span data-stu-id="a3eaf-110">The Windows PowerShell runtime calls this method only once.</span></span>

## <a name="to-override-the-beginprocessing-method"></a><span data-ttu-id="a3eaf-111">Überschreiben Sie die BeginProcessing-Methode</span><span class="sxs-lookup"><span data-stu-id="a3eaf-111">To override the BeginProcessing method</span></span>

- <span data-ttu-id="a3eaf-112">Deklarieren Sie eine geschützte Überschreibung der [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) Methode.</span><span class="sxs-lookup"><span data-stu-id="a3eaf-112">Declare a protected override of the [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method.</span></span>

<span data-ttu-id="a3eaf-113">Die folgende Klasse gibt eine Beispielnachricht an.</span><span class="sxs-lookup"><span data-stu-id="a3eaf-113">The following class prints a sample message.</span></span> <span data-ttu-id="a3eaf-114">Um diese Klasse verwenden, ändern Sie die Verb- und in der Cmdlet-Attribut, ändern Sie den Namen der Klasse entsprechend den neuen Verb- und und dann die Funktionalität, die Sie benötigen die Überschreibung der Hinzufügen der [System.Management.Automation.Cmdlet.Beginprocessing ](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) Methode.</span><span class="sxs-lookup"><span data-stu-id="a3eaf-114">To use this class, change the verb and noun in the Cmdlet attribute, change the name of the class to reflect the new verb and noun, and then add the functionality you require to the override of the [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method.</span></span>

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

## <a name="to-override-the-processrecord-method"></a><span data-ttu-id="a3eaf-115">So überschreiben Sie die ProcessRecord-Methode</span><span class="sxs-lookup"><span data-stu-id="a3eaf-115">To override the ProcessRecord method</span></span>

- <span data-ttu-id="a3eaf-116">Deklarieren Sie eine geschützte Überschreibung der [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) Methode.</span><span class="sxs-lookup"><span data-stu-id="a3eaf-116">Declare a protected override of the [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

<span data-ttu-id="a3eaf-117">Die folgende Klasse gibt eine Beispielnachricht an.</span><span class="sxs-lookup"><span data-stu-id="a3eaf-117">The following class prints a sample message.</span></span> <span data-ttu-id="a3eaf-118">Um diese Klasse verwenden, ändern Sie die Verb- und in der Cmdlet-Attribut, ändern Sie den Namen der Klasse entsprechend den neuen Verb- und und dann die Funktionalität, die Sie benötigen die Überschreibung der Hinzufügen der [System.Management.Automation.Cmdlet.Processrecord\* ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) Methode.</span><span class="sxs-lookup"><span data-stu-id="a3eaf-118">To use this class, change the verb and noun in the Cmdlet attribute, change the name of the class to reflect the new verb and noun, and then add the functionality you require to the override of the [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

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

## <a name="to-override-the-endprocessing-method"></a><span data-ttu-id="a3eaf-119">So überschreiben Sie die EndProcessing-Methode</span><span class="sxs-lookup"><span data-stu-id="a3eaf-119">To override the EndProcessing method</span></span>

- <span data-ttu-id="a3eaf-120">Deklarieren Sie eine geschützte Überschreibung der [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) Methode.</span><span class="sxs-lookup"><span data-stu-id="a3eaf-120">Declare a protected override of the [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span>

<span data-ttu-id="a3eaf-121">Die folgende Klasse gibt ein Beispiel aus.</span><span class="sxs-lookup"><span data-stu-id="a3eaf-121">The following class prints a sample.</span></span> <span data-ttu-id="a3eaf-122">Um diese Klasse verwenden, ändern Sie die Verb- und in der Cmdlet-Attribut, ändern Sie den Namen der Klasse entsprechend den neuen Verb- und und dann die Funktionalität, die Sie benötigen die Überschreibung der Hinzufügen der [System.Management.Automation.Cmdlet.Endprocessing\* ](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) Methode.</span><span class="sxs-lookup"><span data-stu-id="a3eaf-122">To use this class, change the verb and noun in the Cmdlet attribute, change the name of the class to reflect the new verb and noun, and then add the functionality you require to the override of the [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a3eaf-123">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="a3eaf-123">See Also</span></span>

[<span data-ttu-id="a3eaf-124">System.Management.Automation.Cmdlet.Beginprocessing\*</span><span class="sxs-lookup"><span data-stu-id="a3eaf-124">System.Management.Automation.Cmdlet.Beginprocessing\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="a3eaf-125">System.Management.Automation.Cmdlet.Endprocessing\*</span><span class="sxs-lookup"><span data-stu-id="a3eaf-125">System.Management.Automation.Cmdlet.Endprocessing\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="a3eaf-126">System.Management.Automation.Cmdlet.Processrecord\*</span><span class="sxs-lookup"><span data-stu-id="a3eaf-126">System.Management.Automation.Cmdlet.Processrecord\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="a3eaf-127">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="a3eaf-127">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
