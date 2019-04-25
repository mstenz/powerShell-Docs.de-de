---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Erstellen von .NET- und COM-Objekten – New-Object
ms.assetid: 2057b113-efeb-465e-8b44-da2f20dbf603
ms.openlocfilehash: ef8215303aacd90536d3c2ae57bc3629e202f318
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086364"
---
# <a name="creating-net-and-com-objects-new-object"></a><span data-ttu-id="f2cbd-103">Erstellen von .NET- und COM-Objekten (New-Object)</span><span class="sxs-lookup"><span data-stu-id="f2cbd-103">Creating .NET and COM Objects (New-Object)</span></span>

<span data-ttu-id="f2cbd-104">Es gibt Softwarekomponenten mit .NET Framework- und COM-Schnittstellen, mit denen Sie viele Systemverwaltungsaufgaben ausführen können.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-104">There are software components with .NET Framework and COM interfaces that enable you to perform many system administration tasks.</span></span> <span data-ttu-id="f2cbd-105">Mit Windows PowerShell können Sie diese Komponenten verwenden und sind somit nicht auf die Aufgaben beschränkt, die mithilfe von Cmdlets ausgeführt werden können.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-105">Windows PowerShell lets you use these components, so you are not limited to the tasks that can be performed by using cmdlets.</span></span> <span data-ttu-id="f2cbd-106">Viele der Cmdlets in der ursprünglichen Version von Windows PowerShell funktionieren nicht auf Remotecomputern.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-106">Many of the cmdlets in the initial release of Windows PowerShell do not work against remote computers.</span></span> <span data-ttu-id="f2cbd-107">Wir zeigen, wie diese Einschränkung beim Verwalten von Ereignisprotokollen mithilfe der .NET Framework-Klasse **System.Diagnostics.EventLog** direkt aus Windows PowerShell heraus umgangen werden können.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-107">We will demonstrate how to get around this limitation when managing event logs by using the .NET Framework **System.Diagnostics.EventLog** class directly from Windows PowerShell.</span></span>

## <a name="using-new-object-for-event-log-access"></a><span data-ttu-id="f2cbd-108">Verwenden von „New-Object“ für den Zugriff auf das Ereignisprotokoll</span><span class="sxs-lookup"><span data-stu-id="f2cbd-108">Using New-Object for Event Log Access</span></span>

<span data-ttu-id="f2cbd-109">Die .NET Framework-Klassenbibliothek enthält eine Klasse namens **System.Diagnostics.EventLog**, die zum Verwalten von Ereignisprotokollen verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-109">The .NET Framework Class Library includes a class named **System.Diagnostics.EventLog** that can be used to manage event logs.</span></span> <span data-ttu-id="f2cbd-110">Zum Erstellen einer neuen Instanz einer .NET Framework-Klasse können Sie das Cmdlet **New-Object** mit dem Parameter **TypeName** verwenden.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-110">You can create a new instance of a .NET Framework class by using the **New-Object** cmdlet with the **TypeName** parameter.</span></span> <span data-ttu-id="f2cbd-111">Der folgende Befehl erstellt z. B. einen Ereignisprotokollverweis:</span><span class="sxs-lookup"><span data-stu-id="f2cbd-111">For example, the following command creates an event log reference:</span></span>

```
PS> New-Object -TypeName System.Diagnostics.EventLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
```

<span data-ttu-id="f2cbd-112">Obwohl der Befehl eine Instanz der EventLog-Klasse erstellt hat, enthält die Instanz keine Daten.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-112">Although the command has created an instance of the EventLog class, the instance does not include any data.</span></span> <span data-ttu-id="f2cbd-113">Der Grund hierfür ist, dass wir kein bestimmtes Ereignisprotokoll angegeben haben.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-113">That is because we did not specify a particular event log.</span></span> <span data-ttu-id="f2cbd-114">Wie erhalten Sie ein echtes Ereignisprotokoll?</span><span class="sxs-lookup"><span data-stu-id="f2cbd-114">How do you get a real event log?</span></span>

### <a name="using-constructors-with-new-object"></a><span data-ttu-id="f2cbd-115">Verwenden von Konstruktoren mit „New-Object“</span><span class="sxs-lookup"><span data-stu-id="f2cbd-115">Using Constructors with New-Object</span></span>

