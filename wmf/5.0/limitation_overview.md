---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 4b006d2ac812abf1f281b6b4e382c2760f92a95c
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2018
---
# <a name="known-issues-and-limitations"></a><span data-ttu-id="5899f-102">Bekannte Probleme und Einschränkungen</span><span class="sxs-lookup"><span data-stu-id="5899f-102">Known Issues and Limitations</span></span>

<a name="powershell-shortcuts-are-broken-when-used-for-the-first-time"></a><span data-ttu-id="5899f-103">PowerShell-Verknüpfungen sind beim ersten Verwenden unterbrochen</span><span class="sxs-lookup"><span data-stu-id="5899f-103">PowerShell Shortcuts are broken when used for the first time</span></span>
------------------------------------------------------------

<span data-ttu-id="5899f-104">**Lösung:** Führen Sie eine der folgenden Aktionen aus:</span><span class="sxs-lookup"><span data-stu-id="5899f-104">**Resolution:** Perform one of the following actions:</span></span>

1.  <span data-ttu-id="5899f-105">Klicken Sie mit der rechten Maustaste auf die PowerShell-Verknüpfung.</span><span class="sxs-lookup"><span data-stu-id="5899f-105">Right click on the PowerShell shortcut.</span></span> <span data-ttu-id="5899f-106">Wählen Sie „Windows PowerShell“ aus, um in einem Modus ohne erhöhte Rechte zu starten.</span><span class="sxs-lookup"><span data-stu-id="5899f-106">Select “Windows PowerShell” to launch in a non-elevated mode.</span></span>
2.  <span data-ttu-id="5899f-107">Klicken Sie mit der rechten Maustaste auf die PowerShell-Verknüpfung.</span><span class="sxs-lookup"><span data-stu-id="5899f-107">Right click on the PowerShell shortcut.</span></span> <span data-ttu-id="5899f-108">Klicken Sie mit der rechten Maustaste auf „Windows PowerShell“, und wählen Sie „Als Administrator ausführen“ aus, um im Modus mit erhöhten Rechten zu starten.</span><span class="sxs-lookup"><span data-stu-id="5899f-108">Right click on “Windows PowerShell” and select “Run As Administrator” to launch in an elevated mode.</span></span>

<span data-ttu-id="5899f-109">Nachdem Sie eine der oben aufgeführten Aktionen ausgeführt haben, funktionieren die PowerShell-Verknüpfungen.</span><span class="sxs-lookup"><span data-stu-id="5899f-109">Once you have performed either of the above actions, the PowerShell shortcuts will work.</span></span> <span data-ttu-id="5899f-110">Diese Aktionen müssen nur einmal ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="5899f-110">These actions need to be performed only once.</span></span>


<a name="powershell-modules-and-dsc-resources-report-errors-about-executionpolicy-on-windows-7"></a><span data-ttu-id="5899f-111">PowerShell-Module und DSC-Ressourcen melden Fehler zu „ExecutionPolicy“ unter Windows 7</span><span class="sxs-lookup"><span data-stu-id="5899f-111">PowerShell Modules and DSC Resources report errors about ExecutionPolicy on Windows 7</span></span>
-------------------------------------------------------------------------------------
<span data-ttu-id="5899f-112">Unter Windows 7 kann die Verwendung von PowerShell-Modulen und DSC-Ressourcen zu Fehlern führen, die zu „ExecutionPolicy“ gemeldet werden.</span><span class="sxs-lookup"><span data-stu-id="5899f-112">On Windows 7, the use of PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

