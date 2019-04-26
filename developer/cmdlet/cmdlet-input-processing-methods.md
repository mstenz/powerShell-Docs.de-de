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
# <a name="cmdlet-input-processing-methods"></a><span data-ttu-id="2a6e6-102">Cmdlet-Eingabeverarbeitungsmethoden</span><span class="sxs-lookup"><span data-stu-id="2a6e6-102">Cmdlet Input Processing Methods</span></span>

<span data-ttu-id="2a6e6-103">Cmdlets muss es sich um eine oder mehrere der in diesem Thema für ihre Arbeit beschriebenen eingabeverarbeitungsmethoden überschreiben.</span><span class="sxs-lookup"><span data-stu-id="2a6e6-103">Cmdlets must override one or more of the input processing methods described in this topic to perform their work.</span></span>
<span data-ttu-id="2a6e6-104">Diese Methoden ermöglichen das-Cmdlet zum Ausführen von Vorgängen der vorverarbeitung, Eingabeverarbeitung und nach der Verarbeitung.</span><span class="sxs-lookup"><span data-stu-id="2a6e6-104">These methods allow the cmdlet to perform operations of pre-processing, input processing, and post-processing.</span></span>
<span data-ttu-id="2a6e6-105">Diese Methoden ermöglichen auch das Cmdlet-Verarbeitung zu beenden.</span><span class="sxs-lookup"><span data-stu-id="2a6e6-105">These methods also allow you to stop cmdlet processing.</span></span>
<span data-ttu-id="2a6e6-106">Ein ausführlicheres Beispiel zur Verwendung dieser Methoden finden Sie unter [SelectStr Tutorial](selectstr-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="2a6e6-106">For a more detailed example of how to use these methods, see [SelectStr Tutorial](selectstr-tutorial.md).</span></span>

## <a name="pre-processing-operations"></a><span data-ttu-id="2a6e6-107">Vorab verarbeitete Vorgänge</span><span class="sxs-lookup"><span data-stu-id="2a6e6-107">Pre-Processing Operations</span></span>

<span data-ttu-id="2a6e6-108">Cmdlets sollten außer Kraft setzen der [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) Methode, um alle vorverarbeitungsoperationen hinzuzufügen, die für alle Datensätze gültig sind, die später vom Cmdlet verarbeitet werden.</span><span class="sxs-lookup"><span data-stu-id="2a6e6-108">Cmdlets should override the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method to add any preprocessing operations that are valid for all the records that will be processed later by the cmdlet.</span></span>
<span data-ttu-id="2a6e6-109">Wenn PowerShell über eine Befehlspipeline verarbeitet, ruft PowerShell diese Methode einmal für jede Instanz des-Cmdlets in der Pipeline.</span><span class="sxs-lookup"><span data-stu-id="2a6e6-109">When PowerShell processes a command pipeline, PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span>
<span data-ttu-id="2a6e6-110">Weitere Informationen dazu, wie PowerShell die Befehlspipeline aufruft, finden Sie unter [Cmdlet Verarbeitung Lebenszyklus](/previous-versions/ms714429(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="2a6e6-110">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="2a6e6-111">Der folgende Code zeigt eine Implementierung der BeginProcessing-Methode.</span><span class="sxs-lookup"><span data-stu-id="2a6e6-111">The following code shows an implementation of the BeginProcessing method.</span></span>

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the BeginProcessing template.");
}
```

## <a name="input-processing-operations"></a><span data-ttu-id="2a6e6-112">Geben Sie die Verarbeitung von Vorgängen</span><span class="sxs-lookup"><span data-stu-id="2a6e6-112">Input Processing Operations</span></span>

<span data-ttu-id="2a6e6-113">Cmdlets können außer Kraft setzen der [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) Methode, um die Eingabe zu verarbeiten, die an das-Cmdlet gesendet wird.</span><span class="sxs-lookup"><span data-stu-id="2a6e6-113">Cmdlets can override the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to process the input that is sent to the cmdlet.</span></span>
<span data-ttu-id="2a6e6-114">Wenn PowerShell über eine Befehlspipeline verarbeitet, ruft PowerShell diese Methode für jeden Eingabedatensatz, die vom Cmdlet verarbeitet wird.</span><span class="sxs-lookup"><span data-stu-id="2a6e6-114">When PowerShell processes a command pipeline, PowerShell calls this method for each input record that is processed by the cmdlet.</span></span>
<span data-ttu-id="2a6e6-115">Weitere Informationen dazu, wie PowerShell die Befehlspipeline aufruft, finden Sie unter [Cmdlet Verarbeitung Lebenszyklus](/previous-versions/ms714429(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="2a6e6-115">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="2a6e6-116">Der folgende Code zeigt eine Implementierung der ProcessRecord-Methode.</span><span class="sxs-lookup"><span data-stu-id="2a6e6-116">The following code shows an implementation of the ProcessRecord method.</span></span>

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the ProcessRecord template.");
}
```

## <a name="post-processing-operations"></a><span data-ttu-id="2a6e6-117">Nachträglich verarbeitete Vorgänge</span><span class="sxs-lookup"><span data-stu-id="2a6e6-117">Post-Processing Operations</span></span>

<span data-ttu-id="2a6e6-118">Cmdlets sollten außer Kraft setzen der [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) Methode, um alle nachträglich verarbeiteten Vorgänge hinzuzufügen, die für alle Datensätze gültig sind, die vom Cmdlet verarbeitet wurden.</span><span class="sxs-lookup"><span data-stu-id="2a6e6-118">Cmdlets should override the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method to add any post-processing operations that are valid for all the records that were processed by the cmdlet.</span></span>
<span data-ttu-id="2a6e6-119">Z. B. Ihr Cmdlet möglicherweise Objektvariablen bereinigen, wenn der Prozess beendet wird verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="2a6e6-119">For example, your cmdlet might have to clean up object variables after it is finished processing.</span></span>

<span data-ttu-id="2a6e6-120">Wenn PowerShell über eine Befehlspipeline verarbeitet, ruft PowerShell diese Methode einmal für jede Instanz des-Cmdlets in der Pipeline.</span><span class="sxs-lookup"><span data-stu-id="2a6e6-120">When PowerShell processes a command pipeline, PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span>
<span data-ttu-id="2a6e6-121">Allerdings ist es wichtig zu beachten, dass die PowerShell-Laufzeit nicht die EndProcessing-Methode aufgerufen wird, wenn das Cmdlet über die Verarbeitung von Benutzereingaben Zielpfads abgebrochen wird, oder wenn ein Fehler mit Abbruch in jedem Teil des Cmdlets auftritt.</span><span class="sxs-lookup"><span data-stu-id="2a6e6-121">However, it is important to remember that the PowerShell runtime will not call the EndProcessing method if the cmdlet is canceled midway through its input processing or if a terminating error occurs in any part of the cmdlet.</span></span>
<span data-ttu-id="2a6e6-122">Aus diesem Grund sollte ein Cmdlet, das Objekt Bereinigung erfordert die vollständige implementieren [System.IDisposable](/dotnet/api/System.IDisposable) Muster, einschließlich von einem Finalizer, damit die Laufzeit sowohl die EndProcessing aufrufen kann und [ System.IDisposable.Dispose](/dotnet/api/System.IDisposable.Dispose) Methoden am Ende der Verarbeitung.</span><span class="sxs-lookup"><span data-stu-id="2a6e6-122">For this reason, a cmdlet that requires object cleanup should implement the complete [System.IDisposable](/dotnet/api/System.IDisposable) pattern, including a finalizer, so that the runtime can call both the EndProcessing and [System.IDisposable.Dispose](/dotnet/api/System.IDisposable.Dispose) methods at the end of processing.</span></span>
<span data-ttu-id="2a6e6-123">Weitere Informationen dazu, wie PowerShell die Befehlspipeline aufruft, finden Sie unter [Cmdlet Verarbeitung Lebenszyklus](/previous-versions/ms714429(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="2a6e6-123">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="2a6e6-124">Der folgende Code zeigt eine Implementierung der EndProcessing-Methode.</span><span class="sxs-lookup"><span data-stu-id="2a6e6-124">The following code shows an implementation of the EndProcessing method.</span></span>

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the EndProcessing template.");
}
```

## <a name="see-also"></a><span data-ttu-id="2a6e6-125">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="2a6e6-125">See Also</span></span>

[<span data-ttu-id="2a6e6-126">System.Management.Automation.Cmdlet.BeginProcessing</span><span class="sxs-lookup"><span data-stu-id="2a6e6-126">System.Management.Automation.Cmdlet.BeginProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="2a6e6-127">System.Management.Automation.Cmdlet.ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="2a6e6-127">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="2a6e6-128">System.Management.Automation.Cmdlet.EndProcessing</span><span class="sxs-lookup"><span data-stu-id="2a6e6-128">System.Management.Automation.Cmdlet.EndProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="2a6e6-129">SelectStr-Tutorial</span><span class="sxs-lookup"><span data-stu-id="2a6e6-129">SelectStr Tutorial</span></span>](selectstr-tutorial.md)

[<span data-ttu-id="2a6e6-130">System.IDisposable</span><span class="sxs-lookup"><span data-stu-id="2a6e6-130">System.IDisposable</span></span>](/dotnet/api/System.IDisposable)

[<span data-ttu-id="2a6e6-131">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="2a6e6-131">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