<span data-ttu-id="f2cbd-116">Um auf ein bestimmtes Ereignisprotokoll zu verweisen, müssen Sie den Namen des Protokolls angeben.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-116">To refer to a specific event log, you need to specify the name of the log.</span></span> <span data-ttu-id="f2cbd-117">**New-Object** verfügt über einen **ArgumentList**-Parameter.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-117">**New-Object** has an **ArgumentList** parameter.</span></span> <span data-ttu-id="f2cbd-118">Die Argumente, die Sie als Werte an diesen Parameter übergeben, werden von einer speziellen Startmethode des Objekts verwendet.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-118">The arguments you pass as values to this parameter are used by a special startup method of the object.</span></span> <span data-ttu-id="f2cbd-119">Die Methode wird als *Konstruktor* bezeichnet, da sie zum Konstruieren des Objekts dient.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-119">The method is called a *constructor* because it is used to construct the object.</span></span> <span data-ttu-id="f2cbd-120">Um beispielsweise einen Verweis auf das Anwendungsprotokoll zu erhalten, geben Sie die Zeichenfolge „Application“ als Argument ein:</span><span class="sxs-lookup"><span data-stu-id="f2cbd-120">For example, to get a reference to the Application log, you specify the string 'Application' as an argument:</span></span>

```
PS> New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application

Max(K) Retain OverflowAction        Entries Name
------ ------ --------------        ------- ----
16,384      7 OverwriteOlder          2,160 Application
```

> [!NOTE]
> <span data-ttu-id="f2cbd-121">Da die meisten .NET Framework Core-Klassen im System-Namespace enthalten sind, versucht Windows PowerShell automatisch, Klassen zu finden, die Sie im System-Namespace angeben, wenn keine Übereinstimmung für den angegebenen Typnamen gefunden wird.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-121">Since most of the .NET Framework core classes are contained in the System namespace, Windows PowerShell will automatically attempt to find classes you specify in the System namespace if it cannot find a match for the typename you specify.</span></span> <span data-ttu-id="f2cbd-122">Dies bedeutet, dass Sie „Diagnostics.EventLog“ anstelle von „System.Diagnostics.EventLog“ angeben können.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-122">This means that you can specify Diagnostics.EventLog instead of System.Diagnostics.EventLog.</span></span>

### <a name="storing-objects-in-variables"></a><span data-ttu-id="f2cbd-123">Speichern von Objekten in Variablen</span><span class="sxs-lookup"><span data-stu-id="f2cbd-123">Storing Objects in Variables</span></span>

<span data-ttu-id="f2cbd-124">Möglicherweise möchten Sie einen Verweis auf ein Objekt speichern, damit Sie es in der aktuellen Shell verwenden können.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-124">You might want to store a reference to an object, so you can use it in the current shell.</span></span> <span data-ttu-id="f2cbd-125">Obwohl Windows PowerShell Ihnen ermöglicht, viele Aufgaben mit Pipelines zu erledigen und damit die Notwendigkeit von Variablen zu verringern, erleichtert das Speichern von Verweisen auf Objekte in Variablen manchmal die Bearbeitung dieser Objekte.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-125">Although Windows PowerShell lets you do a lot of work with pipelines, lessening the need for variables, sometimes storing references to objects in variables makes it more convenient to manipulate those objects.</span></span>

<span data-ttu-id="f2cbd-126">Mit Windows PowerShell können Sie Variablen erstellen, die im Prinzip benannte Objekte sind.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-126">Windows PowerShell lets you create variables that are essentially named objects.</span></span> <span data-ttu-id="f2cbd-127">Die Ausgabe eines beliebigen gültigen Windows PowerShell-Befehls kann in einer Variablen gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-127">The output from any valid Windows PowerShell command can be stored in a variable.</span></span> <span data-ttu-id="f2cbd-128">Namen von Variablen beginnen immer mit $.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-128">Variable names always begin with $.</span></span> <span data-ttu-id="f2cbd-129">Wenn Sie den Verweis auf ein Anwendungsprotokoll in einer Variablen namens „$AppLog“ speichern möchten, geben Sie den Namen der Variablen an, gefolgt von einem Gleichheitszeichen und dem Befehl zum Erstellen des Anwendungsprotokollobjekts:</span><span class="sxs-lookup"><span data-stu-id="f2cbd-129">If you want to store the Application log reference in a variable named $AppLog, type the name of the variable, followed by an equal sign and then type the command used to create the Application log object:</span></span>

```
PS> $AppLog = New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application
```

<span data-ttu-id="f2cbd-130">Wenn Sie dann „$AppLog“ eingeben, sehen Sie, dass es das Anwendungsprotokoll enthält:</span><span class="sxs-lookup"><span data-stu-id="f2cbd-130">If you then type $AppLog, you can see that it contains the Application log:</span></span>

