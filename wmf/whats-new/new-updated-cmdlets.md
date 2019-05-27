---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Neue und aktualisierte Cmdlets
ms.openlocfilehash: 9ec31c89c0bc4b111b40e2d4725fa0782a573204
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855545"
---
# <a name="new-and-updated-cmdlets"></a>Neue und aktualisierte Cmdlets

Wir haben basierend auf Feedback aus der Community neue Cmdlets hinzugefügt und vorhandene Cmdlets aktualisiert.

## <a name="archive-cmdlets"></a>„Archive“-Cmdlets

Die beiden neuen Cmdlets `Compress-Archive` und `Expand-Archive` ermöglichen das Komprimieren und Dekomprimieren von ZIP-Dateien.

Weitere Informationen erhalten Sie in der Dokumentation zum [Microsoft.Powershell.Archive](/powershell/module/microsoft.powershell.archive/)-Modul.

## <a name="catalog-cmdlets"></a>Katalog-Cmdlets

Dem „Microsoft.PowerShell.Security“-Modul wurden zwei neue Cmdlets hinzugefügt.

- [New-FileCatalog](/powershell/module/microsoft.powershell.security/New-FileCatalog)
- [Test-FileCatalog](/powershell/module/microsoft.powershell.security/Test-FileCatalog)

Diese generieren und überprüfen Windows-Katalogdateien.

## <a name="clipboard-cmdlets"></a>„Clipboard“-Cmdlets

Die Cmdlets `Get-Clipboard` und `Set-Clipboard` vereinfachen das Übertragen von Inhalten in eine und aus einer Windows PowerShell-Sitzung. Die „Clipboard“-Cmdlets unterstützen Bilder, Audiodateien, Dateilisten und Text.

Weitere Informationen finden Sie unter:

- [Get-Clipboard](/powershell/module/Microsoft.PowerShell.Management/Get-Clipboard)
- [Set-Clipboard](/powershell/module/Microsoft.PowerShell.Management/Set-Clipboard)

## <a name="cryptographic-message-syntax-cms-cmdlets"></a>CMS-Cmdlets (Cryptographic Message Syntax, Syntax verschlüsselter Nachrichten)