<span data-ttu-id="5899f-113">**Lösung:** Legen Sie „ExecutionPolicy“ auf „RemoteSigned“ fest, indem Sie den folgenden Befehl mit erhöhten Rechten in einer PowerShell-Sitzung ausführen (Als Administrator ausführen):</span><span class="sxs-lookup"><span data-stu-id="5899f-113">**Resolution:** Set the ExecutionPolicy to RemoteSigned by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```

<a name="connecting-to-an-old-remote-exchange-endpoint-causes-a-crash"></a><span data-ttu-id="5899f-114">Herstellen einer Verbindung mit einem alten Exchange- Remoteendpunkt führt zum Absturz</span><span class="sxs-lookup"><span data-stu-id="5899f-114">Connecting to an old remote Exchange endpoint causes a crash</span></span>
------------------------------------------------------------

<span data-ttu-id="5899f-115">Der alte Exchange-Endpunkt wird zu einem neuen Endpunkt umgeleitet.</span><span class="sxs-lookup"><span data-stu-id="5899f-115">The old Exchange endpoint redirects to a new endpoint.</span></span> <span data-ttu-id="5899f-116">Die Umleitungslogik weist einen Fehler auf, der zu einem Absturz führt.</span><span class="sxs-lookup"><span data-stu-id="5899f-116">There is a bug in the redirection logic that results in a crash.</span></span>

<span data-ttu-id="5899f-117">**Lösung:** Stellen Sie eine direkte Verbindung mit dem neuen Endpunkt her.</span><span class="sxs-lookup"><span data-stu-id="5899f-117">**Resolution:** Connect directly to the new endpoint.</span></span>


<a name="software-inventory-logging-feature-is-erroneously-stopped-after-wmf-50-installation-on-windows-server-2012-r2"></a><span data-ttu-id="5899f-118">Das Feature „Protokollierung des Softwarebestands“ wird nach der Installation von WMF 5.0 unter Windows Server 2012 R2 fälschlicherweise beendet</span><span class="sxs-lookup"><span data-stu-id="5899f-118">Software Inventory Logging feature is erroneously stopped after WMF 5.0 installation on Windows Server 2012 R2</span></span>
-------------------------------------------------------------------------------------------------------------

<span data-ttu-id="5899f-119">Wenn WMF 5.0 auf einem Computer mit Windows Server 2012 R2 installiert wird, auf dem die Protokollierung des Softwarebestands bereits ausgeführt wird, wird dieses Feature nach der Installation fälschlicherweise beendet.</span><span class="sxs-lookup"><span data-stu-id="5899f-119">When installing WMF 5.0 on a Windows Server 2012 R2 that is already running SIL, the Software Inventory Logging feature is erroneously stopped after installation.</span></span>

<span data-ttu-id="5899f-120">**Lösung:** Führen Sie das Cmdlet „Start-SilLogging“ nach der Installation von WMF aus, da der Installationsvorgang fälschlicherweise das Feature „Protokollierung des Softwarebestands“ beendet.</span><span class="sxs-lookup"><span data-stu-id="5899f-120">**Resolution:** Run the Start-SilLogging cmdlet once after the WMF installation, as the installation process will errantly stop the Software Inventory Logging feature.</span></span>

<a name="get-childitem-does-not-work-if--literalpath-and--recurse-are-used-together"></a><span data-ttu-id="5899f-121">„Get-ChildItem“ funktioniert nicht, wenn „-LiteralPath“ und „-Recurse“ zusammen verwendet werden</span><span class="sxs-lookup"><span data-stu-id="5899f-121">Get-ChildItem does not work if -LiteralPath and -Recurse are used together</span></span>
--------------------------------------------------------------------------

<span data-ttu-id="5899f-122">Wenn ein Verzeichnisname ein ungültiges Platzhalterzeichen enthält, liefert „Get-ChildItem“ nicht die erwarteten Ergebnisse, wenn „-LiteralPath“ und „-Recurse“ zusammen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="5899f-122">If a directory name contains an invalid wildcard character, then Get-ChildItem will not produce expected results when both -LiteralPath and -Recurse are used together.</span></span>

<span data-ttu-id="5899f-123">**Lösung:** Die aktuelle, allerdings nicht ideale Umgehung ist das Implementieren der Rekursion im Skript, anstatt das Cmdlet zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="5899f-123">**Resolution:** Not ideal, but current workaround is to implement recursion in the script rather than rely on the cmdlet.</span></span>


<a name="sysprep-fails-after-wmf-50-installation"></a><span data-ttu-id="5899f-124">Sysrep schlägt nach der Installation von WMF 5.0 fehl.</span><span class="sxs-lookup"><span data-stu-id="5899f-124">Sysprep fails after WMF 5.0 installation</span></span>
----------------------------------------

<span data-ttu-id="5899f-125">Es gibt zwei Problemumgehungen für dieses Problem, abhängig davon, welche Version von Windows Server Sie ausführen.</span><span class="sxs-lookup"><span data-stu-id="5899f-125">There are two workarounds for this issue depending on the version of Windows Server you are running.</span></span>

<span data-ttu-id="5899f-126">**Lösung:**</span><span class="sxs-lookup"><span data-stu-id="5899f-126">**Resolution:**</span></span>
- <span data-ttu-id="5899f-127">Für Systeme, die **Windows Server 2008 R2** ausführen</span><span class="sxs-lookup"><span data-stu-id="5899f-127">For systems running **Windows Server 2008 R2**</span></span>
  1. <span data-ttu-id="5899f-128">Öffnen Sie PowerShell als Administrator.</span><span class="sxs-lookup"><span data-stu-id="5899f-128">Open Powershell as an administrator</span></span>
  2. <span data-ttu-id="5899f-129">Führen Sie den folgenden Befehl aus.</span><span class="sxs-lookup"><span data-stu-id="5899f-129">Run the following command</span></span>

  ```powershell
    Set-SilLogging –TargetUri https://BlankTarget –CertificateThumbprint 0123456789
  ```
  3. <span data-ttu-id="5899f-130">Führen Sie den Befehl aus, und ignorieren Sie die Fehler, da diese zu erwarten sind.</span><span class="sxs-lookup"><span data-stu-id="5899f-130">Run the command and ignore the error, as they are expected.</span></span>

  ```powershell
    Publish-SilData
   ```
  4. <span data-ttu-id="5899f-131">Löschen Sie die Dateien im Verzeichnis \Windows\System32\Logfiles\SIL\.</span><span class="sxs-lookup"><span data-stu-id="5899f-131">Delete the files in  \Windows\System32\Logfiles\SIL\ directory</span></span>

  ```powershell
    Remove-Item -Recurse $env:SystemRoot\System32\Logfiles\SIL\
  ```
  5. <span data-ttu-id="5899f-132">Installieren Sie alle verfügbaren wichtigen Windows-Updates und beginnen Sie normal mit dem Sysyprep-Vorgang.</span><span class="sxs-lookup"><span data-stu-id="5899f-132">Install all available important Windows Updates, and begin Sysyprep operation normally.</span></span>

- <span data-ttu-id="5899f-133">Für Systeme, die **Windows Server 2012** ausführen</span><span class="sxs-lookup"><span data-stu-id="5899f-133">For systems running **Windows Server 2012**</span></span>
  1.    <span data-ttu-id="5899f-134">Nach der Installation von WMF 5.0 auf dem Server, der mit Sysrep vorbereitet werden soll, melden Sie sich als Administrator an.</span><span class="sxs-lookup"><span data-stu-id="5899f-134">After installing WMF 5.0 on the server to be Sysprep’d, login as administrator.</span></span>
  2.    <span data-ttu-id="5899f-135">Kopieren Sie „Generize.xml“ aus dem Verzeichnis \Windows\System32\Sysprep\ActionFiles\ an einen Ort außerhalb des Windows-Verzeichnisses, z.B. C:\.</span><span class="sxs-lookup"><span data-stu-id="5899f-135">Copy Generize.xml from directory \Windows\System32\Sysprep\ActionFiles\ to a location outside of the Windows directory, C:\ for example.</span></span>
  3.    <span data-ttu-id="5899f-136">Öffnen Sie die „Generalize.xml“-Kopie mit dem Editor.</span><span class="sxs-lookup"><span data-stu-id="5899f-136">Open your Generalize.xml copy with notepad.</span></span>
  4.    <span data-ttu-id="5899f-137">Suchen und entfernen Sie den folgenden Text. Eine Instanz von jedem Textelement muss gelöscht werden (sie sind fast am Ende des Dokuments zu finden).</span><span class="sxs-lookup"><span data-stu-id="5899f-137">Find and remove the following text, one instance of each needs to be deleted (they will be near the end of the document).</span></span>

    ```
    <sysprepOrder order="0x3200"></sysprepOrder>
    <sysprepOrder order="0x3300"></sysprepOrder>
    ```

  5.    <span data-ttu-id="5899f-138">Speichern Sie die bearbeitete Kopie von „Generalize.xml“, und schließen Sie die Datei.</span><span class="sxs-lookup"><span data-stu-id="5899f-138">Save the edited copy of Generalize.xml and close the file.</span></span>
  6.    <span data-ttu-id="5899f-139">Öffnen Sie eine Eingabeaufforderung als Administrator.</span><span class="sxs-lookup"><span data-stu-id="5899f-139">Open a command prompt as administrator</span></span>
  7.    <span data-ttu-id="5899f-140">Führen Sie den folgenden Befehl aus, um die „Generalize.xml“-Datei im Ordner „system32“ in Besitz zu nehmen.</span><span class="sxs-lookup"><span data-stu-id="5899f-140">Run the following command to take ownership of the Generalize.xml file in system32 folder:</span></span>

    ```
    Takeown /f C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
    ```

  8.    <span data-ttu-id="5899f-141">Führen Sie den folgenden Befehl aus, um die entsprechende Berechtigung für die Datei festzulegen:</span><span class="sxs-lookup"><span data-stu-id="5899f-141">Run the following command to set appropriate permission on the file:</span></span>

    ```
    Cacls C:\Windows\System32\ Sysprep\ActionFiles\Generalize.xml /G `<AdministratorUserName>`:F
    ```
      * <span data-ttu-id="5899f-142">Geben Sie bei der Aufforderung zur Bestätigung geben „Ja“ an.</span><span class="sxs-lookup"><span data-stu-id="5899f-142">Answer Yes at the prompt for confirmation.</span></span>
      * <span data-ttu-id="5899f-143">Beachten Sie, dass `<AdministratorUserName>` durch den Benutzernamen ersetzt werden sollte, der Administrator auf dem Computer ist.</span><span class="sxs-lookup"><span data-stu-id="5899f-143">Note that `<AdministratorUserName>` should be replaced by the username who is administrator on the machine.</span></span> <span data-ttu-id="5899f-144">Beispiel: „Administrator“.</span><span class="sxs-lookup"><span data-stu-id="5899f-144">For example, "Administrator".</span></span>

  9.    <span data-ttu-id="5899f-145">Kopieren Sie die von Ihnen bearbeitete und gespeicherte Datei mit dem folgenden Befehl in das Sysprep-Verzeichnis:</span><span class="sxs-lookup"><span data-stu-id="5899f-145">Copy the file you edited and saved over to the Sysprep directory using the following command:</span></span>

    ```
    xcopy C:\Generalize.xml C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
    ```
      * <span data-ttu-id="5899f-146">Geben Sie „Ja“ an, um die Datei zu überschreiben (Überprüfen Sie nochmal den Pfad, den Sie eingegeben haben, falls keine Aufforderung zum Überschreiben erscheint).</span><span class="sxs-lookup"><span data-stu-id="5899f-146">Answer Yes to overwrite (note that if there is no prompt to overwrite, double check the path entered).</span></span>
      * <span data-ttu-id="5899f-147">Es wird davon ausgegangen, dass Ihre bearbeitete Kopie von „Generalize.xml“ nach C:\ kopiert wurde.</span><span class="sxs-lookup"><span data-stu-id="5899f-147">Assumes your edited copy of Generalize.xml was copied to C:\ .</span></span>

  10.   <span data-ttu-id="5899f-148">„Generalize.XML“ wird jetzt mit der Problemumgehung aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="5899f-148">Generalize.xml is now updated with the workaround.</span></span> <span data-ttu-id="5899f-149">Führen Sie Sysprep bitte mit der aktivierten Generalisierungsoption aus.</span><span class="sxs-lookup"><span data-stu-id="5899f-149">Please run Sysprep with the generalize option enabled.</span></span>