```
PS> $AppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
  16,384      7 OverwriteOlder          2,160 Application
```

### <a name="accessing-a-remote-event-log-with-new-object"></a><span data-ttu-id="f2cbd-131">Zugreifen auf ein Remoteereignisprotokoll mit „New-Object“</span><span class="sxs-lookup"><span data-stu-id="f2cbd-131">Accessing a Remote Event Log with New-Object</span></span>

<span data-ttu-id="f2cbd-132">Die im vorherigen Abschnitt verwendeten Befehle hatten den lokalen Computer als Ziel. Dazu kann auch das Cmdlet **Get-EventLog** verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-132">The commands used in the preceding section target the local computer; the **Get-EventLog** cmdlet can do that.</span></span> <span data-ttu-id="f2cbd-133">Um auf das Anwendungsprotokoll auf einem Remotecomputer zuzugreifen, müssen Sie sowohl den Namen des Protokolls als auch einen Computernamen (oder eine IP-Adresse) als Argumente bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-133">To access the Application log on a remote computer, you must supply both the log name and a computer name (or IP address) as arguments.</span></span>

```
PS> $RemoteAppLog = New-Object -TypeName System.Diagnostics.EventLog Application,192.168.1.81
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder            262 Application
```

<span data-ttu-id="f2cbd-134">Welche Aufgaben können wir nun mit dem Verweis auf ein in der Variablen $RemoteAppLog gespeichertes Ereignisprotokoll ausführen?</span><span class="sxs-lookup"><span data-stu-id="f2cbd-134">Now that we have a reference to an event log stored in the $RemoteAppLog variable, what tasks can we perform on it?</span></span>

### <a name="clearing-an-event-log-with-object-methods"></a><span data-ttu-id="f2cbd-135">Löschen eines Ereignisprotokolls mit Objektmethoden</span><span class="sxs-lookup"><span data-stu-id="f2cbd-135">Clearing an Event Log with Object Methods</span></span>

<span data-ttu-id="f2cbd-136">Objekte verfügen oft über Methoden, die aufgerufen werden können, um Aufgaben auszuführen.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-136">Objects often have methods that can be called to perform tasks.</span></span> <span data-ttu-id="f2cbd-137">Sie können **Get-Member** verwenden, um die einem Objekt zugeordneten Methoden anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-137">You can use **Get-Member** to display the methods associated with an object.</span></span> <span data-ttu-id="f2cbd-138">Mit dem folgenden Befehl und der ausgewählten Ausgabe werden einige der Methoden der EventLog-Klasse angezeigt:</span><span class="sxs-lookup"><span data-stu-id="f2cbd-138">The following command and selected output show some the methods of the EventLog class:</span></span>

```
PS> $RemoteAppLog | Get-Member -MemberType Method

   TypeName: System.Diagnostics.EventLog

Name                      MemberType Definition
----                      ---------- ----------
...
Clear                     Method     System.Void Clear()
Close                     Method     System.Void Close()
...
GetType                   Method     System.Type GetType()
...
ModifyOverflowPolicy      Method     System.Void ModifyOverflowPolicy(Overfl...
RegisterDisplayName       Method     System.Void RegisterDisplayName(String ...
...
ToString                  Method     System.String ToString()
WriteEntry                Method     System.Void WriteEntry(String message),...
WriteEvent                Method     System.Void WriteEvent(EventInstance in...
```

<span data-ttu-id="f2cbd-139">Die Methode **Clear()** kann zum Löschen des Ereignisprotokolls verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-139">The **Clear()** method can be used to clear the event log.</span></span> <span data-ttu-id="f2cbd-140">Beim Aufrufen einer Methode müssen dem Methodennamen immer Klammern folgen, auch wenn die Methode keine Argumente erfordert.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-140">When calling a method, you must always follow the method name by parentheses, even if the method does not require arguments.</span></span> <span data-ttu-id="f2cbd-141">So kann Windows PowerShell zwischen der Methode und einer möglichen Eigenschaft mit gleichem Namen unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-141">This lets Windows PowerShell distinguish between the method and a potential property with the same name.</span></span> <span data-ttu-id="f2cbd-142">Geben Sie Folgendes ein, um die Methode **Clear** aufzurufen:</span><span class="sxs-lookup"><span data-stu-id="f2cbd-142">Type the following to call the **Clear** method:</span></span>

