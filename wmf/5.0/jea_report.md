---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: cd3338ae305896e282056a871974e5f899ef6ff5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085252"
---
# <a name="reporting-on-jea"></a><span data-ttu-id="c75fc-102">Berichterstellung zu JEA</span><span class="sxs-lookup"><span data-stu-id="c75fc-102">Reporting on JEA</span></span>

<span data-ttu-id="c75fc-103">Um einen Bericht zum Zustand Ihrer JEA-Konfiguration zu erhalten, können Sie die folgenden Cmdlets verwenden:</span><span class="sxs-lookup"><span data-stu-id="c75fc-103">In order to report on the state of your JEA configuration, you can use:</span></span>

1. <span data-ttu-id="c75fc-104">**Get-PSSessionConfiguration**, um eine Liste aller registrierten Endpunkte auf einem bestimmten Computer zurückzugeben.</span><span class="sxs-lookup"><span data-stu-id="c75fc-104">**Get-PSSessionConfiguration** to return a list of all registered endpoints on a given machine.</span></span>
2. <span data-ttu-id="c75fc-105">**Get-PSSessionCapability**, um die Optionen zu melden, die ein Benutzer auf einem bestimmten Endpunkt hat.</span><span class="sxs-lookup"><span data-stu-id="c75fc-105">**Get-PSSessionCapability** to report on the capabilities any given user has on a specific endpoint.</span></span>

<span data-ttu-id="c75fc-106">Hier ein Beispiel für **Get-PSSessionCapability**:</span><span class="sxs-lookup"><span data-stu-id="c75fc-106">Here's an example of **Get-PSSessionCapability**:</span></span>

```powershell
Get-PSSessionCapability -ConfigurationName Maintenance -Username "CONTOSO\JohnDoe"

CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           clear -> Clear-Host
Alias           cls -> Clear-Host
Alias           exsn -> Exit-PSSession
Alias           gcm -> Get-Command
Alias           measure -> Measure-Object
Alias           select -> Select-Object
Function        Clear-Host
Function        Exit-PSSession
Function        Get-Command
Function        Get-FormatData
Function        Get-Help
Function        Get-UserInfo
Function        Measure-Object
Function        Out-Default
Function        Select-Object
Cmdlet          Restart-Service                                    3.0.0.0 Microsof...
```

<span data-ttu-id="c75fc-107">Zum Erstellen eines Berichts zu den _Aktionen_, die ein Benutzer in einer JEA-Sitzung ausgeführt hat, haben Sie diese Möglichkeiten:</span><span class="sxs-lookup"><span data-stu-id="c75fc-107">To report on the _actions_ users took during a JEA session, you can:</span></span>

1. <span data-ttu-id="c75fc-108">Aktivieren Sie die „Über die Schulter“-Aufzeichnungen für den gewünschten Endpunkt, und fragen Sie das Verzeichnis mit den Aufzeichnungen auf ein vollständiges Protokoll aller Aktionen des Benutzers ab.</span><span class="sxs-lookup"><span data-stu-id="c75fc-108">Enable the "over-the-shoulder" transcripts for that JEA endpoint and consult the transcript directory for a full log of each user's actions</span></span>
2. <span data-ttu-id="c75fc-109">Aktivieren Sie die PowerShell-Modulprotokollierung, und überprüfen Sie die PowerShell-Ereignisprotokolle.</span><span class="sxs-lookup"><span data-stu-id="c75fc-109">Turn on PowerShell module logging and inspect the PowerShell event logs.</span></span>