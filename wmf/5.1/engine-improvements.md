---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
title: Verbesserungen am PowerShell-Modul in WMF 5.1
ms.openlocfilehash: 6c8000ccfc59ab46de95dc4f67161e12a5a41199
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
#<a name="powershell-engine-improvements"></a><span data-ttu-id="17524-103">Verbesserungen am PowerShell-Modul</span><span class="sxs-lookup"><span data-stu-id="17524-103">PowerShell Engine Improvements</span></span>

<span data-ttu-id="17524-104">Die folgenden Verbesserungen am PowerShell-Kernmodul wurden in WMF 5.1 implementiert:</span><span class="sxs-lookup"><span data-stu-id="17524-104">The following improvements to the core PowerShell engine have been implemented in WMF 5.1:</span></span>


## <a name="performance"></a><span data-ttu-id="17524-105">Leistung</span><span class="sxs-lookup"><span data-stu-id="17524-105">Performance</span></span> ##

<span data-ttu-id="17524-106">In einigen wichtigen Bereichen wurde die Leistung verbessert:</span><span class="sxs-lookup"><span data-stu-id="17524-106">Performance has improved in some important areas:</span></span>

- <span data-ttu-id="17524-107">Start</span><span class="sxs-lookup"><span data-stu-id="17524-107">Startup</span></span>
- <span data-ttu-id="17524-108">Das Pipelining zu Cmdlets wie „ForEach-Object“ und „Where-Object“ erfolgt ca. 50 % schneller.</span><span class="sxs-lookup"><span data-stu-id="17524-108">Pipelining to cmdlets like ForEach-Object and Where-Object is approximately 50% faster</span></span> 

<span data-ttu-id="17524-109">Einige Beispiele für Verbesserungen (die Ergebnisse variieren je nach Hardware):</span><span class="sxs-lookup"><span data-stu-id="17524-109">Some example improvements (your results may vary depending on your hardware):</span></span> 

| <span data-ttu-id="17524-110">Szenario</span><span class="sxs-lookup"><span data-stu-id="17524-110">Scenario</span></span> | <span data-ttu-id="17524-111">Zeit (ms) in 5.0</span><span class="sxs-lookup"><span data-stu-id="17524-111">5.0 Time (ms)</span></span> | <span data-ttu-id="17524-112">Zeit (ms) in 5.1</span><span class="sxs-lookup"><span data-stu-id="17524-112">5.1 Time (ms)</span></span> |
| -------- | :---------------: | :---------------: |
| `powershell -command "echo 1"` | <span data-ttu-id="17524-113">900</span><span class="sxs-lookup"><span data-stu-id="17524-113">900</span></span> | <span data-ttu-id="17524-114">250</span><span class="sxs-lookup"><span data-stu-id="17524-114">250</span></span> |
| <span data-ttu-id="17524-115">Erste Ausführung von PowerShell überhaupt: `powershell -command "Unknown-Command"`</span><span class="sxs-lookup"><span data-stu-id="17524-115">First ever PowerShell run: `powershell -command "Unknown-Command"`</span></span> | <span data-ttu-id="17524-116">30.000</span><span class="sxs-lookup"><span data-stu-id="17524-116">30000</span></span> | <span data-ttu-id="17524-117">13.000</span><span class="sxs-lookup"><span data-stu-id="17524-117">13000</span></span> |
| <span data-ttu-id="17524-118">Erstellung des Caches für die Befehlsanalyse: `powershell -command "Unknown-Command"`</span><span class="sxs-lookup"><span data-stu-id="17524-118">Command analysis cache built: `powershell -command "Unknown-Command"`</span></span> | <span data-ttu-id="17524-119">7000</span><span class="sxs-lookup"><span data-stu-id="17524-119">7000</span></span> | <span data-ttu-id="17524-120">520</span><span class="sxs-lookup"><span data-stu-id="17524-120">520</span></span> |
| <code>1..1000000 &#124; % { }</code> | <span data-ttu-id="17524-121">1400</span><span class="sxs-lookup"><span data-stu-id="17524-121">1400</span></span> | <span data-ttu-id="17524-122">750</span><span class="sxs-lookup"><span data-stu-id="17524-122">750</span></span> |
  
> <span data-ttu-id="17524-123">Hinweis: Eine Änderung im Zusammenhang mit dem Start kann sich möglicherweise auf einige (nicht unterstützte) Szenarien auswirken.</span><span class="sxs-lookup"><span data-stu-id="17524-123">Note One change related to startup might impact some unsupported scenarios.</span></span> 
> <span data-ttu-id="17524-124">PowerShell liest nicht mehr die Dateien des Typs `$pshome\*.ps1xml`. Diese Dateien wurden in C# konvertiert, um den Datei- und CPU-Overhead beim Verarbeiten der XML-Dateien zu reduzieren.</span><span class="sxs-lookup"><span data-stu-id="17524-124">PowerShell no longer reads the files `$pshome\*.ps1xml` -- these files have been converted to C# to avoid some file and CPU overhead of processing the XML files.</span></span> 
<span data-ttu-id="17524-125">Die Dateien sind zur Unterstützung der parallelen Verwendung von Version 2 noch vorhanden. Wenn Sie also den Inhalt der Dateien ändern, hat dies keine Auswirkung auf Version 5, sondern nur auf Version 2.</span><span class="sxs-lookup"><span data-stu-id="17524-125">The files still exist to support V2 side-by-side, so if you change the file contents, it will not have any effect to V5, only V2.</span></span> 
<span data-ttu-id="17524-126">Beachten Sie, dass das Ändern dieser Dateien zu keiner Zeit ein unterstütztes Szenario war.</span><span class="sxs-lookup"><span data-stu-id="17524-126">Note that changing the contents of these files was never a supported scenario.</span></span>

<span data-ttu-id="17524-127">Eine andere sichtbare Änderung ist, wie PowerShell die exportierten Befehle und andere Informationen für Module zwischenspeichert, die auf einem System installiert sind.</span><span class="sxs-lookup"><span data-stu-id="17524-127">Another visible change is how PowerShell caches the exported commands and other information for modules that are installed on a system.</span></span> <span data-ttu-id="17524-128">Zuvor wurde dieser Cache im Verzeichnis `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis` gespeichert.</span><span class="sxs-lookup"><span data-stu-id="17524-128">Previously, this cache was stored in the directory `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`.</span></span> <span data-ttu-id="17524-129">In WMF 5.1 befindet sich der Cache ausschließlich in der Datei `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span><span class="sxs-lookup"><span data-stu-id="17524-129">In WMF 5.1, the cache is a single file `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span></span>
<span data-ttu-id="17524-130">Unter [Die Datei „ModuleAnalysisCache“](scenarios-features.md#module-analysis-cache) finden Sie weitere Details.</span><span class="sxs-lookup"><span data-stu-id="17524-130">See [Module Analysis Cache](scenarios-features.md#module-analysis-cache) for more details.</span></span>

