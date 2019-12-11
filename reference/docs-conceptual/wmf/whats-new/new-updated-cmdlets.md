---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Neue und aktualisierte Cmdlets
ms.openlocfilehash: ffd5db2d4fc9bf8f67ef5e352633ad3209f72c87
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71147590"
---
# <a name="new-and-updated-cmdlets"></a><span data-ttu-id="c4f76-103">Neue und aktualisierte Cmdlets</span><span class="sxs-lookup"><span data-stu-id="c4f76-103">New and updated cmdlets</span></span>

<span data-ttu-id="c4f76-104">Wir haben basierend auf Feedback aus der Community neue Cmdlets hinzugefügt und vorhandene Cmdlets aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="c4f76-104">We have added new and updated existing cmdlets based on feedback from the community.</span></span>

## <a name="archive-cmdlets"></a><span data-ttu-id="c4f76-105">„Archive“-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="c4f76-105">Archive cmdlets</span></span>

<span data-ttu-id="c4f76-106">Die beiden neuen Cmdlets `Compress-Archive` und `Expand-Archive` ermöglichen das Komprimieren und Dekomprimieren von ZIP-Dateien.</span><span class="sxs-lookup"><span data-stu-id="c4f76-106">Two new cmdlets, `Compress-Archive` and `Expand-Archive`, let you compress and expand ZIP files.</span></span>

<span data-ttu-id="c4f76-107">Weitere Informationen erhalten Sie in der Dokumentation zum [Microsoft.Powershell.Archive](/powershell/module/microsoft.powershell.archive/)-Modul.</span><span class="sxs-lookup"><span data-stu-id="c4f76-107">For more information, see the [Microsoft.Powershell.Archive](/powershell/module/microsoft.powershell.archive/) module documentation.</span></span>

## <a name="catalog-cmdlets"></a><span data-ttu-id="c4f76-108">Katalog-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="c4f76-108">Catalog Cmdlets</span></span>

<span data-ttu-id="c4f76-109">Dem „Microsoft.PowerShell.Security“-Modul wurden zwei neue Cmdlets hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="c4f76-109">Two new cmdlets have been added in the Microsoft.PowerShell.Security module.</span></span>

- [<span data-ttu-id="c4f76-110">New-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="c4f76-110">New-FileCatalog</span></span>](/powershell/module/microsoft.powershell.security/New-FileCatalog)
- [<span data-ttu-id="c4f76-111">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="c4f76-111">Test-FileCatalog</span></span>](/powershell/module/microsoft.powershell.security/Test-FileCatalog)

<span data-ttu-id="c4f76-112">Diese generieren und überprüfen Windows-Katalogdateien.</span><span class="sxs-lookup"><span data-stu-id="c4f76-112">These generate and validate Windows catalog files.</span></span>

## <a name="clipboard-cmdlets"></a><span data-ttu-id="c4f76-113">„Clipboard“-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="c4f76-113">Clipboard cmdlets</span></span>

<span data-ttu-id="c4f76-114">Die Cmdlets `Get-Clipboard` und `Set-Clipboard` vereinfachen das Übertragen von Inhalten in eine und aus einer Windows PowerShell-Sitzung.</span><span class="sxs-lookup"><span data-stu-id="c4f76-114">`Get-Clipboard` and `Set-Clipboard` make it easier for you to transfer content to and from a Windows PowerShell session.</span></span> <span data-ttu-id="c4f76-115">Die „Clipboard“-Cmdlets unterstützen Bilder, Audiodateien, Dateilisten und Text.</span><span class="sxs-lookup"><span data-stu-id="c4f76-115">The Clipboard cmdlets support images, audio files, file lists, and text.</span></span>

<span data-ttu-id="c4f76-116">Weitere Informationen finden Sie unter:</span><span class="sxs-lookup"><span data-stu-id="c4f76-116">For more information, see:</span></span>

- [<span data-ttu-id="c4f76-117">Get-Clipboard</span><span class="sxs-lookup"><span data-stu-id="c4f76-117">Get-Clipboard</span></span>](/powershell/module/Microsoft.PowerShell.Management/Get-Clipboard)
- [<span data-ttu-id="c4f76-118">Set-Clipboard</span><span class="sxs-lookup"><span data-stu-id="c4f76-118">Set-Clipboard</span></span>](/powershell/module/Microsoft.PowerShell.Management/Set-Clipboard)

## <a name="cryptographic-message-syntax-cms-cmdlets"></a><span data-ttu-id="c4f76-119">CMS-Cmdlets (Cryptographic Message Syntax, Syntax verschlüsselter Nachrichten)</span><span class="sxs-lookup"><span data-stu-id="c4f76-119">Cryptographic Message Syntax (CMS) cmdlets</span></span>