Der CMS-Cmdlets unterstützen die Ver- und Entschlüsselung von Inhalten mithilfe des IETF-Standardformats für kryptografisch geschützte Nachrichten, wie unter [RFC5652](https://tools.ietf.org/html/rfc5652) dokumentiert.

Der CMS-Verschlüsselungsstandard implementiert die Verschlüsselung mit öffentlichem Schlüssel, bei der der Schlüssel zum Verschlüsseln von Inhalten (der *öffentliche Schlüssel*) und zum Entschlüsseln von Inhalten (der *private Schlüssel*) getrennt sind.

Ihr öffentlicher Schlüssel kann umfassend freigegeben werden, da seine Daten nicht vertraulich sind. Jeder Inhalt, der mit dem öffentlichen Schlüssel verschlüsselt wurde, kann nur mit dem privaten Schlüssel entschlüsselt werden. Weitere Informationen finden Sie unter [Public-Key-Verschlüsselungsverfahren](https://en.wikipedia.org/wiki/Public-key_cryptography).

Weitere Informationen finden Sie unter:

- [Get-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/Get-CmsMessage.md)
- [Protect-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage.md)
- [Unprotect-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/rotect-CmsMessage.md)

Zertifikate erfordern einen eindeutigen Schlüsselverwendungsbezeichner wie „Codesignatur“ oder „Verschlüsselte E-Mail“, um sie als Datenverschlüsselungszertifikate in PowerShell zu kennzeichnen. Um Verschlüsselungszertifikate für Dokumente beim Zertifikatanbieter anzuzeigen, können Sie den dynamischen Parameter **DocumentEncryptionCert** von `Get-ChildItem` verwenden:

```powershell
Get-ChildItem Cert:\CurrentUser -DocumentEncryptionCert -Recurse
```

## <a name="extract-and-parse-structured-objects-from-string-content"></a>Extrahieren und Analysieren von strukturierten Objekten aus einer Zeichenfolge

### <a name="convertfrom-string"></a>ConvertFrom-String

Das neue Cmdlet`ConvertFrom-String` unterstützt zwei Modi:

- Grundlegende, getrennte Analyse
- Automatisch generierte, beispielgesteuerte Analyse

Bei der getrennten Analyse wird die Eingabe standardmäßig bei Leerzeichen getrennt, wobei den resultierenden Gruppen Eigenschaftsnamen zugewiesen werden.

Der Parameter **UpdateTemplate** speichert die Ergebnisse des Lernalgorithmus in einem Kommentar in der Vorlagendatei. Dadurch wird der Lernprozess (die langsamste Phase) zu einem einmaligen Aufwand. Das Ausführen von `ConvertFrom-String` mit einer Vorlage, die den codierten lernenden Algorithmus enthält, erfolgt nun fast unmittelbar.

Weitere Informationen finden Sie unter [ConvertFrom-String](/powershell/module/Microsoft.PowerShell.Utility/ConvertFrom-String).

### <a name="convert-string"></a>Convert-String

`Convert-String` gestattete es Ihnen, „Vorher“- und „Nachher“-Beispiele dafür anzugeben, wie Text aussehen soll. Das Cmdlet formatiert Ihren Text dann automatisch.

Weitere Informationen finden Sie unter [Convert-String](/powershell/module/Microsoft.PowerShell.Utility/Convert-String).

## <a name="updates-to-fileinfo-object"></a>Aktualisierungen beim „FileInfo“-Objekt

Dateiversionsinformationen können irreführend sein, insbesondere in Fällen, bei denen die Datei geändert wurde. WMF 5.0 fügt **FileInfo**-Objekten die neuen Skripteigenschaften **FileVersionRaw** und **ProductVersionRaw** hinzu.
Es folgen die für „powershell.exe“ angezeigten Eigenschaften (vorausgesetzt wird, dass „$pid“ die ID des PowerShell-Prozesses ist):

```powershell
Get-Process -Id $pid -FileVersionInfo | Format-List *version*
```

```Output
FileVersionRaw    : 10.0.17763.1
ProductVersionRaw : 10.0.17763.1
FileVersion       : 10.0.17763.1 (WinBuild.160101.0800)
ProductVersion    : 10.0.17763.1
```

## <a name="format-hex"></a>Format-Hex

Mit `Format-Hex` können Sie Text- und Binärdaten im Hexadezimalformat anzeigen.

Weitere Informationen finden Sie unter [Format-Hex](/powershell/module/microsoft.powershell.utility/format-hex).

## <a name="get-childitem-has--depth-parameter"></a>„Get-ChildItem“ mit „-Depth“-Parameter

`Get-ChildItem` enthält nun einen Parameter **Depth**, den Sie mit **Recurse** verwenden können, um die Rekursion zu begrenzen:

## <a name="modules-support-for-declaring-version-ranges-1-etc"></a>Modulunterstützung für das Deklarieren von Versionsbereichen (1.* usw.)

Nun können Sie **MinimumVersion** und **MaximumVersion** kombinieren, um das Modul innerhalb eines bestimmten Bereichs zu importieren. Der Parameter unterstützt auch Platzhalterzeichen.

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

## <a name="new-guid"></a>New-Guid

Es gibt viele Szenarien, in denen eindeutige Bezeichner erforderlich sind. Das Cmdlet `New-GUID`bietet eine einfache Möglichkeit zum Erstellen einer neuen GUID.

```powershell
New-Guid
```

```Output
Guid
----
e19d6ea5-3cc2-4db9-8095-0cdaed5a703d
```

## <a name="nonewline-parameter"></a>„NoNewLine“-Parameter

`Out-File`, `Add-Content` und `Set-Content` verfügen nun über einen Schalter **NoNewline**, der eine neue Zeile hinter der Ausgabe weglässt. Beispiel:

```powershell
"This is " | Out-File -FilePath Example.txt -NoNewline
"a single " | Add-Content -Path Example.txt -NoNewline
"sentence." | Add-Content -Path Example.txt -NoNewline
Get-Content .\Example.txt

```Output
This is a single sentence.
```

Ohne Angabe von **NoNewline** befindet sich jedes Fragment in einer gesonderten Zeile:

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

## <a name="interact-with-symbolic-links-using-improved-item-cmdlets"></a>Interagieren mit symbolischen Verknüpfungen mithilfe verbesserter „Item“-Cmdlets

Zur Unterstützung symbolischer Verknüpfungen wurden das Item-Cmdlet und einige zugehörige Cmdlets erweitert.

### <a name="symbolic-link-files"></a>Symbolische Verknüpfungsdateien

In diesem Beispiel erstellen wir eine neue symbolische Verknüpfungsdatei mit dem Namen „MySymLinkFile.txt“ in „C:\Temp“, die mit „$pshome\profile.ps1“ verknüpft. Alle drei Beispiele erzeugen dasselbe Ergebnis.

```powershell
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
```

### <a name="symbolic-link-directories"></a>Symbolische Verknüpfungsverzeichnisse

In diesem Beispiel erstellen wir ein neues symbolisches Verknüpfungsverzeichnis mit dem Namen „MySymLinkDir“ in „C:\Temp“, das mit dem Ordner „$pshome“ verknüpft. Alle drei Beispiele erzeugen dasselbe Ergebnis.

```powershell
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkDir -Value $pshome
```

### <a name="hard-links"></a>Feste Links

Dieselben Kombinationen von **Pfad** und **Namen** sind zulässig, wie oben beschrieben.

```powershell
New-Item -ItemType HardLink -Path C:\Temp -Name MyHardLinkFile.txt -Value $pshome\profile.ps1
```

### <a name="directory-junctions"></a>Verzeichnisverbindungen

Dieselben Kombinationen von **Pfad** und **Namen** sind zulässig, wie oben beschrieben.

```powershell
New-Item -ItemType Junction -Path C:\Temp\MyJunctionDir -Value $pshome
```

### <a name="get-childitem"></a>Get-ChildItem

`Get-ChildItem` zeigt nun „l“ in der **Modus**-Eigenschaft an, um ein/e symbolische/s Verknüpfungsdatei oder -verzeichnis anzuzeigen.

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

### <a name="remove-item"></a>Remove-Item

Das Entfernen symbolischer Verknüpfungen funktioniert wie das Entfernen jedes anderen Elementtyps.

```powershell
Remove-Item C:\Temp\MySymLinkFile.txt
Remove-Item C:\Temp\MySymLinkDir
```

Verwenden Sie den Parameter **Force**, um die Dateien im Zielverzeichnis und die symbolische Verknüpfung zu entfernen.

```powershell
Remove-Item C:\Temp\MySymLinkDir -Force
```

## <a name="new-temporaryfile"></a>New-TemporaryFile

Mitunter müssen Sie in Ihren Skripts eine temporäre Datei erstellen. Hierzu können Sie jetzt den Befehl `New-TemporaryFile` verwenden.

```powershell
$tempFile = New-TemporaryFile
$tempFile.FullName
```

```Output
C:\Users\user1\AppData\Local\Temp\tmp375.tmp
```

## <a name="network-switch-management-with-powershell"></a>Verwalten von Netzwerkswitches mit PowerShell

Die „NetworkSwitch“-Cmdlets, die in WMF 5.0 eingeführt wurden, ermöglichen Ihnen Netzwerkswitches, die mit dem Windows Server 2012 R2-Logo zertifiziert sind, mit einer Switch-, VLAN- und grundlegenden Layer 2-Netzwerkswitch-Konfiguration zu versehen. Mithilfe dieser Cmdlets können Sie Folgendes ausführen:

- Globale Switchkonfiguration, wie z. B.:
  - Hostnamen festlegen
  - Switchbanner festlegen
  - Konfiguration dauerhaft speichern
  - Features aktivieren oder deaktivieren

- VLAN-Konfiguration:
  - VLAN erstellen oder entfernen
  - VLAN aktivieren oder deaktivieren
  - VLAN auflisten
  - Anzeigenamen für ein VLAN festlegen

- Layer 2-Portkonfiguration:
  - Ports auflisten
  - Ports aktivieren oder deaktivieren
  - Portmodi und -eigenschaften festlegen
  - VLAN im Modus „Access“ oder „Trunk“ für den Port hinzufügen oder zuordnen

Weitere Informationen finden Sie in der [NetworkSwitchManager](/powershell/module/networkswitchmanager/)-Dokumentation.

## <a name="generate-powershell-cmdlets-based-on-an-odata-endpoint-with-odatautils"></a>Generieren von PowerShell-Cmdlets basierend auf einem OData-Endpunkt mit ODataUtils

Das „ODataUtils“-Modul ermöglicht die Generierung von PowerShell-Cmdlets anhand von REST-Endpunkten, die OData unterstützen. Das „Microsoft.PowerShell.ODataUtils“-Modul umfasst die folgenden Features:

- Übertragen zusätzlicher Informationen vom serverseitigen Endpunkt zur Clientseite
- Unterstützung einer clientseitigen Auslagerung
- Serverseitige Filterung mithilfe des „-Select“-Parameters
- Unterstützung für Webanforderungsheader

Die vom `Export-ODataEndPointProxy`-Cmdlet generierten „Proxy“-Cmdlets bieten zusätzliche Informationen vom serverseitigen OData-Endpunkt zum **Information**sdatenstrom.

```powershell
Import-Module Microsoft.PowerShell.ODataUtils -Force
$generatedProxyModuleDir = Join-Path -Path $env:SystemDrive -ChildPath 'ODataDemoProxy'
$uri = "http://services.odata.org/V3/(S(fhleiief23wrm5a5nhf542q5))/OData/OData.svc/"
Export-ODataEndpointProxy -Uri $uri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -AllowClobber
```

Im folgenden Beispiel rufen wir das Top-Produkt ab und erfassen die Ausgabe in der Variablen `$infoStream`.

Durch Angabe des Parameters **IncludeTotalResponseCount** erhalten wir die Gesamtzahl aller **Produkt**-Datensätze, die auf dem Server verfügbar sind.

```powershell
Import-Module $generatedProxyModuleDir -Force
$product = Get-Product -Top 1 -AllowUnsecureConnection -AllowAdditionalData -IncludeTotalResponseCount -InformationVariable infoStream
$additionalInfo = $infoStream.GetEnumerator() | % MessageData
$additionalInfo['odata.count']
```

Sie können die Datensätze vom Server mithilfe der Unterstützung clientseitiger Auslagerung in Batches abrufen. Dies ist hilfreich, wenn Sie eine große Datenmenge vom Server über das Netzwerk abrufen müssen.

```powershell
$skipCount = 0
$batchSize = 3
while($skipCount -le $additionalInfo['odata.count'])
{
  Get-Product -AllowUnsecureConnection -AllowAdditionalData -Top $batchSize -Skip $skipCount
  $skipCount += $batchSize
}
```

Die generierten „Proxy“-Cmdlets unterstützen den **Select**-Parameter, der als Filter verwendet wird, um nur die Datensatzeigenschaften zu empfangen, die der Client benötigt. Die Filterung erfolgt auf dem Server, was die Menge der Daten reduziert, die über das Netzwerk übertragen werden.

```powershell
Get-Product -Top 2 -AllowUnsecureConnection -AllowAdditionalData -Select Name
```

Das `Export-ODataEndpointProxy`-Cmdlet und die von diesem generierten „Proxy“-Cmdlets unterstützen jetzt den Parameter **Headers**. Der Header kann verwendet werden, um zusätzliche Informationen, die vom OData-Endpunkt erwartet werden, zu übertragen.

Im folgenden Beispiel wird dem Parameter**Headers** eine Hashtabelle bereitgestellt, die einen Abonnementschlüssel enthält. Dies ist ein typisches Beispiel für Dienste, die einen Abonnementschlüssel für die Authentifizierung erwarten.

```powershell
Export-ODataEndpointProxy -Uri $endPointUri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -Headers @{'subscription-key'='XXXX'}
```