```
PS> $RemoteAppLog.Clear()
```

<span data-ttu-id="f2cbd-143">Geben Sie Folgendes ein, um das Protokoll anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-143">Type the following to display the log.</span></span> <span data-ttu-id="f2cbd-144">Sie können erkennen, dass das Ereignisprotokoll gelöscht wurde und jetzt statt 262 Einträgen 0 Einträge enthält:</span><span class="sxs-lookup"><span data-stu-id="f2cbd-144">You will see that the event log was cleared, and now has 0 entries instead of 262:</span></span>

```
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder              0 Application
```

## <a name="creating-com-objects-with-new-object"></a><span data-ttu-id="f2cbd-145">Erstellen von COM-Objekten mit „New-Object“</span><span class="sxs-lookup"><span data-stu-id="f2cbd-145">Creating COM Objects with New-Object</span></span>
<span data-ttu-id="f2cbd-146">Sie können **New-Object** verwenden, um mit Component Object Model-Komponenten (COM) zu arbeiten.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-146">You can use **New-Object** to work with Component Object Model (COM) components.</span></span> <span data-ttu-id="f2cbd-147">Die Komponenten reichen von den verschiedenen in Windows Script Host (WSH) enthaltenen Bibliotheken bis hin zu ActiveX-Anwendungen wie Internet Explorer, die auf den meisten Systemen installiert sind.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-147">Components range from the various libraries included with Windows Script Host (WSH) to ActiveX applications such as Internet Explorer that are installed on most systems.</span></span>

<span data-ttu-id="f2cbd-148">**New-Object** verwendet zum Erstellen von COM-Objekten .NET Framework Runtime Callable Wrapper, es gelten somit die gleichen Einschränkungen wie für .NET Framework beim Aufrufen von COM-Objekten.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-148">**New-Object** uses .NET Framework Runtime-Callable Wrappers to create COM objects, so it has the same limitations that .NET Framework does when calling COM objects.</span></span> <span data-ttu-id="f2cbd-149">Zum Erstellen eines COM-Objekts müssen Sie den Parameter **ComObject** mit dem programmatischen Bezeichner bzw. der *ProgId* der COM-Klasse angeben, die Sie verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-149">To create a COM object, you need to specify the **ComObject** parameter with the Programmatic Identifier or *ProgId* of the COM class you want to use.</span></span> <span data-ttu-id="f2cbd-150">Eine vollständige Erläuterung der Einschränkungen der COM-Verwendung und Informationen zu den auf einem System verfügbaren ProgIDs würden den Rahmen dieses Handbuchs sprengen, aber die meisten bekannten Objekte aus Umgebungen wie WSH können in Windows PowerShell verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-150">A complete discussion of the limitations of COM use and determining what ProgIds are available on a system is beyond the scope of this user's guide, but most well-known objects from environments such as WSH can be used within Windows PowerShell.</span></span>

<span data-ttu-id="f2cbd-151">Sie können die WSH-Objekte durch Angabe der folgenden ProgIDs erstellen: **WScript.Shell**, **WScript.Network**, **Scripting.Dictionary** und **Scripting.FileSystemObject**.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-151">You can create the WSH objects by specifying these progids: **WScript.Shell**, **WScript.Network**, **Scripting.Dictionary**, and **Scripting.FileSystemObject**.</span></span> <span data-ttu-id="f2cbd-152">Mit den folgenden Befehlen werden diese Objekte erstellt:</span><span class="sxs-lookup"><span data-stu-id="f2cbd-152">The following commands create these objects:</span></span>

```powershell
New-Object -ComObject WScript.Shell
New-Object -ComObject WScript.Network
New-Object -ComObject Scripting.Dictionary
New-Object -ComObject Scripting.FileSystemObject
```

<span data-ttu-id="f2cbd-153">Die meisten Funktionen dieser Klassen werden zwar auch auf andere Weise in Windows PowerShell bereitgestellt, aber einige Aufgaben wie das Erstellen einer Verknüpfung lassen sich mit den WSH-Klassen einfacher erledigen.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-153">Although most of the functionality of these classes is made available in other ways in Windows PowerShell, a few tasks such as shortcut creation are still easier to do using the WSH classes.</span></span>

## <a name="creating-a-desktop-shortcut-with-wscriptshell"></a><span data-ttu-id="f2cbd-154">Erstellen einer Desktopverknüpfung mit „WScript.Shell“</span><span class="sxs-lookup"><span data-stu-id="f2cbd-154">Creating a Desktop Shortcut with WScript.Shell</span></span>