<span data-ttu-id="c4f76-120">Die CMS-Cmdlets unterstützen die Ver- und Entschlüsselung von Inhalten mithilfe des IETF-Standardformats für kryptografisch geschützte Nachrichten, wie unter [RFC5652](https://tools.ietf.org/html/rfc5652.html) dokumentiert.</span><span class="sxs-lookup"><span data-stu-id="c4f76-120">The Cryptographic Message Syntax cmdlets support encryption and decryption of content using the IETF standard format for cryptographically protecting messages as documented by [RFC5652](https://tools.ietf.org/html/rfc5652.html).</span></span>

<span data-ttu-id="c4f76-121">Der CMS-Verschlüsselungsstandard implementiert die Verschlüsselung mit öffentlichem Schlüssel, bei der der Schlüssel zum Verschlüsseln von Inhalten (der *öffentliche Schlüssel*) und zum Entschlüsseln von Inhalten (der *private Schlüssel*) getrennt sind.</span><span class="sxs-lookup"><span data-stu-id="c4f76-121">The CMS encryption standard implements public key cryptography, where the key used to encrypt content (the *public key*) and the key used to decrypt content (the *private key*) are separate.</span></span>

<span data-ttu-id="c4f76-122">Ihr öffentlicher Schlüssel kann umfassend freigegeben werden, da seine Daten nicht vertraulich sind.</span><span class="sxs-lookup"><span data-stu-id="c4f76-122">Your public key can be shared widely and is not sensitive data.</span></span> <span data-ttu-id="c4f76-123">Jeder Inhalt, der mit dem öffentlichen Schlüssel verschlüsselt wurde, kann nur mit dem privaten Schlüssel entschlüsselt werden.</span><span class="sxs-lookup"><span data-stu-id="c4f76-123">Any content encrypted with the public key can only be decrypted using the private key.</span></span> <span data-ttu-id="c4f76-124">Weitere Informationen finden Sie unter [Public-Key-Verschlüsselungsverfahren](https://en.wikipedia.org/wiki/Public-key_cryptography).</span><span class="sxs-lookup"><span data-stu-id="c4f76-124">For more information, see [Public-key cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography).</span></span>

<span data-ttu-id="c4f76-125">Weitere Informationen finden Sie unter:</span><span class="sxs-lookup"><span data-stu-id="c4f76-125">For more information see:</span></span>

- [<span data-ttu-id="c4f76-126">Get-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="c4f76-126">Get-CmsMessage</span></span>](/powershell/module/Microsoft.PowerShell.Security/Get-CmsMessage)
- [<span data-ttu-id="c4f76-127">Protect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="c4f76-127">Protect-CmsMessage</span></span>](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage)
- [<span data-ttu-id="c4f76-128">Unprotect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="c4f76-128">Unprotect-CmsMessage</span></span>](/powershell/module/Microsoft.PowerShell.Security/unprotect-CmsMessage)

<span data-ttu-id="c4f76-129">Zertifikate erfordern einen eindeutigen Schlüsselverwendungsbezeichner wie „Codesignatur“ oder „Verschlüsselte E-Mail“, um sie als Datenverschlüsselungszertifikate in PowerShell zu kennzeichnen.</span><span class="sxs-lookup"><span data-stu-id="c4f76-129">Certificates require a unique key usage identifier (EKU), such as 'Code Signing' or 'Encrypted Mail', to identify them as data encryption certificates in PowerShell.</span></span> <span data-ttu-id="c4f76-130">Um Verschlüsselungszertifikate für Dokumente beim Zertifikatanbieter anzuzeigen, können Sie den dynamischen Parameter **DocumentEncryptionCert** von `Get-ChildItem` verwenden:</span><span class="sxs-lookup"><span data-stu-id="c4f76-130">To view document encryption certificates in the certificate provider, you can use the **DocumentEncryptionCert** dynamic parameter of `Get-ChildItem`:</span></span>

```powershell
Get-ChildItem Cert:\CurrentUser -DocumentEncryptionCert -Recurse
```

## <a name="extract-and-parse-structured-objects-from-string-content"></a><span data-ttu-id="c4f76-131">Extrahieren und Analysieren von strukturierten Objekten aus einer Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="c4f76-131">Extract and parse structured objects from string content</span></span>

### <a name="convertfrom-string"></a><span data-ttu-id="c4f76-132">ConvertFrom-String</span><span class="sxs-lookup"><span data-stu-id="c4f76-132">ConvertFrom-String</span></span>

<span data-ttu-id="c4f76-133">Das neue Cmdlet`ConvertFrom-String` unterstützt zwei Modi:</span><span class="sxs-lookup"><span data-stu-id="c4f76-133">The new `ConvertFrom-String` cmdlet supports two modes:</span></span>

- <span data-ttu-id="c4f76-134">Grundlegende, getrennte Analyse</span><span class="sxs-lookup"><span data-stu-id="c4f76-134">Basic delimited parsing</span></span>
- <span data-ttu-id="c4f76-135">Automatisch generierte, beispielgesteuerte Analyse</span><span class="sxs-lookup"><span data-stu-id="c4f76-135">Auto generated example-driven parsing</span></span>

<span data-ttu-id="c4f76-136">Bei der getrennten Analyse wird die Eingabe standardmäßig bei Leerzeichen getrennt, wobei den resultierenden Gruppen Eigenschaftsnamen zugewiesen werden.</span><span class="sxs-lookup"><span data-stu-id="c4f76-136">Delimited parsing, by default, splits the input at white space, and assigns property names to the resulting groups.</span></span>

<span data-ttu-id="c4f76-137">Der Parameter **UpdateTemplate** speichert die Ergebnisse des Lernalgorithmus in einem Kommentar in der Vorlagendatei.</span><span class="sxs-lookup"><span data-stu-id="c4f76-137">The **UpdateTemplate** parameter saves the results of the learning algorithm into a comment in the template file.</span></span> <span data-ttu-id="c4f76-138">Dadurch wird der Lernprozess (die langsamste Phase) zu einem einmaligen Aufwand.</span><span class="sxs-lookup"><span data-stu-id="c4f76-138">This makes the learning process (the slowest stage) a one-time cost.</span></span> <span data-ttu-id="c4f76-139">Das Ausführen von `ConvertFrom-String` mit einer Vorlage, die den codierten lernenden Algorithmus enthält, erfolgt nun fast unmittelbar.</span><span class="sxs-lookup"><span data-stu-id="c4f76-139">Running `ConvertFrom-String` with a template that contains the encoded learning algorithm is now nearly instantaneous.</span></span>

<span data-ttu-id="c4f76-140">Weitere Informationen finden Sie unter [ConvertFrom-String](/powershell/module/Microsoft.PowerShell.Utility/ConvertFrom-String).</span><span class="sxs-lookup"><span data-stu-id="c4f76-140">For more information, see [ConvertFrom-String](/powershell/module/Microsoft.PowerShell.Utility/ConvertFrom-String).</span></span>

### <a name="convert-string"></a><span data-ttu-id="c4f76-141">Convert-String</span><span class="sxs-lookup"><span data-stu-id="c4f76-141">Convert-String</span></span>

<span data-ttu-id="c4f76-142">`Convert-String` gestattet es Ihnen, „Vorher“- und „Nachher“-Beispiele dafür anzugeben, wie Text aussehen soll.</span><span class="sxs-lookup"><span data-stu-id="c4f76-142">`Convert-String` allows you to provide before and after examples of how you want text to look.</span></span> <span data-ttu-id="c4f76-143">Das Cmdlet formatiert Ihren Text dann automatisch.</span><span class="sxs-lookup"><span data-stu-id="c4f76-143">The cmdlet formats your text automatically.</span></span>

<span data-ttu-id="c4f76-144">Weitere Informationen finden Sie unter [Convert-String](/powershell/module/Microsoft.PowerShell.Utility/Convert-String).</span><span class="sxs-lookup"><span data-stu-id="c4f76-144">For more information, see [Convert-String](/powershell/module/Microsoft.PowerShell.Utility/Convert-String).</span></span>

## <a name="updates-to-fileinfo-object"></a><span data-ttu-id="c4f76-145">Aktualisierungen beim „FileInfo“-Objekt</span><span class="sxs-lookup"><span data-stu-id="c4f76-145">Updates to FileInfo object</span></span>

<span data-ttu-id="c4f76-146">Dateiversionsinformationen können irreführend sein, insbesondere in Fällen, bei denen die Datei geändert wurde.</span><span class="sxs-lookup"><span data-stu-id="c4f76-146">File version information can be misleading, especially in cases where the file was patched.</span></span> <span data-ttu-id="c4f76-147">WMF 5.0 fügt **FileInfo**-Objekten die neuen Skripteigenschaften **FileVersionRaw** und **ProductVersionRaw** hinzu.</span><span class="sxs-lookup"><span data-stu-id="c4f76-147">WMF 5.0 adds new **FileVersionRaw** and **ProductVersionRaw** script properties to **FileInfo** objects.</span></span>
<span data-ttu-id="c4f76-148">Es folgen die für „powershell.exe“ angezeigten Eigenschaften (vorausgesetzt wird, dass „$pid“ die ID des PowerShell-Prozesses ist):</span><span class="sxs-lookup"><span data-stu-id="c4f76-148">Here are the properties as displayed for powershell.exe (assuming $pid is the ID of the PowerShell process):</span></span>

```powershell
Get-Process -Id $pid -FileVersionInfo | Format-List *version*
```

```Output
FileVersionRaw    : 10.0.17763.1
ProductVersionRaw : 10.0.17763.1
FileVersion       : 10.0.17763.1 (WinBuild.160101.0800)
ProductVersion    : 10.0.17763.1
```

## <a name="format-hex"></a><span data-ttu-id="c4f76-149">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="c4f76-149">Format-Hex</span></span>

<span data-ttu-id="c4f76-150">Mit `Format-Hex` können Sie Text- und Binärdaten im Hexadezimalformat anzeigen.</span><span class="sxs-lookup"><span data-stu-id="c4f76-150">`Format-Hex` lets you view text or binary data in hexadecimal format.</span></span>

<span data-ttu-id="c4f76-151">Weitere Informationen finden Sie unter [Format-Hex](/powershell/module/microsoft.powershell.utility/format-hex).</span><span class="sxs-lookup"><span data-stu-id="c4f76-151">For more information, see [Format-Hex](/powershell/module/microsoft.powershell.utility/format-hex).</span></span>

## <a name="get-childitem-has--depth-parameter"></a><span data-ttu-id="c4f76-152">„Get-ChildItem“ mit „-Depth“-Parameter</span><span class="sxs-lookup"><span data-stu-id="c4f76-152">Get-ChildItem has -Depth parameter</span></span>

<span data-ttu-id="c4f76-153">`Get-ChildItem` enthält nun einen Parameter **Depth**, den Sie mit **Recurse** verwenden können, um die Rekursion zu begrenzen:</span><span class="sxs-lookup"><span data-stu-id="c4f76-153">`Get-ChildItem` now has a **Depth** parameter for use with **Recurse** to limit the recursion:</span></span>

## <a name="modules-support-for-declaring-version-ranges-1-etc"></a><span data-ttu-id="c4f76-154">Modulunterstützung für das Deklarieren von Versionsbereichen (1.\* usw.)</span><span class="sxs-lookup"><span data-stu-id="c4f76-154">Modules support for declaring version ranges (1.\*, etc)</span></span>

<span data-ttu-id="c4f76-155">Nun können Sie **MinimumVersion** und **MaximumVersion** kombinieren, um das Modul innerhalb eines bestimmten Bereichs zu importieren.</span><span class="sxs-lookup"><span data-stu-id="c4f76-155">You can now combine **MinimumVersion** and **MaximumVersion** to import module within specific range.</span></span> <span data-ttu-id="c4f76-156">Der Parameter unterstützt auch Platzhalterzeichen.</span><span class="sxs-lookup"><span data-stu-id="c4f76-156">The parameters also support wildcards.</span></span>

```powershell
Import-Module psreadline -Verbose -MinimumVersion 1.0 -MaximumVersion 1.2.*
```

```Output
VERBOSE: Loading module from path 'C:\Program Files\WindowsPowerShell\Modules\psreadline\1.1\psreadline.psd1'.
VERBOSE: Importing cmdlet 'Get-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Get-PSReadlineOption'.
VERBOSE: Importing cmdlet 'Remove-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineOption'.
VERBOSE: Importing function 'PSConsoleHostReadline'.
```

## <a name="new-guid"></a><span data-ttu-id="c4f76-157">New-Guid</span><span class="sxs-lookup"><span data-stu-id="c4f76-157">New-Guid</span></span>

<span data-ttu-id="c4f76-158">Es gibt viele Szenarien, in denen eindeutige Bezeichner erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="c4f76-158">There are many scenarios where youneed for unique identifier.</span></span> <span data-ttu-id="c4f76-159">Das Cmdlet `New-GUID`bietet eine einfache Möglichkeit zum Erstellen einer neuen GUID.</span><span class="sxs-lookup"><span data-stu-id="c4f76-159">The `New-GUID` cmdlet provides a simple way to create a new GUID.</span></span>

```powershell
New-Guid
```

```Output
Guid
----
e19d6ea5-3cc2-4db9-8095-0cdaed5a703d
```

## <a name="nonewline-parameter"></a><span data-ttu-id="c4f76-160">„NoNewLine“-Parameter</span><span class="sxs-lookup"><span data-stu-id="c4f76-160">NoNewLine parameter</span></span>

<span data-ttu-id="c4f76-161">`Out-File`, `Add-Content` und `Set-Content` verfügen nun über einen Schalter **NoNewline**, der eine neue Zeile hinter der Ausgabe weglässt.</span><span class="sxs-lookup"><span data-stu-id="c4f76-161">`Out-File`, `Add-Content`, and `Set-Content` now have a new **NoNewline** switch which omits a new line after the output.</span></span> <span data-ttu-id="c4f76-162">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="c4f76-162">For example:</span></span>

```powershell
"This is " | Out-File -FilePath Example.txt -NoNewline
"a single " | Add-Content -Path Example.txt -NoNewline
"sentence." | Add-Content -Path Example.txt -NoNewline
Get-Content .\Example.txt
```

```Output
This is a single sentence.
```

<span data-ttu-id="c4f76-163">Ohne Angabe von **NoNewline** befindet sich jedes Fragment in einer gesonderten Zeile:</span><span class="sxs-lookup"><span data-stu-id="c4f76-163">Without **NoNewline** specified, each fragment would be on a separate line:</span></span>

```powershell
"This is " | Out-File -FilePath Example.txt
"a single " | Add-Content -Path Example.txt
"sentence." | Add-Content -Path Example.txt
Get-Content .\Example.txt
```

```Output
This is
a single
sentence.
```

## <a name="interact-with-symbolic-links-using-improved-item-cmdlets"></a><span data-ttu-id="c4f76-164">Interagieren mit symbolischen Verknüpfungen mithilfe verbesserter „Item“-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="c4f76-164">Interact with Symbolic links using improved Item cmdlets</span></span>

<span data-ttu-id="c4f76-165">Zur Unterstützung symbolischer Verknüpfungen wurden das Item-Cmdlet und einige zugehörige Cmdlets erweitert.</span><span class="sxs-lookup"><span data-stu-id="c4f76-165">The Item cmdlet and a few related cmdlets have been extended to support symbolic links.</span></span>

### <a name="symbolic-link-files"></a><span data-ttu-id="c4f76-166">Symbolische Verknüpfungsdateien</span><span class="sxs-lookup"><span data-stu-id="c4f76-166">Symbolic link files</span></span>

<span data-ttu-id="c4f76-167">In diesem Beispiel erstellen wir eine neue symbolische Verknüpfungsdatei mit dem Namen „MySymLinkFile.txt“ in „C:\Temp“, die mit „$pshome\profile.ps1“ verknüpft ist.</span><span class="sxs-lookup"><span data-stu-id="c4f76-167">In this example, we create a new symbolic link file named MySymLinkFile.txt in C:\Temp which links to $pshome\profile.ps1.</span></span> <span data-ttu-id="c4f76-168">Alle drei Beispiele erzeugen dasselbe Ergebnis.</span><span class="sxs-lookup"><span data-stu-id="c4f76-168">All three examples produce the same result.</span></span>

```powershell
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
```

### <a name="symbolic-link-directories"></a><span data-ttu-id="c4f76-169">Symbolische Verknüpfungsverzeichnisse</span><span class="sxs-lookup"><span data-stu-id="c4f76-169">Symbolic link directories</span></span>

<span data-ttu-id="c4f76-170">In diesem Beispiel erstellen wir ein neues symbolisches Verknüpfungsverzeichnis mit dem Namen „MySymLinkDir“ in „C:\Temp“, das mit dem Ordner „$pshome“ verknüpft.</span><span class="sxs-lookup"><span data-stu-id="c4f76-170">In this example, we create a new symbolic link directory named MySymLinkDir in C:\Temp which links to the $pshome folder.</span></span> <span data-ttu-id="c4f76-171">Alle drei Beispiele erzeugen dasselbe Ergebnis.</span><span class="sxs-lookup"><span data-stu-id="c4f76-171">All three examples produce the same result.</span></span>

```powershell
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkDir -Value $pshome
```

### <a name="hard-links"></a><span data-ttu-id="c4f76-172">Feste Links</span><span class="sxs-lookup"><span data-stu-id="c4f76-172">Hard links</span></span>

<span data-ttu-id="c4f76-173">Dieselben Kombinationen von **Pfad** und **Namen** sind zulässig, wie oben beschrieben.</span><span class="sxs-lookup"><span data-stu-id="c4f76-173">The same combinations of **Path** and **Name** allowed as described above.</span></span>

```powershell
New-Item -ItemType HardLink -Path C:\Temp -Name MyHardLinkFile.txt -Value $pshome\profile.ps1
```

### <a name="directory-junctions"></a><span data-ttu-id="c4f76-174">Verzeichnisverbindungen</span><span class="sxs-lookup"><span data-stu-id="c4f76-174">Directory junctions</span></span>

<span data-ttu-id="c4f76-175">Dieselben Kombinationen von **Pfad** und **Namen** sind zulässig, wie oben beschrieben.</span><span class="sxs-lookup"><span data-stu-id="c4f76-175">The same combinations of **Path** and **Name** allowed as described above.</span></span>

```powershell
New-Item -ItemType Junction -Path C:\Temp\MyJunctionDir -Value $pshome
```

### <a name="get-childitem"></a><span data-ttu-id="c4f76-176">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="c4f76-176">Get-ChildItem</span></span>

<span data-ttu-id="c4f76-177">`Get-ChildItem` zeigt nun „l“ in der **Modus**-Eigenschaft an, um eine symbolische Verknüpfungsdatei bzw. ein symbolisches Verknüpfungsverzeichnis anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="c4f76-177">`Get-ChildItem` now displays an 'l' in the **Mode** property to indicate a symbolic link file or directory.</span></span>

```powershell
Get-ChildItem C:\Temp | sort LastWriteTime -Descending

Directory: C:\Temp

Mode       LastWriteTime Length Name
----       ------------- ------ ----
-a---- 6/13/2014 3:00 PM     16 File.txt
d----- 6/13/2014 3:00 PM        Directory
-a---l 6/13/2014 3:21 PM      0 MySymLinkFile.txt
d----l 6/13/2014 3:22 PM        MySymLinkDir
-a---l 6/13/2014 3:23 PM  23304 MyHardLinkFile.txt
d----l 6/13/2014 3:24 PM        MyJunctionDir
```

### <a name="remove-item"></a><span data-ttu-id="c4f76-178">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="c4f76-178">Remove-Item</span></span>

<span data-ttu-id="c4f76-179">Das Entfernen symbolischer Verknüpfungen funktioniert wie das Entfernen jedes anderen Elementtyps.</span><span class="sxs-lookup"><span data-stu-id="c4f76-179">Removing symbolic links works like removing any other item type.</span></span>

```powershell
Remove-Item C:\Temp\MySymLinkFile.txt
Remove-Item C:\Temp\MySymLinkDir
```

<span data-ttu-id="c4f76-180">Verwenden Sie den Parameter **Force**, um die Dateien im Zielverzeichnis und die symbolische Verknüpfung zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="c4f76-180">Use the **Force** parameter to remove the files in the target directory and the symbolic link.</span></span>

```powershell
Remove-Item C:\Temp\MySymLinkDir -Force
```

## <a name="new-temporaryfile"></a><span data-ttu-id="c4f76-181">New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="c4f76-181">New-TemporaryFile</span></span>

<span data-ttu-id="c4f76-182">Mitunter müssen Sie in Ihren Skripts eine temporäre Datei erstellen.</span><span class="sxs-lookup"><span data-stu-id="c4f76-182">Sometimes in your scripts, you must create a temporary file.</span></span> <span data-ttu-id="c4f76-183">Hierzu können Sie jetzt den Befehl `New-TemporaryFile` verwenden.</span><span class="sxs-lookup"><span data-stu-id="c4f76-183">You can now do this with the `New-TemporaryFile` cmdlet:</span></span>

```powershell
$tempFile = New-TemporaryFile
$tempFile.FullName
```

```Output
C:\Users\user1\AppData\Local\Temp\tmp375.tmp
```

## <a name="network-switch-management-with-powershell"></a><span data-ttu-id="c4f76-184">Verwalten von Netzwerkswitches mit PowerShell</span><span class="sxs-lookup"><span data-stu-id="c4f76-184">Network Switch Management with PowerShell</span></span>

<span data-ttu-id="c4f76-185">Die „NetworkSwitch“-Cmdlets, die in WMF 5.0 eingeführt wurden, ermöglichen Ihnen Netzwerkswitches, die mit dem Windows Server 2012 R2-Logo zertifiziert sind, mit einer Switch-, VLAN- und grundlegenden Layer 2-Netzwerkswitch-Konfiguration zu versehen.</span><span class="sxs-lookup"><span data-stu-id="c4f76-185">The Network Switch cmdlets, introduced in WMF 5.0, enable you to apply switch, virtual LAN (VLAN), and basic Layer 2 network switch port configuration to Windows Server 2012 R2 logo-certified network switches.</span></span> <span data-ttu-id="c4f76-186">Mithilfe dieser Cmdlets können Sie Folgendes ausführen:</span><span class="sxs-lookup"><span data-stu-id="c4f76-186">Using these cmdlets you can perform:</span></span>

- <span data-ttu-id="c4f76-187">Globale Switchkonfiguration, wie z. B.:</span><span class="sxs-lookup"><span data-stu-id="c4f76-187">Global switch configuration, such as:</span></span>
  - <span data-ttu-id="c4f76-188">Hostnamen festlegen</span><span class="sxs-lookup"><span data-stu-id="c4f76-188">Set host name</span></span>
  - <span data-ttu-id="c4f76-189">Switchbanner festlegen</span><span class="sxs-lookup"><span data-stu-id="c4f76-189">Set switch banner</span></span>
  - <span data-ttu-id="c4f76-190">Konfiguration dauerhaft speichern</span><span class="sxs-lookup"><span data-stu-id="c4f76-190">Persist configuration</span></span>
  - <span data-ttu-id="c4f76-191">Features aktivieren oder deaktivieren</span><span class="sxs-lookup"><span data-stu-id="c4f76-191">Enable or disable feature</span></span>

- <span data-ttu-id="c4f76-192">VLAN-Konfiguration:</span><span class="sxs-lookup"><span data-stu-id="c4f76-192">VLAN configuration:</span></span>
  - <span data-ttu-id="c4f76-193">VLAN erstellen oder entfernen</span><span class="sxs-lookup"><span data-stu-id="c4f76-193">Create or remove VLAN</span></span>
  - <span data-ttu-id="c4f76-194">VLAN aktivieren oder deaktivieren</span><span class="sxs-lookup"><span data-stu-id="c4f76-194">Enable or disable VLAN</span></span>
  - <span data-ttu-id="c4f76-195">VLAN auflisten</span><span class="sxs-lookup"><span data-stu-id="c4f76-195">Enumerate VLAN</span></span>
  - <span data-ttu-id="c4f76-196">Anzeigenamen für ein VLAN festlegen</span><span class="sxs-lookup"><span data-stu-id="c4f76-196">Set friendly name to a VLAN</span></span>

- <span data-ttu-id="c4f76-197">Layer 2-Portkonfiguration:</span><span class="sxs-lookup"><span data-stu-id="c4f76-197">Layer 2 port configuration:</span></span>
  - <span data-ttu-id="c4f76-198">Ports auflisten</span><span class="sxs-lookup"><span data-stu-id="c4f76-198">Enumerate ports</span></span>
  - <span data-ttu-id="c4f76-199">Ports aktivieren oder deaktivieren</span><span class="sxs-lookup"><span data-stu-id="c4f76-199">Enable or disable ports</span></span>
  - <span data-ttu-id="c4f76-200">Portmodi und -eigenschaften festlegen</span><span class="sxs-lookup"><span data-stu-id="c4f76-200">Set port modes and properties</span></span>
  - <span data-ttu-id="c4f76-201">VLAN im Modus „Access“ oder „Trunk“ für den Port hinzufügen oder zuordnen</span><span class="sxs-lookup"><span data-stu-id="c4f76-201">Add or associate VLAN to Trunk or Access on the port</span></span>

<span data-ttu-id="c4f76-202">Weitere Informationen finden Sie in der [NetworkSwitchManager](/powershell/module/networkswitchmanager/)-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="c4f76-202">For more information, see the [NetworkSwitchManager](/powershell/module/networkswitchmanager/) documentation.</span></span>

## <a name="generate-powershell-cmdlets-based-on-an-odata-endpoint-with-odatautils"></a><span data-ttu-id="c4f76-203">Generieren von PowerShell-Cmdlets basierend auf einem OData-Endpunkt mit ODataUtils</span><span class="sxs-lookup"><span data-stu-id="c4f76-203">Generate PowerShell cmdlets based on an OData endpoint with ODataUtils</span></span>

<span data-ttu-id="c4f76-204">Das „ODataUtils“-Modul ermöglicht die Generierung von PowerShell-Cmdlets anhand von REST-Endpunkten, die OData unterstützen.</span><span class="sxs-lookup"><span data-stu-id="c4f76-204">The ODataUtils module allows generation of PowerShell cmdlets from REST endpoints that support OData.</span></span> <span data-ttu-id="c4f76-205">Das „Microsoft.PowerShell.ODataUtils“-Modul umfasst die folgenden Features:</span><span class="sxs-lookup"><span data-stu-id="c4f76-205">The Microsoft.PowerShell.ODataUtils module includes the following features:</span></span>

- <span data-ttu-id="c4f76-206">Übertragen zusätzlicher Informationen vom serverseitigen Endpunkt zur Clientseite</span><span class="sxs-lookup"><span data-stu-id="c4f76-206">Channel additional information from server-side endpoint to client side.</span></span>
- <span data-ttu-id="c4f76-207">Unterstützung einer clientseitigen Auslagerung</span><span class="sxs-lookup"><span data-stu-id="c4f76-207">Client-side paging support</span></span>
- <span data-ttu-id="c4f76-208">Serverseitige Filterung mithilfe des „-Select“-Parameters</span><span class="sxs-lookup"><span data-stu-id="c4f76-208">Server-side filtering by using the -Select parameter</span></span>
- <span data-ttu-id="c4f76-209">Unterstützung für Webanforderungsheader</span><span class="sxs-lookup"><span data-stu-id="c4f76-209">Support for web request headers</span></span>

<span data-ttu-id="c4f76-210">Die vom `Export-ODataEndPointProxy`-Cmdlet generierten „Proxy“-Cmdlets bieten zusätzliche Informationen vom serverseitigen OData-Endpunkt zum **Information**sdatenstrom.</span><span class="sxs-lookup"><span data-stu-id="c4f76-210">The proxy cmdlets generated by the `Export-ODataEndPointProxy` cmdlet provide additional information from the server-side OData endpoint on the **Information** stream.</span></span>

```powershell
Import-Module Microsoft.PowerShell.ODataUtils -Force
$generatedProxyModuleDir = Join-Path -Path $env:SystemDrive -ChildPath 'ODataDemoProxy'
$uri = "http://services.odata.org/V3/(S(fhleiief23wrm5a5nhf542q5))/OData/OData.svc/"
Export-ODataEndpointProxy -Uri $uri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -AllowClobber
```

<span data-ttu-id="c4f76-211">Im folgenden Beispiel rufen wir das Top-Produkt ab und erfassen die Ausgabe in der Variablen `$infoStream`.</span><span class="sxs-lookup"><span data-stu-id="c4f76-211">In the following example, we are retrieving top product and capturing the output in the `$infoStream` variable.</span></span>

<span data-ttu-id="c4f76-212">Durch Angabe des Parameters **IncludeTotalResponseCount** erhalten wir die Gesamtzahl aller **Produkt**-Datensätze, die auf dem Server verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="c4f76-212">By specifying **IncludeTotalResponseCount** parameter, we get the total count of all the **Product** records available on the server.</span></span>

```powershell
Import-Module $generatedProxyModuleDir -Force
$product = Get-Product -Top 1 -AllowUnsecureConnection -AllowAdditionalData -IncludeTotalResponseCount -InformationVariable infoStream
$additionalInfo = $infoStream.GetEnumerator() | % MessageData
$additionalInfo['odata.count']
```

<span data-ttu-id="c4f76-213">Sie können die Datensätze vom Server mithilfe der Unterstützung clientseitiger Auslagerung in Batches abrufen.</span><span class="sxs-lookup"><span data-stu-id="c4f76-213">You can get the records from the server in batches using client-side paging support.</span></span> <span data-ttu-id="c4f76-214">Dies ist hilfreich, wenn Sie eine große Datenmenge vom Server über das Netzwerk abrufen müssen.</span><span class="sxs-lookup"><span data-stu-id="c4f76-214">This is useful when you must get a large amount of data from the server over the network.</span></span>

```powershell
$skipCount = 0
$batchSize = 3
while($skipCount -le $additionalInfo['odata.count'])
{
  Get-Product -AllowUnsecureConnection -AllowAdditionalData -Top $batchSize -Skip $skipCount
  $skipCount += $batchSize
}
```

<span data-ttu-id="c4f76-215">Die generierten „Proxy“-Cmdlets unterstützen den **Select**-Parameter, der als Filter verwendet wird, um nur die Datensatzeigenschaften zu empfangen, die der Client benötigt.</span><span class="sxs-lookup"><span data-stu-id="c4f76-215">The generated proxy cmdlets support the **Select** parameter that is used as a filter to receive only the record properties that the client needs.</span></span> <span data-ttu-id="c4f76-216">Die Filterung erfolgt auf dem Server, was die Menge der Daten reduziert, die über das Netzwerk übertragen werden.</span><span class="sxs-lookup"><span data-stu-id="c4f76-216">The filtering occurs on the server, which reduces the amount of data that is transferred over the network.</span></span>

```powershell
Get-Product -Top 2 -AllowUnsecureConnection -AllowAdditionalData -Select Name
```

<span data-ttu-id="c4f76-217">Das `Export-ODataEndpointProxy`-Cmdlet und die von diesem generierten „Proxy“-Cmdlets unterstützen jetzt den Parameter **Headers**.</span><span class="sxs-lookup"><span data-stu-id="c4f76-217">The `Export-ODataEndpointProxy` cmdlet, and the proxy cmdlets generated by it, now support the **Headers** parameter.</span></span> <span data-ttu-id="c4f76-218">Der Header kann verwendet werden, um zusätzliche Informationen, die vom OData-Endpunkt erwartet werden, zu übertragen.</span><span class="sxs-lookup"><span data-stu-id="c4f76-218">The header can be used to channel additional information expected by the OData endpoint.</span></span>

<span data-ttu-id="c4f76-219">Im folgenden Beispiel wird dem Parameter**Headers** eine Hashtabelle bereitgestellt, die einen Abonnementschlüssel enthält.</span><span class="sxs-lookup"><span data-stu-id="c4f76-219">In the following example, a hash table containing a Subscription key is provided to the **Headers** parameter.</span></span> <span data-ttu-id="c4f76-220">Dies ist ein typisches Beispiel für Dienste, die einen Abonnementschlüssel für die Authentifizierung erwarten.</span><span class="sxs-lookup"><span data-stu-id="c4f76-220">This is a typical example for services that are expecting a Subscription key for authentication.</span></span>

```powershell
Export-ODataEndpointProxy -Uri $endPointUri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -Headers @{'subscription-key'='XXXX'}
```
