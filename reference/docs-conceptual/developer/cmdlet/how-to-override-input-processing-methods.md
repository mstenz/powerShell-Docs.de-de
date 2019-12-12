---
title: Überschreiben von Eingabe Verarbeitungsmethoden | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1a1ad921-5816-4937-acf1-ed4760fae740
caps.latest.revision: 8
ms.openlocfilehash: cfee55576518cf9ce38501192872ce94054f5213
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364469"
---
# <a name="how-to-override-input-processing-methods"></a><span data-ttu-id="8d600-102">Überschreiben von Eingabeverarbeitungsmethoden</span><span class="sxs-lookup"><span data-stu-id="8d600-102">How to Override Input Processing Methods</span></span>

<span data-ttu-id="8d600-103">In diesen Beispielen wird gezeigt, wie die Eingabe Verarbeitungsmethoden innerhalb eines Cmdlets überschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="8d600-103">These examples show how to overwrite the input processing methods within a cmdlet.</span></span> <span data-ttu-id="8d600-104">Diese Methoden werden verwendet, um die folgenden Vorgänge auszuführen:</span><span class="sxs-lookup"><span data-stu-id="8d600-104">These methods are used to perform the following operations:</span></span>

- <span data-ttu-id="8d600-105">Die [System. Management. Automation. Cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) -Methode wird zum Ausführen von einmaligen Start Vorgängen verwendet, die für alle vom Cmdlet verarbeiteten Objekte gültig sind.</span><span class="sxs-lookup"><span data-stu-id="8d600-105">The [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method is used to perform one-time startup operations that are valid for all the objects processed by the cmdlet.</span></span> <span data-ttu-id="8d600-106">Die Windows PowerShell-Laufzeit ruft diese Methode nur einmal auf.</span><span class="sxs-lookup"><span data-stu-id="8d600-106">The Windows PowerShell runtime calls this method only once.</span></span>

- <span data-ttu-id="8d600-107">Die [System. Management. Automation. Cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) -Methode wird verwendet, um die Objekte zu verarbeiten, die an das Cmdlet übergeben werden.</span><span class="sxs-lookup"><span data-stu-id="8d600-107">The [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is used to process the objects passed to the cmdlet.</span></span> <span data-ttu-id="8d600-108">Die Windows PowerShell-Laufzeit ruft diese Methode für jedes Objekt auf, das an das Cmdlet übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="8d600-108">The Windows PowerShell runtime calls this method for each object passed to the cmdlet.</span></span>

- <span data-ttu-id="8d600-109">Die [System. Management. Automation. Cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) -Methode wird verwendet, um einmal nach Verarbeitungsvorgänge auszuführen.</span><span class="sxs-lookup"><span data-stu-id="8d600-109">The [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method is used to perform one-time post processing operations.</span></span> <span data-ttu-id="8d600-110">Die Windows PowerShell-Laufzeit ruft diese Methode nur einmal auf.</span><span class="sxs-lookup"><span data-stu-id="8d600-110">The Windows PowerShell runtime calls this method only once.</span></span>

## <a name="to-override-the-beginprocessing-method"></a><span data-ttu-id="8d600-111">So überschreiben Sie die BeginProcessing-Methode</span><span class="sxs-lookup"><span data-stu-id="8d600-111">To override the BeginProcessing method</span></span>

- <span data-ttu-id="8d600-112">Deklarieren Sie eine geschützte außer Kraft setzung der [System. Management. Automation. Cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) -Methode.</span><span class="sxs-lookup"><span data-stu-id="8d600-112">Declare a protected override of the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method.</span></span>

<span data-ttu-id="8d600-113">Die folgende Klasse druckt eine Beispiel Nachricht.</span><span class="sxs-lookup"><span data-stu-id="8d600-113">The following class prints a sample message.</span></span> <span data-ttu-id="8d600-114">Um diese Klasse zu verwenden, ändern Sie das Verb und das Nomen im Cmdlet-Attribut, ändern Sie den Namen der Klasse, um das neue Verb und das neue Substantiv widerzuspiegeln, und fügen Sie dann die erforderliche Funktionalität zur außer Kraft setzung der [System. Management. Automation. Cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) -Methode hinzu.</span><span class="sxs-lookup"><span data-stu-id="8d600-114">To use this class, change the verb and noun in the Cmdlet attribute, change the name of the class to reflect the new verb and noun, and then add the functionality you require to the override of the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method.</span></span>

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

## <a name="to-override-the-processrecord-method"></a><span data-ttu-id="8d600-115">So überschreiben Sie die ProcessRecord-Methode</span><span class="sxs-lookup"><span data-stu-id="8d600-115">To override the ProcessRecord method</span></span>

- <span data-ttu-id="8d600-116">Deklarieren Sie eine geschützte außer Kraft setzung der [System. Management. Automation. Cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) -Methode.</span><span class="sxs-lookup"><span data-stu-id="8d600-116">Declare a protected override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

<span data-ttu-id="8d600-117">Die folgende Klasse druckt eine Beispiel Nachricht.</span><span class="sxs-lookup"><span data-stu-id="8d600-117">The following class prints a sample message.</span></span> <span data-ttu-id="8d600-118">Um diese Klasse zu verwenden, ändern Sie das Verb und das Nomen im Cmdlet-Attribut, ändern Sie den Namen der Klasse, um das neue Verb und das neue Substantiv widerzuspiegeln, und fügen Sie dann die erforderliche Funktionalität zur außer Kraft setzung der [System. Management. Automation. Cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) -Methode hinzu.</span><span class="sxs-lookup"><span data-stu-id="8d600-118">To use this class, change the verb and noun in the Cmdlet attribute, change the name of the class to reflect the new verb and noun, and then add the functionality you require to the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

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

## <a name="to-override-the-endprocessing-method"></a><span data-ttu-id="8d600-119">So überschreiben Sie die EndProcessing-Methode</span><span class="sxs-lookup"><span data-stu-id="8d600-119">To override the EndProcessing method</span></span>

- <span data-ttu-id="8d600-120">Deklarieren Sie eine geschützte außer Kraft setzung der [System. Management. Automation. Cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) -Methode.</span><span class="sxs-lookup"><span data-stu-id="8d600-120">Declare a protected override of the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span>

<span data-ttu-id="8d600-121">Die folgende Klasse druckt ein Beispiel.</span><span class="sxs-lookup"><span data-stu-id="8d600-121">The following class prints a sample.</span></span> <span data-ttu-id="8d600-122">Um diese Klasse zu verwenden, ändern Sie das Verb und das Nomen im Cmdlet-Attribut, ändern Sie den Namen der Klasse, um das neue Verb und das neue Substantiv widerzuspiegeln, und fügen Sie dann die erforderliche Funktionalität zur außer Kraft setzung der [System. Management. Automation. Cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) -Methode hinzu.</span><span class="sxs-lookup"><span data-stu-id="8d600-122">To use this class, change the verb and noun in the Cmdlet attribute, change the name of the class to reflect the new verb and noun, and then add the functionality you require to the override of the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="8d600-123">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="8d600-123">See Also</span></span>

[<span data-ttu-id="8d600-124">System. Management. Automation. Cmdlet. BeginProcessing</span><span class="sxs-lookup"><span data-stu-id="8d600-124">System.Management.Automation.Cmdlet.BeginProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="8d600-125">System. Management. Automation. Cmdlet. EndProcessing</span><span class="sxs-lookup"><span data-stu-id="8d600-125">System.Management.Automation.Cmdlet.EndProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="8d600-126">System. Management. Automation. Cmdlet. ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="8d600-126">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="8d600-127">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="8d600-127">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