<span data-ttu-id="f2cbd-155">Eine Aufgabe, die mit einem COM-Objekt schnell und einfach ausgeführt werden kann, ist das Erstellen einer Verknüpfung.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-155">One task that can be performed quickly with a COM object is creating a shortcut.</span></span> <span data-ttu-id="f2cbd-156">Angenommen, Sie möchten auf dem Desktop eine Verknüpfung zum Basisordner für Windows PowerShell erstellen.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-156">Suppose you want to create a shortcut on your desktop that links to the home folder for Windows PowerShell.</span></span> <span data-ttu-id="f2cbd-157">Zuerst müssen Sie einen Verweis auf **WScript.Shell** erstellen, den wir in einer Variablen namens **$WshShell** speichern:</span><span class="sxs-lookup"><span data-stu-id="f2cbd-157">You first need to create a reference to **WScript.Shell**, which we will store in a variable named **$WshShell**:</span></span>

```powershell
$WshShell = New-Object -ComObject WScript.Shell
```

<span data-ttu-id="f2cbd-158">„Get-Member“ funktioniert mit COM-Objekten, sodass Sie die Elemente des Objekts untersuchen können, indem Sie folgendes eingeben:</span><span class="sxs-lookup"><span data-stu-id="f2cbd-158">Get-Member works with COM objects, so you can explore the members of the object by typing:</span></span>

```
PS> $WshShell | Get-Member

   TypeName: System.__ComObject#{41904400-be18-11d3-a28b-00104bd35090}

Name                     MemberType            Definition
----                     ----------            ----------
AppActivate              Method                bool AppActivate (Variant, Va...
CreateShortcut           Method                IDispatch CreateShortcut (str...
...
```

<span data-ttu-id="f2cbd-159">**Get-Member** verfügt über einen optionalen **InputObject**-Parameter, den Sie anstelle von Piping als Eingabe für **Get-Member** verwenden können.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-159">**Get-Member** has an optional **InputObject** parameter you can use instead of piping to provide input to **Get-Member**.</span></span> <span data-ttu-id="f2cbd-160">Dieselbe Ausgabe wie oben hätten Sie auch über den Befehl **Get-Member -InputObject $WshShell** erhalten.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-160">You would get the same output as shown above if you instead used the command **Get-Member -InputObject $WshShell**.</span></span> <span data-ttu-id="f2cbd-161">Wenn Sie **InputObject** verwenden, wird das Argument als ein einzelnes Element behandelt.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-161">If you use **InputObject**, it treats its argument as a single item.</span></span> <span data-ttu-id="f2cbd-162">Dies bedeutet, dass bei mehreren Objekte in einer Variablen diese von **Get-Member** als ein Array von Objekten behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-162">This means that if you have several objects in a variable, **Get-Member** treats them as an array of objects.</span></span> <span data-ttu-id="f2cbd-163">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="f2cbd-163">For example:</span></span>

```
PS> $a = 1,2,"three"
PS> Get-Member -InputObject $a
TypeName: System.Object[]
Name               MemberType    Definition
----               ----------    ----------
Count              AliasProperty Count = Length
...
```

<span data-ttu-id="f2cbd-164">Die Methode **WScript.Shell CreateShortcut** akzeptiert ein einziges Argument, und zwar, den Pfad zur zu erstellenden Verknüpfungsdatei.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-164">The **WScript.Shell CreateShortcut** method accepts a single argument, the path to the shortcut file to create.</span></span> <span data-ttu-id="f2cbd-165">Wir könnten den vollständigen Pfad zum Desktop eingeben, aber es gibt einen einfacheren Weg.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-165">We could type in the full path to the desktop, but there is an easier way.</span></span> <span data-ttu-id="f2cbd-166">Der Desktop wird normalerweise durch einen Ordner namens „Desktop“ im Basisordner des aktuellen Benutzers dargestellt.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-166">The desktop is normally represented by a folder named Desktop inside the home folder of the current user.</span></span> <span data-ttu-id="f2cbd-167">Windows PowerShell verfügt über eine Variable **$Home**, die den Pfad zu diesem Ordner enthält.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-167">Windows PowerShell has a variable **$Home** that contains the path to this folder.</span></span> <span data-ttu-id="f2cbd-168">Sie können den Pfad zum Basisordner mithilfe dieser Variablen angeben und dann den Namen des Ordners „Desktop“ sowie den Namen für die zu erstellende Verknüpfung hinzufügen. Geben Sie dazu Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="f2cbd-168">We can specify the path to the home folder by using this variable, and then add the name of the Desktop folder and the name for the shortcut to create by typing:</span></span>

