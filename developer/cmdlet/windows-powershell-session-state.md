---
title: Windows PowerShell-Sitzungsstatus | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Cmdlets [PowerShell], session state
- session state [PowerShell]
ms.assetid: 74912940-2b10-4a76-b174-6d035d71c02b
caps.latest.revision: 8
ms.openlocfilehash: fa207130bbb120750780bb0aa9b32150a32daaa2
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059540"
---
# <a name="windows-powershell-session-state"></a><span data-ttu-id="a8ece-102">Windows PowerShell-Sitzungszustand</span><span class="sxs-lookup"><span data-stu-id="a8ece-102">Windows PowerShell Session State</span></span>

<span data-ttu-id="a8ece-103">Sitzungsstatus bezieht sich auf die aktuelle Konfiguration einer Windows PowerShell-Sitzung oder dieses Moduls.</span><span class="sxs-lookup"><span data-stu-id="a8ece-103">Session state refers to the current configuration of a Windows PowerShell session or module.</span></span> <span data-ttu-id="a8ece-104">Eine Windows PowerShell-Sitzung ist die betriebsumgebung, die interaktiv vom Benutzer Befehlszeile oder programmgesteuert von einer hostanwendung verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="a8ece-104">A Windows PowerShell session is the operational environment that is used interactively by the command-line user or programmatically by a host application.</span></span> <span data-ttu-id="a8ece-105">Der Sitzungszustand für eine Sitzung wird als den globalen Sitzungsstatus bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="a8ece-105">The session state for a session is referred to as the global session state.</span></span>

<span data-ttu-id="a8ece-106">Bezieht sich aus Sicht eines Entwicklers bietet eine Windows PowerShell-Sitzung auf den Zeitraum zwischen, wenn eine hostanwendung mit einen Windows PowerShell-Runspace geöffnet wird und wenn den Runspace geschlossen wird.</span><span class="sxs-lookup"><span data-stu-id="a8ece-106">From a developer perspective, a Windows PowerShell session refers to the time between when a host application opens a Windows PowerShell runspace and when it closes the runspace.</span></span> <span data-ttu-id="a8ece-107">Eine andere Möglichkeit haben, ist die Sitzung der Lebensdauer einer Instanz von der Windows PowerShell-Engine, die aufgerufen wird, während die Runspace vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="a8ece-107">Looked at another way, the session is the lifetime of an instance of the Windows PowerShell engine that is invoked while the runspace exists.</span></span>

## <a name="module-session-state"></a><span data-ttu-id="a8ece-108">Modulsitzungsstatus</span><span class="sxs-lookup"><span data-stu-id="a8ece-108">Module Session State</span></span>

<span data-ttu-id="a8ece-109">Sitzungsstatus des Moduls werden erstellt, wenn das Modul oder eines seiner geschachtelten Module in die Sitzung importiert wird.</span><span class="sxs-lookup"><span data-stu-id="a8ece-109">Module session states are created whenever the module or one of its nested modules is imported into the session.</span></span> <span data-ttu-id="a8ece-110">Wenn ein Modul ein Element wie ein Cmdlet, Funktion oder Skript exportiert, wird ein Verweis auf dieses Element den globalen Sitzungsstatus der Sitzung hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="a8ece-110">When a module exports an element such as a cmdlet, function, or script, a reference to that element is added to the global session state of the session.</span></span> <span data-ttu-id="a8ece-111">Wenn das Element ausgeführt wird, wird es jedoch in den Sitzungsstatus des Moduls ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="a8ece-111">However, when the element is run, it is executed within the session state of the module.</span></span>

## <a name="session-state-data"></a><span data-ttu-id="a8ece-112">Sitzungszustandsdaten</span><span class="sxs-lookup"><span data-stu-id="a8ece-112">Session-State Data</span></span>

<span data-ttu-id="a8ece-113">Sitzungszustandsdaten können öffentlich oder privat sein.</span><span class="sxs-lookup"><span data-stu-id="a8ece-113">Session state data can be public or private.</span></span> <span data-ttu-id="a8ece-114">Öffentliche Daten ist für Aufrufe von außerhalb der Sitzungszustand verfügbar, während private Daten nur auf Aufrufe von innerhalb der Sitzungsstatus zur Verfügung steht.</span><span class="sxs-lookup"><span data-stu-id="a8ece-114">Public data is available to calls from outside the session state while private data is available only to calls from within the session state.</span></span> <span data-ttu-id="a8ece-115">Ein Modul kann z. B. eine private Funktion, die nur durch das Modul oder nur intern aufgerufen werden, enthält ein öffentlich-Element, die exportiert wurde.</span><span class="sxs-lookup"><span data-stu-id="a8ece-115">For example, a module can have a private function that can be called only by the module or only internally by a public element that has been exported.</span></span> <span data-ttu-id="a8ece-116">Dies ist ähnlich wie die öffentlichen und privaten Member von .NET Framework-Typ.</span><span class="sxs-lookup"><span data-stu-id="a8ece-116">This is similar to the private and public members of a .NET Framework type.</span></span>

