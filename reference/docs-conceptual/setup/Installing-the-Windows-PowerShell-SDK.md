---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Installieren das Windows PowerShell SDK
ms.assetid: c3636b45-61aa-4720-85f0-58312c4fc8f9
ms.openlocfilehash: c6acba828e469e716c80603ec2432176652a7280
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2017
---
# <a name="installing-the-windows-powershell-sdk"></a><span data-ttu-id="0481c-103">Installieren das Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="0481c-103">Installing the Windows PowerShell SDK</span></span>

<span data-ttu-id="0481c-104">Das folgende Thema beschreibt, wie das PowerShell SDK in verschiedenen Versionen von Windows installiert wird.</span><span class="sxs-lookup"><span data-stu-id="0481c-104">The following topic describes how to install the PowerShell SDK on different versions of Windows.</span></span>

## <a name="installing-windows-powershell-30-sdk-for-windows-8-and-windows-server-2012"></a><span data-ttu-id="0481c-105">Installieren des Windows PowerShell 3.0 SDK für Windows 8 und Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="0481c-105">Installing Windows PowerShell 3.0 SDK for Windows 8 and Windows Server 2012</span></span>

<span data-ttu-id="0481c-106">Windows PowerShell 3.0 wird automatisch mit Windows 8 und Windows Server 2012 installiert.</span><span class="sxs-lookup"><span data-stu-id="0481c-106">Windows PowerShell 3.0 is automatically installed with Windows 8 and Windows Server 2012.</span></span>
<span data-ttu-id="0481c-107">Darüber hinaus können Sie die Verweisassemblys für Windows PowerShell 3.0 als Teil des Windows 8 SDKs herunterladen und installieren.</span><span class="sxs-lookup"><span data-stu-id="0481c-107">In addition, you can download and install the reference assemblies for Windows PowerShell 3.0 as part of the Windows 8 SDK.</span></span>
<span data-ttu-id="0481c-108">Diese Assemblys ermöglichen Ihnen das Schreiben von Cmdlets, Anbietern und Host-Programmen für Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="0481c-108">These assemblies allow you to write cmdlets, providers, and host programs for Windows PowerShell 3.0.</span></span>
<span data-ttu-id="0481c-109">Wenn Sie das Windows SDK für Windows 8 installieren, werden die Windows PowerShell-Assemblys im Ordner „Verweisassembly“ unter „\Programme (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0“ automatisch installiert.</span><span class="sxs-lookup"><span data-stu-id="0481c-109">When you install the Windows SDK for Windows 8, the Windows PowerShell assemblies are automatically installed in the reference assembly folder, in \Program Files (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0.</span></span>
<span data-ttu-id="0481c-110">Weitere Informationen finden Sie auf der [Windows 8 SDK-Downloadwebsite](http://msdn.microsoft.com/windows/hardware/hh852363.aspx).</span><span class="sxs-lookup"><span data-stu-id="0481c-110">For more information, see the [Windows 8 SDK download site](http://msdn.microsoft.com/windows/hardware/hh852363.aspx).</span></span>
<span data-ttu-id="0481c-111">Codebeispiele für Windows PowerShell stehen ebenfalls im Dev Center zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="0481c-111">Windows PowerShell code samples are also available on the Development Center.</span></span>
<span data-ttu-id="0481c-112">Weitere Informationen finden Sie auf der Seite mit Desktop-Codebeispielen auf der [Dev Center-Website](http://code.msdn.microsoft.com/windowsdesktop/).</span><span class="sxs-lookup"><span data-stu-id="0481c-112">For more information, see the Desktop code sample page on the [Dev center site](http://code.msdn.microsoft.com/windowsdesktop/).</span></span>

<span data-ttu-id="0481c-113">Darüber hinaus ist Windows PowerShell 3.0 abwärtskompatibel mit dem Windows PowerShell 2.0 SDK, das eine Reihe von Codebeispielen enthält.</span><span class="sxs-lookup"><span data-stu-id="0481c-113">In addition, Windows PowerShell 3.0 is backwards-compatible with the Windows PowerShell 2.0 SDK, which includes a number of code samples.</span></span>
<span data-ttu-id="0481c-114">Weitere Informationen zum Herunterladen des Windows PowerShell 2.0 SDKs finden Sie nachstehend.</span><span class="sxs-lookup"><span data-stu-id="0481c-114">For more information on how to download the Windows PowerShell 2.0 SDK, see below.</span></span>
<span data-ttu-id="0481c-115">(Beachten Sie, dass, während die 2.0-Codebeispiele mit Windows 8 und Windows PowerShell 3.0 kompatibel sind, Sie Windows PowerShell 2.0 auf einer Windows 8-Plattform nicht installieren können.)</span><span class="sxs-lookup"><span data-stu-id="0481c-115">(Note that while the 2.0 code samples are compatible with Windows 8 and Windows PowerShell 3.0, you cannot install Windows PowerShell 2.0 on a Windows 8 platform.)</span></span>

##<a name="installing-windows-powershell-30-sdk-for-windows-7-and-windows-server-2008-r2"></a><span data-ttu-id="0481c-116">Installieren des Windows PowerShell 3.0 SDK für Windows 7 und Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="0481c-116">Installing Windows PowerShell 3.0 SDK for Windows 7 and Windows Server 2008 R2</span></span>

<span data-ttu-id="0481c-117">Bei Windows 7 und Windows Server 2008 R2 wird PowerShell 2.0 automatisch installiert.</span><span class="sxs-lookup"><span data-stu-id="0481c-117">Windows 7 and Windows Server 2008 R2 automatically have PowerShell 2.0 installed.</span></span>
<span data-ttu-id="0481c-118">Darüber hinaus können Sie PowerShell 3.0 auf diesen Systemen installieren.</span><span class="sxs-lookup"><span data-stu-id="0481c-118">In addition, you can install PowerShell 3.0 on these systems.</span></span>
<span data-ttu-id="0481c-119">(Weitere Informationen finden Sie unter [Installieren von Windows PowerShell](Installing-Windows-PowerShell.md).)</span><span class="sxs-lookup"><span data-stu-id="0481c-119">(For more information, see [Installing Windows PowerShell](Installing-Windows-PowerShell.md).).</span></span>
<span data-ttu-id="0481c-120">Wie oben beschrieben, können Sie das Windows 8 SDK auch unter Windows 7 und Windows Server 2008 R2 installieren.</span><span class="sxs-lookup"><span data-stu-id="0481c-120">As described above, you can also install the Windows 8 SDK on Windows 7 and Windows Server 2008 R2.</span></span>

## <a name="installing-windows-powershell-20-sdk-for-windows-7-vista-xp-server-2003-and-server-2008"></a><span data-ttu-id="0481c-121">Installieren des Windows PowerShell 2.0 SDK für Windows 7, Vista, XP, Server 2003 und Server 2008</span><span class="sxs-lookup"><span data-stu-id="0481c-121">Installing Windows PowerShell 2.0 SDK for Windows 7, Vista, XP, Server 2003, and Server 2008</span></span>

<span data-ttu-id="0481c-122">Das Windows PowerShell 2.0 SDK stellt die Verweisassemblys bereit, die zum Schreiben von Cmdlets, Anbietern und Hostinganwendungen erforderlich sind, und bietet C#-Beispielcode, der als Ausgangspunkt dienen kann, wenn Sie mit dem Schreiben von Code beginnen.</span><span class="sxs-lookup"><span data-stu-id="0481c-122">The Windows PowerShell 2.0 SDK provides the reference assemblies needed to write cmdlets, providers, and hosting applications, and it provides C# sample code that can be used as the starting point when you begin writing code.</span></span>

<span data-ttu-id="0481c-123">Informationen zur Installation dieses SDK finden Sie unter [Windows PowerShell 2.0 SDK](http://go.microsoft.com/fwlink/?LinkId=184611).</span><span class="sxs-lookup"><span data-stu-id="0481c-123">To install this SDK, see [Windows PowerShell 2.0 SDK](http://go.microsoft.com/fwlink/?LinkId=184611).</span></span>

## <a name="reference-assemblies"></a><span data-ttu-id="0481c-124">Verweisassemblys</span><span class="sxs-lookup"><span data-stu-id="0481c-124">Reference assemblies</span></span>

<span data-ttu-id="0481c-125">Verweisassemblys werden standardmäßig an folgendem Speicherort installiert: `c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0`.</span><span class="sxs-lookup"><span data-stu-id="0481c-125">Reference assemblies are installed in the following location by default: `c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0`.</span></span>

> <span data-ttu-id="0481c-126">**Hinweis**: Code, der für die Windows PowerShell 2.0-Assemblys kompiliert wird, kann nicht in Windows PowerShell 1.0-Installationen geladen werden.</span><span class="sxs-lookup"><span data-stu-id="0481c-126">**Note**: Code that is compiled against the Windows PowerShell 2.0 assemblies cannot be loaded into Windows PowerShell 1.0 installations.</span></span>
><span data-ttu-id="0481c-127">Jedoch kann Code, der für die Windows PowerShell 1.0-Assemblys kompiliert wird, in Windows PowerShell 2.0-Installationen geladen werden.</span><span class="sxs-lookup"><span data-stu-id="0481c-127">However, code that is compiled against the Windows PowerShell 1.0 assemblies can be loaded into Windows PowerShell 2.0 installations.</span></span>

## <a name="samples"></a><span data-ttu-id="0481c-128">Beispiele</span><span class="sxs-lookup"><span data-stu-id="0481c-128">Samples</span></span>

<span data-ttu-id="0481c-129">Codebeispiele werden standardmäßig an folgendem Speicherort installiert: `C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`.</span><span class="sxs-lookup"><span data-stu-id="0481c-129">Code samples are installed in the following location by default: `C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`.</span></span>

<span data-ttu-id="0481c-130">Die folgenden Abschnitte enthalten eine kurze Beschreibung der einzelnen Beispiele.</span><span class="sxs-lookup"><span data-stu-id="0481c-130">The following sections provide a brief description of what each sample does.</span></span>

## <a name="cmdlet-samples"></a><span data-ttu-id="0481c-131">Cmdlet-Beispiele</span><span class="sxs-lookup"><span data-stu-id="0481c-131">Cmdlet samples</span></span>
<span data-ttu-id="0481c-132">**GetProcessSample01**</span><span class="sxs-lookup"><span data-stu-id="0481c-132">**GetProcessSample01**</span></span>

<span data-ttu-id="0481c-133">Zeigt, wie Sie ein einfaches Cmdlet schreiben, das alle Prozesse auf dem lokalen Computer abruft.</span><span class="sxs-lookup"><span data-stu-id="0481c-133">Shows how to write a simple cmdlet that gets all the processes on the local computer.</span></span>

<span data-ttu-id="0481c-134">**GetProcessSample02**</span><span class="sxs-lookup"><span data-stu-id="0481c-134">**GetProcessSample02**</span></span>

<span data-ttu-id="0481c-135">Zeigt, wie dem Cmdlet Parameter hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="0481c-135">Shows how to add parameters to the cmdlet.</span></span>
<span data-ttu-id="0481c-136">Das Cmdlet akzeptiert einen oder mehrere Prozessnamen und gibt die entsprechenden Prozesse zurück.</span><span class="sxs-lookup"><span data-stu-id="0481c-136">The cmdlet takes one or more process names and returns the matching processes.</span></span>

<span data-ttu-id="0481c-137">**GetProcessSample03**</span><span class="sxs-lookup"><span data-stu-id="0481c-137">**GetProcessSample03**</span></span>

<span data-ttu-id="0481c-138">Zeigt, wie Sie Parameter hinzufügen, die Eingaben aus der Pipeline akzeptieren.</span><span class="sxs-lookup"><span data-stu-id="0481c-138">Shows how to add parameters that accept input from the pipeline.</span></span>

<span data-ttu-id="0481c-139">**GetProcessSample04**</span><span class="sxs-lookup"><span data-stu-id="0481c-139">**GetProcessSample04**</span></span>

<span data-ttu-id="0481c-140">Zeigt, wie Fehler ohne Abbruch behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="0481c-140">Shows how to handle nonterminating errors.</span></span>

<span data-ttu-id="0481c-141">**GetProcessSample05**</span><span class="sxs-lookup"><span data-stu-id="0481c-141">**GetProcessSample05**</span></span>

<span data-ttu-id="0481c-142">Zeigt, wie eine Liste der angegebenen Prozesse angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="0481c-142">Shows how to display a list of specified processes.</span></span>

<span data-ttu-id="0481c-143">**SelectObject**</span><span class="sxs-lookup"><span data-stu-id="0481c-143">**SelectObject**</span></span>

<span data-ttu-id="0481c-144">Zeigt das Schreiben eines Filters, um nur bestimmte Objekte auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="0481c-144">Shows how to write a filter to select only certain objects.</span></span>

<span data-ttu-id="0481c-145">**SelectString**</span><span class="sxs-lookup"><span data-stu-id="0481c-145">**SelectString**</span></span>

<span data-ttu-id="0481c-146">Zeigt, wie Dateien nach angegebenen Mustern durchsucht werden.</span><span class="sxs-lookup"><span data-stu-id="0481c-146">Shows how to search files for specified patterns.</span></span>

<span data-ttu-id="0481c-147">**StopProcessSample01**</span><span class="sxs-lookup"><span data-stu-id="0481c-147">**StopProcessSample01**</span></span>

<span data-ttu-id="0481c-148">Zeigt das Implementieren eines *PassThru*-Parameters und das Anfordern von Benutzerfeedback durch Aufrufe der Methoden [ShouldProcess](https://technet.microsoft.com/library/system.management.automation.cmdlet.shouldprocess.aspx) und [ShouldContinue](https://technet.microsoft.com/library/system.management.automation.cmdlet.shouldcontinue.aspx).</span><span class="sxs-lookup"><span data-stu-id="0481c-148">Shows how to implement a *PassThru* parameter, and how to request user feedback by calls to the [ShouldProcess](https://technet.microsoft.com/library/system.management.automation.cmdlet.shouldprocess.aspx) and [ShouldContinue](https://technet.microsoft.com/library/system.management.automation.cmdlet.shouldcontinue.aspx) methods.</span></span>
<span data-ttu-id="0481c-149">Benutzer geben den Parameter *PassThru* an, wenn sie erzwingen möchten, dass das Cmdlet ein Objekt zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="0481c-149">Users specify the *PassThru* parameter when they want to force the cmdlet to return an object,</span></span>

<span data-ttu-id="0481c-150">**StopProcessSample02**</span><span class="sxs-lookup"><span data-stu-id="0481c-150">**StopProcessSample02**</span></span>

<span data-ttu-id="0481c-151">Zeigt, wie ein bestimmter Prozess beendet wird.</span><span class="sxs-lookup"><span data-stu-id="0481c-151">Shows how to stop a specific process.</span></span>

<span data-ttu-id="0481c-152">**StopProcessSample03**</span><span class="sxs-lookup"><span data-stu-id="0481c-152">**StopProcessSample03**</span></span>

<span data-ttu-id="0481c-153">Zeigt, wie Aliase für Parameter deklariert und Platzhalter unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="0481c-153">Shows how to declare aliases for parameters and how to support wildcards.</span></span>

<span data-ttu-id="0481c-154">**StopProcessSample04**</span><span class="sxs-lookup"><span data-stu-id="0481c-154">**StopProcessSample04**</span></span>

<span data-ttu-id="0481c-155">Zeigt die Deklaration von Parametersätzen, das Objekt, das vom Cmdlet als Eingabe akzeptiert wird, und die Angabe des zu verwendenden Standardparametersatzes.</span><span class="sxs-lookup"><span data-stu-id="0481c-155">Shows how to declare parameter sets, the object that the cmdlet takes as input, and how to specify the default parameter set to use.</span></span>

## <a name="remoting-samples"></a><span data-ttu-id="0481c-156">Remotingbeispiele</span><span class="sxs-lookup"><span data-stu-id="0481c-156">Remoting samples</span></span>

<span data-ttu-id="0481c-157">**RemoteRunspace01**</span><span class="sxs-lookup"><span data-stu-id="0481c-157">**RemoteRunspace01**</span></span>

<span data-ttu-id="0481c-158">Zeigt, wie Sie einen Remoterunspace erstellen, der zum Herstellen einer Remoteverbindung verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="0481c-158">Shows how to create a remote runspace that is used to establish a remote connection.</span></span>

<span data-ttu-id="0481c-159">**RemoteRunspacePool01**</span><span class="sxs-lookup"><span data-stu-id="0481c-159">**RemoteRunspacePool01**</span></span>

<span data-ttu-id="0481c-160">Zeigt, wie Sie einen Remoterunspace-Pool erstellen und anhand dieses Pools mehrere Befehle gleichzeitig ausführen.</span><span class="sxs-lookup"><span data-stu-id="0481c-160">Shows how to construct a remote runspace pool and how to run multiple commands concurrently by using this pool.</span></span>

<span data-ttu-id="0481c-161">**Serialization01**</span><span class="sxs-lookup"><span data-stu-id="0481c-161">**Serialization01**</span></span>

<span data-ttu-id="0481c-162">Zeigt, wie Sie eine vorhandene .NET-Klasse anzeigen und sicherstellen, dass Informationen von ausgewählten öffentlichen Eigenschaften dieser Klasse über die Serialisierung/Deserialisierung hinweg beibehalten werden.</span><span class="sxs-lookup"><span data-stu-id="0481c-162">Shows how to look at an existing .NET class and make sure that information from selected public properties of this class is preserved across serialization/deserialization.</span></span>

<span data-ttu-id="0481c-163">**Serialization02**</span><span class="sxs-lookup"><span data-stu-id="0481c-163">**Serialization02**</span></span>

<span data-ttu-id="0481c-164">Zeigt, wie Sie eine vorhandene .NET-Klasse anzeigen und sicherstellen, dass Informationen von Instanzen aus dieser Klasse über die Serialisierung/Deserialisierung hinweg beibehalten werden, wenn die Informationen nicht in öffentlichen Eigenschaften dieser Klasse verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="0481c-164">Shows how to look at an existing .NET class and make sure that information from instance of this class is preserved across serialization/deserialization when the information is not available in public properties of the class.</span></span>

<span data-ttu-id="0481c-165">**Serialization03**</span><span class="sxs-lookup"><span data-stu-id="0481c-165">**Serialization03**</span></span>

<span data-ttu-id="0481c-166">Zeigt, wie Sie eine vorhandene .NET-Klasse anzeigen und sicherstellen, dass Instanzen dieser Klasse und von abgeleiteten Klassen in aktive .NET-Objekte deserialisiert (aktiviert) werden.</span><span class="sxs-lookup"><span data-stu-id="0481c-166">Shows how to look at an existing .NET class and make sure that instances of this class and of derived classes are deserialized (rehydrated) into live .NET objects.</span></span>

## <a name="event-samples"></a><span data-ttu-id="0481c-167">Ereignisbeispiele</span><span class="sxs-lookup"><span data-stu-id="0481c-167">Event samples</span></span>

<span data-ttu-id="0481c-168">**Event01**</span><span class="sxs-lookup"><span data-stu-id="0481c-168">**Event01**</span></span>

<span data-ttu-id="0481c-169">Zeigt, wie Sie ein Cmdlet für die Ereignisregistrierung durch Ableiten von ObjectEventRegistrationBase erstellen.</span><span class="sxs-lookup"><span data-stu-id="0481c-169">Shows how to create a cmdlet for event registration by deriving from ObjectEventRegistrationBase.</span></span>

<span data-ttu-id="0481c-170">**Event02**</span><span class="sxs-lookup"><span data-stu-id="0481c-170">**Event02**</span></span>

<span data-ttu-id="0481c-171">Zeigt, wie Sie Benachrichtigungen von Windows PowerShell-Ereignissen empfangen, die auf Remotecomputern generiert werden.</span><span class="sxs-lookup"><span data-stu-id="0481c-171">Shows how to shows how to receive notifications of Windows PowerShell events that are generated on remote computers.</span></span>
<span data-ttu-id="0481c-172">Verwendet das über die [Runspace](https://technet.microsoft.com/library/system.management.automation.runspaces.runspace.aspx)-Klasse offen gelegte PSEventReceived-Ereignis.</span><span class="sxs-lookup"><span data-stu-id="0481c-172">It uses the PSEventReceived event exposed through the [Runspace](https://technet.microsoft.com/library/system.management.automation.runspaces.runspace.aspx) class.</span></span>

## <a name="hosting-application-samples"></a><span data-ttu-id="0481c-173">Hosten von Anwendungsbeispielen</span><span class="sxs-lookup"><span data-stu-id="0481c-173">Hosting application samples</span></span>

<span data-ttu-id="0481c-174">**Runspace01**</span><span class="sxs-lookup"><span data-stu-id="0481c-174">**Runspace01**</span></span>

<span data-ttu-id="0481c-175">Zeigt, wie Sie die [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx)-Klasse zum synchronen Ausführen des Cmdlets [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) verwenden.</span><span class="sxs-lookup"><span data-stu-id="0481c-175">Shows how to use the [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) class to run the [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet synchronously.</span></span>
<span data-ttu-id="0481c-176">Das Cmdlet [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) gibt [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx)-Objekte für jeden Prozess zurück, der auf dem lokalen Computer ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="0481c-176">The [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet returns [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) objects for each process running on the local computer.</span></span>

<span data-ttu-id="0481c-177">**Runspace02**</span><span class="sxs-lookup"><span data-stu-id="0481c-177">**Runspace02**</span></span>

<span data-ttu-id="0481c-178">Zeigt, wie Sie die [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx)-Klasse zum synchronen Ausführen der Cmdlets [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) und [Sort-Object](http://go.microsoft.com/fwlink/?LinkID=113403) verwenden.</span><span class="sxs-lookup"><span data-stu-id="0481c-178">Shows how to use the [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) class to run the [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) and [Sort-Object](http://go.microsoft.com/fwlink/?LinkID=113403) cmdlets synchronously.</span></span>
<span data-ttu-id="0481c-179">Das Cmdlet [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) gibt [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx)-Objekte für jeden Prozess zurück, der auf dem lokalen Computer ausgeführt wird, und das Cmdlet „Sort-Object“ sortiert die Objekte basierend auf ihrer [Id](https://technet.microsoft.com/library/system.diagnostics.process.id.aspx)-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="0481c-179">The [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet returns [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) objects for each process running on the local computer, and the Sort-Object sorts the objects based on their [Id](https://technet.microsoft.com/library/system.diagnostics.process.id.aspx) property.</span></span>
<span data-ttu-id="0481c-180">Die Ergebnisse dieser Befehle werden anhand des Steuerelements [DataGridView](https://technet.microsoft.com/library/system.windows.forms.datagridview.aspx) angezeigt.</span><span class="sxs-lookup"><span data-stu-id="0481c-180">The results of these commands is displayed by using a [DataGridView](https://technet.microsoft.com/library/system.windows.forms.datagridview.aspx) control.</span></span>

<span data-ttu-id="0481c-181">**Runspace03**</span><span class="sxs-lookup"><span data-stu-id="0481c-181">**Runspace03**</span></span>

<span data-ttu-id="0481c-182">Zeigt, wie Sie die [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx)-Klasse zum synchronen Ausführen eines Skripts verwenden und wie Sie Fehler ohne Abbruch behandeln.</span><span class="sxs-lookup"><span data-stu-id="0481c-182">Shows how to use the [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) class to run a script synchronously, and how to handle non-terminating errors.</span></span>
<span data-ttu-id="0481c-183">Das Skript empfängt eine Liste von Prozessnamen und ruft diese Prozesse anschließend ab.</span><span class="sxs-lookup"><span data-stu-id="0481c-183">The script receives a list of process names and then retrieves those processes.</span></span>
<span data-ttu-id="0481c-184">Die Ergebnisse des Skripts, einschließlich Fehler ohne Abbruch, die beim Ausführen des Skripts generiert wurden, werden in einem Konsolenfenster angezeigt.</span><span class="sxs-lookup"><span data-stu-id="0481c-184">The results of the script, including any non-terminating errors that were generated when running the script, are displayed in a console window.</span></span>

<span data-ttu-id="0481c-185">**Runspace04**</span><span class="sxs-lookup"><span data-stu-id="0481c-185">**Runspace04**</span></span>

<span data-ttu-id="0481c-186">Zeigt, wie die [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx)-Klasse zum Ausführen von Befehlen verwendet wird und wie Fehler mit Abbruch abgefangen werden, die beim Ausführen der Befehle ausgelöst werden.</span><span class="sxs-lookup"><span data-stu-id="0481c-186">Shows how to use the [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) class to run commands, and how to catch terminating errors that are thrown when running the commands.</span></span>
<span data-ttu-id="0481c-187">Zwei Befehle werden ausgeführt. An den letzten Befehl wird ein ungültiges Parameterargument übergeben.</span><span class="sxs-lookup"><span data-stu-id="0481c-187">Two commands are run, and the last command is passed a parameter argument that is not valid.</span></span>
<span data-ttu-id="0481c-188">Daher werden keine Objekte zurückgegeben, und ein Fehler mit Abbruch wird ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="0481c-188">As a result, no objects are returned and a terminating error is thrown.</span></span>

<span data-ttu-id="0481c-189">**Runspace05**</span><span class="sxs-lookup"><span data-stu-id="0481c-189">**Runspace05**</span></span>

<span data-ttu-id="0481c-190">Zeigt, wie Sie einem [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx)-Objekt ein Snap-In hinzufügen, sodass das Cmdlet des Snap-Ins bei Öffnen des Runspace verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="0481c-190">Shows how to add a snap-in to an [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) object so that the cmdlet of the snap-in is available when the runspace is opened.</span></span>
<span data-ttu-id="0481c-191">Das Snap-In stellt ein Get-Proc-Cmdlet bereit (definiert durch das [GetProcessSample01-Beispiel](https://technet.microsoft.com/library/ff602028.aspx)), das synchron mithilfe eines [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx)-Objekts ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="0481c-191">The snap-in provides a Get-Proc cmdlet (defined by the [GetProcessSample01 Sample](https://technet.microsoft.com/library/ff602028.aspx)) that is run synchronously by using a [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) object.</span></span>

<span data-ttu-id="0481c-192">**Runspace06**</span><span class="sxs-lookup"><span data-stu-id="0481c-192">**Runspace06**</span></span>

<span data-ttu-id="0481c-193">Zeigt, wie Sie einem [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx)-Objekt ein Modul hinzufügen, sodass das Modul beim Öffnen des Runspace geladen wird.</span><span class="sxs-lookup"><span data-stu-id="0481c-193">Shows how to add a module to an [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) object so that the module is loaded when the runspace is opened.</span></span>
<span data-ttu-id="0481c-194">Das Modul stellt ein Get-Proc-Cmdlet bereit (definiert durch das [GetProcessSample02-Beispiel](https://technet.microsoft.com/library/ff602027.aspx)), das synchron mithilfe eines [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx)-Objekts ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="0481c-194">The module provides a Get-Proc cmdlet (defined by the [GetProcessSample02 Sample](https://technet.microsoft.com/library/ff602027.aspx)) that is run synchronously by using a [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) object.</span></span>

<span data-ttu-id="0481c-195">**Runspace07**</span><span class="sxs-lookup"><span data-stu-id="0481c-195">**Runspace07**</span></span>

<span data-ttu-id="0481c-196">Zeigt, wie Sie einen Runspace erstellen und dann diesen Runspace zum synchronen Ausführen von zwei Cmdlets anhand eines [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx)-Objekts verwenden.</span><span class="sxs-lookup"><span data-stu-id="0481c-196">Shows how to create a runspace, and then use that runspace to run two cmdlets synchronously by using a [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) object.</span></span>

<span data-ttu-id="0481c-197">**Runspace08**</span><span class="sxs-lookup"><span data-stu-id="0481c-197">**Runspace08**</span></span>

<span data-ttu-id="0481c-198">Zeigt, wie Sie der Pipeline eines [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx)-Objekts Befehle und Argumente hinzufügen und die Befehle synchron ausführen.</span><span class="sxs-lookup"><span data-stu-id="0481c-198">Shows how to add commands and arguments to the pipeline of a [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) object and how to run the commands synchronously.</span></span>

<span data-ttu-id="0481c-199">**Runspace09**</span><span class="sxs-lookup"><span data-stu-id="0481c-199">**Runspace09**</span></span>

<span data-ttu-id="0481c-200">Zeigt, wie Sie der Pipeline eines [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx)-Objekts ein Skript hinzufügen und das Skript asynchron ausführen.</span><span class="sxs-lookup"><span data-stu-id="0481c-200">Shows how to add a script to the pipeline of a [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) object and how to run the script asynchronously.</span></span>
<span data-ttu-id="0481c-201">Ereignisse werden verwendet, um die Ausgabe des Skripts zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="0481c-201">Events are used to handle the output of the script.</span></span>

<span data-ttu-id="0481c-202">**Runspace10**</span><span class="sxs-lookup"><span data-stu-id="0481c-202">**Runspace10**</span></span>

<span data-ttu-id="0481c-203">Zeigt, wie Sie einen anfänglichen Standardsitzungsstatus erstellen, dem [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) ein Cmdlet hinzufügen, einen Runspace erstellen, der den anfänglichen Sitzungsstatus verwendet, und wie Sie den Befehl anhand eines [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx)-Objekts ausführen.</span><span class="sxs-lookup"><span data-stu-id="0481c-203">Shows how to create a default initial session state, how to add a cmdlet to the [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx), how to create a runspace that uses the initial session state, and how to run the command by using a [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) object.</span></span>

<span data-ttu-id="0481c-204">**Runspace11**</span><span class="sxs-lookup"><span data-stu-id="0481c-204">**Runspace11**</span></span>

<span data-ttu-id="0481c-205">Zeigt, wie Sie mithilfe der [ProxyCommand](https://technet.microsoft.com/library/system.management.automation.proxycommand.aspx)-Klasse einen Proxybefehl erstellen, der ein vorhandenes Cmdlet aufruft, aber den Satz der verfügbaren Parameter einschränkt.</span><span class="sxs-lookup"><span data-stu-id="0481c-205">Shows how to use the [ProxyCommand](https://technet.microsoft.com/library/system.management.automation.proxycommand.aspx) class to create a proxy command that calls an existing cmdlet, but restricts the set of available parameters.</span></span>
<span data-ttu-id="0481c-206">Der Proxybefehl wird anschließend zu einem anfänglichen Sitzungsstatus hinzugefügt, der dazu verwendet wird, einen eingeschränkten Runspace zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="0481c-206">The proxy command is then added to an initial session state that is used to create a constrained runspace.</span></span>
<span data-ttu-id="0481c-207">Dies bedeutet, dass der Benutzer nur über den Proxybefehl auf die Funktionalität des Cmdlets zugreifen kann.</span><span class="sxs-lookup"><span data-stu-id="0481c-207">This means that the user can access the functionality of the cmdlet only through the proxy command.</span></span>

<span data-ttu-id="0481c-208">**PowerShell01**</span><span class="sxs-lookup"><span data-stu-id="0481c-208">**PowerShell01**</span></span>

<span data-ttu-id="0481c-209">Zeigt, wie Sie über ein [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx)-Objekt einen eingeschränkten Runspace erstellen.</span><span class="sxs-lookup"><span data-stu-id="0481c-209">Shows how to create a constrained runspace using an [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) object.</span></span>

<span data-ttu-id="0481c-210">**PowerShell02**</span><span class="sxs-lookup"><span data-stu-id="0481c-210">**PowerShell02**</span></span>

<span data-ttu-id="0481c-211">Zeigt, wie Sie einen Runspacepool verwenden, um mehrere Befehle gleichzeitig auszuführen.</span><span class="sxs-lookup"><span data-stu-id="0481c-211">Shows how to use a runspace pool to run multiple commands concurrently.</span></span>

## <a name="host-samples"></a><span data-ttu-id="0481c-212">Hostbeispiele</span><span class="sxs-lookup"><span data-stu-id="0481c-212">Host samples</span></span>

<span data-ttu-id="0481c-213">**Host01**</span><span class="sxs-lookup"><span data-stu-id="0481c-213">**Host01**</span></span>

<span data-ttu-id="0481c-214">Zeigt, wie eine Hostanwendung implementiert wird, die einen benutzerdefinierten Host verwendet.</span><span class="sxs-lookup"><span data-stu-id="0481c-214">Shows how to implement a host application that uses a custom host.</span></span>
<span data-ttu-id="0481c-215">In diesem Beispiel wird ein Runspace erstellt, der den benutzerdefinierten Host verwendet. Anschließend wird die [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx)-API zum Ausführen eines Skripts verwendet, das „exit“ aufruft.</span><span class="sxs-lookup"><span data-stu-id="0481c-215">In this sample a runspace is created that uses the custom host, and then the [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) API is used to run a script that calls "exit".</span></span>
<span data-ttu-id="0481c-216">Die Hostanwendung untersucht anschließend die Ausgabe des Skripts und gibt die Ergebnisse aus.</span><span class="sxs-lookup"><span data-stu-id="0481c-216">The host application then looks at the output of the script and prints out the results.</span></span>

<span data-ttu-id="0481c-217">**Host02**</span><span class="sxs-lookup"><span data-stu-id="0481c-217">**Host02**</span></span>

<span data-ttu-id="0481c-218">Zeigt, wie Sie eine Hostanwendung schreiben, die die Windows PowerShell-Laufzeit zusammen mit einer benutzerdefinierten Hostimplementierung verwendet.</span><span class="sxs-lookup"><span data-stu-id="0481c-218">Shows how to write a host application that uses the Windows PowerShell runtime along with a custom host implementation.</span></span>
<span data-ttu-id="0481c-219">Die Hostanwendung legt die Hostkultur auf Deutsch fest, führt das Cmdlet [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) aus und zeigt die Ergebnisse so an, wie sie über „pwrsh.exe“ dargestellt würden, und gibt dann das aktuelle Datum und die Uhrzeit auf Deutsch aus.</span><span class="sxs-lookup"><span data-stu-id="0481c-219">The host application sets the host culture to German, runs the [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet and displays the results as you would see them by using pwrsh.exe, and then prints out the current data and time in German.</span></span>

<span data-ttu-id="0481c-220">**Host03**</span><span class="sxs-lookup"><span data-stu-id="0481c-220">**Host03**</span></span>

<span data-ttu-id="0481c-221">Zeigt, wie eine interaktive, konsolenbasierte Hostanwendung erstellt wird, die Befehle von der Befehlszeile aus liest, die Befehle ausführt und die Ergebnisse anschließend in der Konsole anzeigt.</span><span class="sxs-lookup"><span data-stu-id="0481c-221">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>

<span data-ttu-id="0481c-222">**Host04**</span><span class="sxs-lookup"><span data-stu-id="0481c-222">**Host04**</span></span>

<span data-ttu-id="0481c-223">Zeigt, wie eine interaktive, konsolenbasierte Hostanwendung erstellt wird, die Befehle von der Befehlszeile aus liest, die Befehle ausführt und die Ergebnisse anschließend in der Konsole anzeigt.</span><span class="sxs-lookup"><span data-stu-id="0481c-223">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>
<span data-ttu-id="0481c-224">Diese Hostanwendung unterstützt auch das Anzeigen von Eingabeaufforderungen, die es den Benutzern ermöglichen, mehrere Auswahlmöglichkeiten anzugeben.</span><span class="sxs-lookup"><span data-stu-id="0481c-224">This host application also supports displaying prompts that allow the user to specify multiple choices.</span></span>

<span data-ttu-id="0481c-225">**Host05**</span><span class="sxs-lookup"><span data-stu-id="0481c-225">**Host05**</span></span>

<span data-ttu-id="0481c-226">Zeigt, wie eine interaktive, konsolenbasierte Hostanwendung erstellt wird, die Befehle von der Befehlszeile aus liest, die Befehle ausführt und die Ergebnisse anschließend in der Konsole anzeigt.</span><span class="sxs-lookup"><span data-stu-id="0481c-226">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>
<span data-ttu-id="0481c-227">Diese Anwendung unterstützt auch Aufrufe von Remotecomputern mithilfe der Cmdlets [Enter-PsSession](http://go.microsoft.com/fwlink/?LinkId=135210) und [Exit-PsSession](http://go.microsoft.com/fwlink/?LinkId=135212).</span><span class="sxs-lookup"><span data-stu-id="0481c-227">This host application also supports calls to remote computers by using the [Enter-PsSession](http://go.microsoft.com/fwlink/?LinkId=135210) and [Exit-PsSession](http://go.microsoft.com/fwlink/?LinkId=135212) cmdlets.</span></span>

<span data-ttu-id="0481c-228">**Host06**</span><span class="sxs-lookup"><span data-stu-id="0481c-228">**Host06**</span></span>

<span data-ttu-id="0481c-229">Zeigt, wie eine interaktive, konsolenbasierte Hostanwendung erstellt wird, die Befehle von der Befehlszeile aus liest, die Befehle ausführt und die Ergebnisse anschließend in der Konsole anzeigt.</span><span class="sxs-lookup"><span data-stu-id="0481c-229">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>
<span data-ttu-id="0481c-230">Darüber hinaus verwendet dieses Beispiel die Tokenizer-APIs, um die Farbe des vom Benutzer eingegebenen Texts anzugeben.</span><span class="sxs-lookup"><span data-stu-id="0481c-230">In addition, this sample uses the Tokenizer APIs to specify the color of the text that is entered by the user.</span></span>

## <a name="provider-samples"></a><span data-ttu-id="0481c-231">Anbieterbeispiele</span><span class="sxs-lookup"><span data-stu-id="0481c-231">Provider samples</span></span>

<span data-ttu-id="0481c-232">**AccessDBProviderSample01**</span><span class="sxs-lookup"><span data-stu-id="0481c-232">**AccessDBProviderSample01**</span></span>

<span data-ttu-id="0481c-233">Zeigt, wie Sie eine Anbieterklasse deklarieren, die direkt von der [CmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.cmdletprovider.aspx)-Klasse abgeleitet wird.</span><span class="sxs-lookup"><span data-stu-id="0481c-233">Shows how to declare a provider class that derives directly from the [CmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.cmdletprovider.aspx) class.</span></span>
<span data-ttu-id="0481c-234">Wird hier nur aus Gründen der Vollständigkeit aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="0481c-234">It is included here only for completeness.</span></span>

<span data-ttu-id="0481c-235">**AccessDBProviderSample02**</span><span class="sxs-lookup"><span data-stu-id="0481c-235">**AccessDBProviderSample02**</span></span>

<span data-ttu-id="0481c-236">Zeigt, wie Sie die Methoden [NewDrive](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.newdrive.aspx) und [RemoveDrive](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.removedrive.aspx) überschreiben, um Aufrufe an die Cmdlets „New-PSDrive“ und „Remove-PSDrive“ zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="0481c-236">Shows how to overwrite the [NewDrive](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.newdrive.aspx) and [RemoveDrive](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.removedrive.aspx) methods to support calls to the New-PSDrive and Remove-PSDrive cmdlets.</span></span>
<span data-ttu-id="0481c-237">Die Anbieterklasse in diesem Beispiel wird von der [DriveCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.aspx)-Klasse abgeleitet.</span><span class="sxs-lookup"><span data-stu-id="0481c-237">The provider class in this sample derives from the [DriveCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.aspx) class.</span></span>

<span data-ttu-id="0481c-238">**AccessDBProviderSample03**</span><span class="sxs-lookup"><span data-stu-id="0481c-238">**AccessDBProviderSample03**</span></span>

<span data-ttu-id="0481c-239">Zeigt, wie Sie die Methoden [GetItem](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.getitem.aspx) und [SetItem](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.setitem.aspx) überschreiben, um Aufrufe an die Cmdlets „Get-Item“ und „Set-Item“ zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="0481c-239">Shows how to overwrite the [GetItem](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.getitem.aspx) and [SetItem](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.setitem.aspx) methods to support calls to the Get-Item and Set-Item cmdlets.</span></span>
<span data-ttu-id="0481c-240">Die Anbieterklasse in diesem Beispiel wird von der [ItemCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.aspx)-Klasse abgeleitet.</span><span class="sxs-lookup"><span data-stu-id="0481c-240">The provider class in this sample derives from the [ItemCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.aspx) class.</span></span>

<span data-ttu-id="0481c-241">**AccessDBProviderSample04**</span><span class="sxs-lookup"><span data-stu-id="0481c-241">**AccessDBProviderSample04**</span></span>

<span data-ttu-id="0481c-242">Zeigt, wie Sie Containermethoden überschreiben, um Aufrufe der Cmdlets „Copy-Item“, „Get-ChildItem“, „New-Item“ und „Remove-Item“ zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="0481c-242">Shows how to overwrite container methods to support calls to the Copy-Item, Get-ChildItem, New-Item, and Remove-Item cmdlets.</span></span>
<span data-ttu-id="0481c-243">Diese Methoden sollten implementiert werden, wenn der Datenspeicher Elemente enthält, die Container sind.</span><span class="sxs-lookup"><span data-stu-id="0481c-243">These methods should be implemented when the data store contains items that are containers.</span></span>
<span data-ttu-id="0481c-244">Ein Container ist eine Gruppe von untergeordneten Elementen unter einem gemeinsamen übergeordneten Element.</span><span class="sxs-lookup"><span data-stu-id="0481c-244">A container is a group of child items under a common parent item.</span></span>
<span data-ttu-id="0481c-245">Die Anbieterklasse in diesem Beispiel wird von der [ItemCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.aspx)-Klasse abgeleitet.</span><span class="sxs-lookup"><span data-stu-id="0481c-245">The provider class in this sample derives from the [ItemCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.aspx) class.</span></span>

<span data-ttu-id="0481c-246">**AccessDBProviderSample05**</span><span class="sxs-lookup"><span data-stu-id="0481c-246">**AccessDBProviderSample05**</span></span>

<span data-ttu-id="0481c-247">Zeigt, wie Sie Containermethoden überschreiben, um Aufrufe der Cmdlets „Move-Item“ und „Join-Path“ zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="0481c-247">Shows how to overwrite container methods to support calls to the Move-Item and Join-Path cmdlets.</span></span>
<span data-ttu-id="0481c-248">Diese Methoden sollten implementiert werden, wenn der Benutzer Elemente innerhalb eines Containers verschieben muss, und wenn der Datenspeicher geschachtelte Container enthält.</span><span class="sxs-lookup"><span data-stu-id="0481c-248">These methods should be implemented when the user needs to move items within a container and if the data store contains nested containers.</span></span>
<span data-ttu-id="0481c-249">Die Anbieterklasse in diesem Beispiel wird von der [NavigationCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider.aspx)-Klasse abgeleitet.</span><span class="sxs-lookup"><span data-stu-id="0481c-249">The provider class in this sample derives from the [NavigationCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider.aspx) class.</span></span>

<span data-ttu-id="0481c-250">**AccessDBProviderSample06**</span><span class="sxs-lookup"><span data-stu-id="0481c-250">**AccessDBProviderSample06**</span></span>

<span data-ttu-id="0481c-251">Zeigt, wie Sie Inhaltsmethoden überschreiben, um Aufrufe der Cmdlets „Clear-Content“, „Get-Content“ und „Set-Content“ zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="0481c-251">Shows how to overwrite content methods to support calls to the Clear-Content, Get-Content, and Set-Content cmdlets.</span></span>
<span data-ttu-id="0481c-252">Diese Methoden sollten implementiert werden, wenn der Benutzer den Inhalt der Elemente im Datenspeicher verwaltet muss.</span><span class="sxs-lookup"><span data-stu-id="0481c-252">These methods should be implemented when the user needs to manage the content of the items in the data store.</span></span>
<span data-ttu-id="0481c-253">Die Anbieterklasse in diesem Beispiel wird von der [NavigationCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider.aspx)-Klasse abgeleitet und implementiert die [IContentCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.icontentcmdletprovider.aspx)-Schnittstelle.</span><span class="sxs-lookup"><span data-stu-id="0481c-253">The provider class in this sample derives from the [NavigationCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider.aspx) class, and it implements the [IContentCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.icontentcmdletprovider.aspx) interface.</span></span>