```powershell
$lnk = $WshShell.CreateShortcut("$Home\Desktop\PSHome.lnk")
```

<span data-ttu-id="f2cbd-169">Wenn Sie ein Element, das wie ein Variablenname aussieht, in doppelten Anführungszeichen angeben, versucht Windows PowerShell, dieses Element durch einen entsprechenden Wert zu ersetzen.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-169">When you use something that looks like a variable name inside double-quotes, Windows PowerShell tries to substitute a matching value.</span></span> <span data-ttu-id="f2cbd-170">Wenn Sie einzelne Anführungszeichen verwenden, versucht Windows PowerShell nicht, den Variablenwert zu ersetzen.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-170">If you use single-quotes, Windows PowerShell does not try to substitute the variable value.</span></span> <span data-ttu-id="f2cbd-171">Geben Sie beispielsweise die folgenden Befehle ein:</span><span class="sxs-lookup"><span data-stu-id="f2cbd-171">For example, try typing the following commands:</span></span>

```
PS> "$Home\Desktop\PSHome.lnk"
C:\Documents and Settings\aka\Desktop\PSHome.lnk
PS> '$Home\Desktop\PSHome.lnk'
$Home\Desktop\PSHome.lnk
```

<span data-ttu-id="f2cbd-172">Wir verfügen jetzt über eine Variable namens **$lnk**, die einen neuen Verknüpfungsverweis enthält.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-172">We now have a variable named **$lnk** that contains a new shortcut reference.</span></span> <span data-ttu-id="f2cbd-173">Wenn Sie die zugehörigen Elemente anzeigen möchten, können Sie sie über die Pipeline an **Get-Member** übergeben.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-173">If you want to see its members, you can pipe it to **Get-Member**.</span></span> <span data-ttu-id="f2cbd-174">In der folgenden Ausgabe werden die zum Abschließen der Erstellung unserer Verknüpfung zu verwendenden Elemente angezeigt:</span><span class="sxs-lookup"><span data-stu-id="f2cbd-174">The output below shows the members we need to use to finish creating our shortcut:</span></span>

```
PS> $lnk | Get-Member
TypeName: System.__ComObject#{f935dc23-1cf0-11d0-adb9-00c04fd58a0b}
Name             MemberType   Definition
----             ----------   ----------
...
Save             Method       void Save ()
...
TargetPath       Property     string TargetPath () {get} {set}
```

<span data-ttu-id="f2cbd-175">Sie müssen den **TargetPath** angeben, d.h. den Anwendungsordner für Windows PowerShell, und dann die Verknüpfung **$lnk** durch Aufrufen der Methode **Save** speichern.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-175">We need to specify the **TargetPath**, which is the application folder for Windows PowerShell, and then save the shortcut **$lnk** by calling the **Save** method.</span></span> <span data-ttu-id="f2cbd-176">Der Pfad des Windows PowerShell-Anwendungsordners ist in der Variablen **$PSHome** gespeichert, also geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="f2cbd-176">The Windows PowerShell application folder path is stored in the variable **$PSHome**, so we can do this by typing:</span></span>

```powershell
$lnk.TargetPath = $PSHome
$lnk.Save()
```

## <a name="using-internet-explorer-from-windows-powershell"></a><span data-ttu-id="f2cbd-177">Verwenden von Internet Explorer in Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f2cbd-177">Using Internet Explorer from Windows PowerShell</span></span>

<span data-ttu-id="f2cbd-178">Viele Anwendungen (einschließlich der Microsoft Office-Anwendungen und Internet Explorer) können mithilfe von COM automatisiert werden.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-178">Many applications (including the Microsoft Office family of applications and Internet Explorer) can be automated by using COM.</span></span> <span data-ttu-id="f2cbd-179">Internet Explorer verdeutlicht einige der typischen Techniken und Probleme im Zusammenhang mit COM-basierten Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-179">Internet Explorer illustrates some of the typical techniques and issues involved in working with COM-based applications.</span></span>

<span data-ttu-id="f2cbd-180">Sie erstellen eine Internet Explorer-Instanz, indem Sie die ProgID von Internet Explorer angeben, **InternetExplorer.Application**:</span><span class="sxs-lookup"><span data-stu-id="f2cbd-180">You create an Internet Explorer instance by specifying the Internet Explorer ProgId, **InternetExplorer.Application**:</span></span>