<span data-ttu-id="a8ece-117">Sitzungszustandsdaten werden von der aktuellen Instanz von der ausführungs-Engine innerhalb des Kontexts der aktuellen Windows PowerShell-Sitzung gespeichert.</span><span class="sxs-lookup"><span data-stu-id="a8ece-117">Session-state data is stored by the current instance of the execution engine within the context of the current Windows PowerShell session.</span></span> <span data-ttu-id="a8ece-118">Sitzungszustandsdaten besteht aus den folgenden Elementen:</span><span class="sxs-lookup"><span data-stu-id="a8ece-118">Session-state data consists of the following items:</span></span>

- <span data-ttu-id="a8ece-119">Informationen über Pfade</span><span class="sxs-lookup"><span data-stu-id="a8ece-119">Path information</span></span>

- <span data-ttu-id="a8ece-120">Informationen zum Laufwerk</span><span class="sxs-lookup"><span data-stu-id="a8ece-120">Drive information</span></span>

- <span data-ttu-id="a8ece-121">Windows PowerShell-Anbieterinformationen</span><span class="sxs-lookup"><span data-stu-id="a8ece-121">Windows PowerShell provider information</span></span>

- <span data-ttu-id="a8ece-122">Informationen zu den importierten Module und die Verweise auf die Modul-Elemente (z. B. Cmdlets, Funktionen und Skripts), die vom Modul exportiert werden.</span><span class="sxs-lookup"><span data-stu-id="a8ece-122">Information about the imported modules and references to the module elements (such as cmdlets, functions, and scripts) that are exported by the module.</span></span> <span data-ttu-id="a8ece-123">Diese Informationen und diese Verweise sind für nur den globalen Sitzungsstatus.</span><span class="sxs-lookup"><span data-stu-id="a8ece-123">This information and these references are for the global session state only.</span></span>

- <span data-ttu-id="a8ece-124">Variablen der Sitzungszustandsinformationen</span><span class="sxs-lookup"><span data-stu-id="a8ece-124">Session-state variable information</span></span>

## <a name="accessing-session-state-data-within-cmdlets"></a><span data-ttu-id="a8ece-125">Zugriff auf Sitzungszustandsdaten in Cmdlets</span><span class="sxs-lookup"><span data-stu-id="a8ece-125">Accessing Session-State Data Within Cmdlets</span></span>

<span data-ttu-id="a8ece-126">Cmdlets können Zugriff auf Sitzungszustandsdaten entweder indirekt über die [System.Management.Automation.PSCmdlet.Sessionstate\*](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState) Eigenschaft, die von der Cmdlet-Klasse oder direkt über die [ System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) Klasse.</span><span class="sxs-lookup"><span data-stu-id="a8ece-126">Cmdlets can access session-state data either indirectly through the [System.Management.Automation.PSCmdlet.Sessionstate\*](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState) property of the cmdlet class or directly through the [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) class.</span></span> <span data-ttu-id="a8ece-127">Die [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) Klasse enthält Eigenschaften, die verwendet werden können, um verschiedene Arten von Sitzungszustandsdaten zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="a8ece-127">The [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) class provides properties that can be used to investigate different types of session-state data.</span></span>

## <a name="see-also"></a><span data-ttu-id="a8ece-128">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="a8ece-128">See Also</span></span>

[<span data-ttu-id="a8ece-129">System.Management.Automation.PSCmdlet.Sessionstate</span><span class="sxs-lookup"><span data-stu-id="a8ece-129">System.Management.Automation.PSCmdlet.Sessionstate</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState)

[<span data-ttu-id="a8ece-130">System.Management.Automation.Sessionstate?Displayproperty=Fullname</span><span class="sxs-lookup"><span data-stu-id="a8ece-130">System.Management.Automation.Sessionstate?Displayproperty=Fullname</span></span>](/dotnet/api/System.Management.Automation.SessionState)

[<span data-ttu-id="a8ece-131">Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="a8ece-131">Windows PowerShell Cmdlets</span></span>](./cmdlet-overview.md)

[<span data-ttu-id="a8ece-132">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="a8ece-132">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="a8ece-133">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="a8ece-133">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
