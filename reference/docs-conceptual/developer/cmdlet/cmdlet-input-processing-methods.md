---
title: Cmdlet-Eingabe Verarbeitungsmethoden | Microsoft-Dokumentation
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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369869"
---
# <a name="cmdlet-input-processing-methods"></a><span data-ttu-id="e05c4-102">Cmdlet-Eingabeverarbeitungsmethoden</span><span class="sxs-lookup"><span data-stu-id="e05c4-102">Cmdlet Input Processing Methods</span></span>

<span data-ttu-id="e05c4-103">Cmdlets müssen eine oder mehrere der in diesem Thema beschriebenen Eingabe Verarbeitungsmethoden überschreiben, um Ihre Arbeit zu erledigen.</span><span class="sxs-lookup"><span data-stu-id="e05c4-103">Cmdlets must override one or more of the input processing methods described in this topic to perform their work.</span></span>
<span data-ttu-id="e05c4-104">Diese Methoden ermöglichen es dem Cmdlet, Vorgänge der vorab Verarbeitung, der Eingabe Verarbeitung und der Nachbearbeitung auszuführen.</span><span class="sxs-lookup"><span data-stu-id="e05c4-104">These methods allow the cmdlet to perform operations of pre-processing, input processing, and post-processing.</span></span>
<span data-ttu-id="e05c4-105">Diese Methoden ermöglichen auch das Abbrechen der Cmdlet-Verarbeitung.</span><span class="sxs-lookup"><span data-stu-id="e05c4-105">These methods also allow you to stop cmdlet processing.</span></span>
<span data-ttu-id="e05c4-106">Ein ausführlicheres Beispiel für die Verwendung dieser Methoden finden Sie unter [selectstr-Tutorial](selectstr-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="e05c4-106">For a more detailed example of how to use these methods, see [SelectStr Tutorial](selectstr-tutorial.md).</span></span>

## <a name="pre-processing-operations"></a><span data-ttu-id="e05c4-107">Vorverarbeitungs Vorgänge</span><span class="sxs-lookup"><span data-stu-id="e05c4-107">Pre-Processing Operations</span></span>

<span data-ttu-id="e05c4-108">Cmdlets sollten die [System. Management. Automation. Cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) -Methode überschreiben, um Vorverarbeitungs Vorgänge hinzuzufügen, die für alle Datensätze gültig sind, die später vom Cmdlet verarbeitet werden.</span><span class="sxs-lookup"><span data-stu-id="e05c4-108">Cmdlets should override the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method to add any preprocessing operations that are valid for all the records that will be processed later by the cmdlet.</span></span>
<span data-ttu-id="e05c4-109">Wenn PowerShell eine Befehls Pipeline verarbeitet, ruft PowerShell diese Methode für jede Instanz des Cmdlets in der Pipeline einmal auf.</span><span class="sxs-lookup"><span data-stu-id="e05c4-109">When PowerShell processes a command pipeline, PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span>
<span data-ttu-id="e05c4-110">Weitere Informationen dazu, wie PowerShell die Befehls Pipeline aufruft, finden Sie unter [Cmdlet processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="e05c4-110">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="e05c4-111">Der folgende Code zeigt eine Implementierung der BeginProcessing-Methode.</span><span class="sxs-lookup"><span data-stu-id="e05c4-111">The following code shows an implementation of the BeginProcessing method.</span></span>

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the BeginProcessing template.");
}
```

## <a name="input-processing-operations"></a><span data-ttu-id="e05c4-112">Eingabe Verarbeitungsvorgänge</span><span class="sxs-lookup"><span data-stu-id="e05c4-112">Input Processing Operations</span></span>

<span data-ttu-id="e05c4-113">Cmdlets können die [System. Management. Automation. Cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) -Methode überschreiben, um die Eingabe zu verarbeiten, die an das Cmdlet gesendet wird.</span><span class="sxs-lookup"><span data-stu-id="e05c4-113">Cmdlets can override the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to process the input that is sent to the cmdlet.</span></span>
<span data-ttu-id="e05c4-114">Wenn PowerShell eine Befehls Pipeline verarbeitet, ruft PowerShell diese Methode für jeden Eingabedaten Satz auf, der vom Cmdlet verarbeitet wird.</span><span class="sxs-lookup"><span data-stu-id="e05c4-114">When PowerShell processes a command pipeline, PowerShell calls this method for each input record that is processed by the cmdlet.</span></span>
<span data-ttu-id="e05c4-115">Weitere Informationen dazu, wie PowerShell die Befehls Pipeline aufruft, finden Sie unter [Cmdlet processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="e05c4-115">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="e05c4-116">Der folgende Code zeigt eine Implementierung der ProcessRecord-Methode.</span><span class="sxs-lookup"><span data-stu-id="e05c4-116">The following code shows an implementation of the ProcessRecord method.</span></span>

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the ProcessRecord template.");
}
```

## <a name="post-processing-operations"></a><span data-ttu-id="e05c4-117">Vorgänge nach der Verarbeitung</span><span class="sxs-lookup"><span data-stu-id="e05c4-117">Post-Processing Operations</span></span>

<span data-ttu-id="e05c4-118">Cmdlets sollten die [System. Management. Automation. Cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) -Methode überschreiben, um alle nach Verarbeitungsvorgänge hinzuzufügen, die für alle vom Cmdlet verarbeiteten Datensätze gültig sind.</span><span class="sxs-lookup"><span data-stu-id="e05c4-118">Cmdlets should override the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method to add any post-processing operations that are valid for all the records that were processed by the cmdlet.</span></span>
<span data-ttu-id="e05c4-119">Beispielsweise muss das Cmdlet möglicherweise Objektvariablen bereinigen, nachdem die Verarbeitung abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="e05c4-119">For example, your cmdlet might have to clean up object variables after it is finished processing.</span></span>

<span data-ttu-id="e05c4-120">Wenn PowerShell eine Befehls Pipeline verarbeitet, ruft PowerShell diese Methode für jede Instanz des Cmdlets in der Pipeline einmal auf.</span><span class="sxs-lookup"><span data-stu-id="e05c4-120">When PowerShell processes a command pipeline, PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span>
<span data-ttu-id="e05c4-121">Es ist jedoch wichtig zu beachten, dass die PowerShell-Runtime die EndProcessing-Methode nicht aufruft, wenn das Cmdlet in der Mitte durch die Eingabe Verarbeitung abgebrochen wird oder wenn in einem beliebigen Teil des Cmdlets ein Abbruch Fehler auftritt.</span><span class="sxs-lookup"><span data-stu-id="e05c4-121">However, it is important to remember that the PowerShell runtime will not call the EndProcessing method if the cmdlet is canceled midway through its input processing or if a terminating error occurs in any part of the cmdlet.</span></span>
<span data-ttu-id="e05c4-122">Aus diesem Grund sollte ein Cmdlet, das die Objekt Bereinigung erfordert, das komplette [System. iverwerf-](/dotnet/api/System.IDisposable) Muster implementieren, einschließlich eines Finalizers, damit die Laufzeit sowohl die EndProcessing-als auch die [System. iverwerf.](/dotnet/api/System.IDisposable.Dispose) verwerfen-Methode am Ende von abrufen kann. Aufbereitungs.</span><span class="sxs-lookup"><span data-stu-id="e05c4-122">For this reason, a cmdlet that requires object cleanup should implement the complete [System.IDisposable](/dotnet/api/System.IDisposable) pattern, including a finalizer, so that the runtime can call both the EndProcessing and [System.IDisposable.Dispose](/dotnet/api/System.IDisposable.Dispose) methods at the end of processing.</span></span>
<span data-ttu-id="e05c4-123">Weitere Informationen dazu, wie PowerShell die Befehls Pipeline aufruft, finden Sie unter [Cmdlet processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="e05c4-123">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="e05c4-124">Der folgende Code zeigt eine Implementierung der EndProcessing-Methode.</span><span class="sxs-lookup"><span data-stu-id="e05c4-124">The following code shows an implementation of the EndProcessing method.</span></span>

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the EndProcessing template.");
}
```

## <a name="see-also"></a><span data-ttu-id="e05c4-125">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="e05c4-125">See Also</span></span>

[<span data-ttu-id="e05c4-126">System. Management. Automation. Cmdlet. BeginProcessing</span><span class="sxs-lookup"><span data-stu-id="e05c4-126">System.Management.Automation.Cmdlet.BeginProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="e05c4-127">System. Management. Automation. Cmdlet. ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="e05c4-127">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="e05c4-128">System. Management. Automation. Cmdlet. EndProcessing</span><span class="sxs-lookup"><span data-stu-id="e05c4-128">System.Management.Automation.Cmdlet.EndProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="e05c4-129">Selectstr-Tutorial</span><span class="sxs-lookup"><span data-stu-id="e05c4-129">SelectStr Tutorial</span></span>](selectstr-tutorial.md)

[<span data-ttu-id="e05c4-130">System. iverwerfbare</span><span class="sxs-lookup"><span data-stu-id="e05c4-130">System.IDisposable</span></span>](/dotnet/api/System.IDisposable)

[<span data-ttu-id="e05c4-131">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="e05c4-131">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