```powershell
$ie = New-Object -ComObject InternetExplorer.Application
```

<span data-ttu-id="f2cbd-181">Dieser Befehl startet Internet Explorer, zeigt die Anwendung macht aber nicht an.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-181">This command starts Internet Explorer, but does not make it visible.</span></span> <span data-ttu-id="f2cbd-182">Wenn Sie „Get-Process“ eingeben, können Sie sehen, dass ein Prozess mit dem Namen „iexplore“ ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-182">If you type Get-Process, you can see that a process named iexplore is running.</span></span> <span data-ttu-id="f2cbd-183">Auch wenn Sie Windows PowerShell beenden, wird der Prozess weiterhin ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-183">In fact, if you exit Windows PowerShell, the process will continue to run.</span></span> <span data-ttu-id="f2cbd-184">Sie müssen den Computer neu starten oder ein Tool wie Task-Manager verwenden, um den Prozess „iexplore“ zu beenden.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-184">You must reboot the computer or use a tool like Task Manager to end the iexplore process.</span></span>

> [!NOTE]
> <span data-ttu-id="f2cbd-185">Für COM-Objekte, die als separate Prozesse gestartet werden, so genannte *ActiveX-EXE-Dateien*, kann beim Start ein Benutzeroberflächenfenster angezeigt werden, muss aber nicht.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-185">COM objects that start as separate processes, commonly called *ActiveX executables*, may or may not display a user interface window when they start up.</span></span> <span data-ttu-id="f2cbd-186">Wenn ein Objekt ein Fenster erstellt, dieses aber nicht anzeigt, wie Internet Explorer, geht der Fokus in der Regel an den Windows-Desktop, und Sie müssen das Fenster einblenden, um mit ihm zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-186">If they create a window but do not make it visible, like Internet Explorer, the focus will generally move to the Windows desktop and you must make the window visible to interact with it.</span></span>

<span data-ttu-id="f2cbd-187">Durch Eingabe von **$ie | Get-Member** können Sie Eigenschaften und Methoden für Internet Explorer anzeigen.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-187">By typing **$ie | Get-Member**, you can view properties and methods for Internet Explorer.</span></span> <span data-ttu-id="f2cbd-188">Um das Internet Explorer-Fenster anzuzeigen, legen Sie die Eigenschaft „Visible“ auf „$true“ fest. Geben Sie dazu Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="f2cbd-188">To see the Internet Explorer window, set the Visible property to $true by typing:</span></span>

```powershell
$ie.Visible = $true
```

<span data-ttu-id="f2cbd-189">Anschließend können Sie mithilfe der Methode „Navigate“ zu einer bestimmten Webadresse navigieren:</span><span class="sxs-lookup"><span data-stu-id="f2cbd-189">You can then navigate to a specific Web address by using the Navigate method:</span></span>

```powershell
$ie.Navigate("http://www.microsoft.com/technet/scriptcenter/default.mspx")
```

<span data-ttu-id="f2cbd-190">Unter Verwendung anderer Elemente des Internet Explorer-Objektmodells können Sie Text-Inhalt von der Website abrufen.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-190">Using other members of the Internet Explorer object model, it is possible to retrieve text content from the Web page.</span></span> <span data-ttu-id="f2cbd-191">Mit dem folgenden Befehl können Sie den HTML-Text im Hauptteil der aktuellen Webseite anzeigen:</span><span class="sxs-lookup"><span data-stu-id="f2cbd-191">The following command will display the HTML text in the body of the current Web page:</span></span>

```powershell
$ie.Document.Body.InnerText
```

<span data-ttu-id="f2cbd-192">Rufen Sie die Methode „Quit()“ auf, um Internet Explorer aus PowerShell heraus zu schließen:</span><span class="sxs-lookup"><span data-stu-id="f2cbd-192">To close Internet Explorer from within PowerShell, call its Quit() method:</span></span>

```powershell
$ie.Quit()
```

<span data-ttu-id="f2cbd-193">Dadurch wird das Schließen von Internet Explorer erzwungen.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-193">This will force it to close.</span></span> <span data-ttu-id="f2cbd-194">Die Variable „$ie“ enthält keinen gültigen Verweis mehr, obwohl es sich noch um ein COM-Objekt zu handeln scheint.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-194">The $ie variable no longer contains a valid reference even though it still appears to be a COM object.</span></span> <span data-ttu-id="f2cbd-195">Wenn Sie die Variable verwenden, erhalten Sie einen Automatisierungsfehler:</span><span class="sxs-lookup"><span data-stu-id="f2cbd-195">If you attempt to use it, you will get an automation error:</span></span>

```
PS> $ie | Get-Member
Get-Member : Exception retrieving the string representation for property "Appli
cation" : "The object invoked has disconnected from its clients. (Exception fro
m HRESULT: 0x80010108 (RPC_E_DISCONNECTED))"
At line:1 char:16
+ $ie | Get-Member <<<<
```

<span data-ttu-id="f2cbd-196">Sie können entweder den verbleibenden Verweis mit einem Befehl wie „$ie = $null“ oder die Variable durch folgende Eingabe entfernen:</span><span class="sxs-lookup"><span data-stu-id="f2cbd-196">You can either remove the remaining reference with a command like $ie = $null, or completely remove the variable by typing:</span></span>

```powershell
Remove-Variable ie
```

> [!NOTE]
> <span data-ttu-id="f2cbd-197">Es gibt keinen allgemeinen Standard, der festlegt, ob ActiveX-EXE-Dateien beendet oder weiterhin ausgeführt werden, wenn Sie einen Verweis darauf entfernen.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-197">There is no common standard for whether ActiveX executables exit or continue to run when you remove a reference to one.</span></span> <span data-ttu-id="f2cbd-198">Je nach Situation, also z. B. abhängig davon, ob die Anwendung angezeigt, ein bearbeitetes Dokument darin ausgeführt oder Windows PowerShell noch ausgeführt wird, wird die Anwendung beendet oder auch nicht.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-198">Depending on circumstances such as whether the application is visible, whether an edited document is running in it, and even whether Windows PowerShell is still running, the application may or may not exit.</span></span> <span data-ttu-id="f2cbd-199">Aus diesem Grund sollten Sie das Abbruchverhalten für jede ActiveX-EXE-Datei testen, die Sie in Windows PowerShell verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-199">For this reason, you should test termination behavior for each ActiveX executable you want to use in Windows PowerShell.</span></span>

## <a name="getting-warnings-about-net-framework-wrapped-com-objects"></a><span data-ttu-id="f2cbd-200">Abrufen von Warnungen zu von .NET Framework umschlossenen COM-Objekten</span><span class="sxs-lookup"><span data-stu-id="f2cbd-200">Getting Warnings About .NET Framework-Wrapped COM Objects</span></span>

<span data-ttu-id="f2cbd-201">In einigen Fällen verfügt ein COM-Objekt möglicherweise über einen zugeordneten .NET Framework *Runtime-Callable Wrapper* oder RCW, und dieser wird von **New-Object** verwendet.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-201">In some cases, a COM object might have an associated .NET Framework *Runtime-Callable Wrapper* or RCW, and this will be used by **New-Object**.</span></span> <span data-ttu-id="f2cbd-202">Da das Verhalten des RCW möglicherweise vom Verhalten des normalen COM-Objekts abweicht, verfügt **New-Object** über einen **Strict**-Parameter, der Sie auf den RCW-Zugriff hinweist.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-202">Since the behavior of the RCW may be different from the behavior of the normal COM object, **New-Object** has a **Strict** parameter to warn you about RCW access.</span></span> <span data-ttu-id="f2cbd-203">Wenn Sie den Parameter **Strict** angeben und dann ein COM-Objekt erstellen, das einen RCW verwendet, wird eine Warnung angezeigt:</span><span class="sxs-lookup"><span data-stu-id="f2cbd-203">If you specify the **Strict** parameter and then create a COM object that uses an RCW, you get a warning message:</span></span>

```
PS> $xl = New-Object -ComObject Excel.Application -Strict
New-Object : The object written to the pipeline is an instance of the type "Mic
rosoft.Office.Interop.Excel.ApplicationClass" from the component's primary inte
rop assembly. If this type exposes different members than the IDispatch members
, scripts written to work with this object might not work if the primary intero
p assembly is not installed.
At line:1 char:17
+ $xl = New-Object  <<<< -ComObject Excel.Application -Strict
```

<span data-ttu-id="f2cbd-204">Das Objekt wird zwar erstellt, Sie werden jedoch darauf hingewiesen, dass es sich nicht um ein Standard-COM-Objekt handelt.</span><span class="sxs-lookup"><span data-stu-id="f2cbd-204">Although the object is still created, you are warned that it is not a standard COM object.</span></span>