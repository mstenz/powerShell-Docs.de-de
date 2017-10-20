---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: PowerShell-Katalogstatus | MSDN
ms.openlocfilehash: af6111d3c511273571bd978c6d0e7447726c2917
ms.sourcegitcommit: f069ff0689006fece768f178c10e3e3eeaee09f0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/13/2017
---
<a name="powershell-gallery-status"></a>PowerShell-Katalogstatus
=========================
## <a name="10102017---powershell-gallery-unavailable-for-2-hours-101017"></a>10.10.2017 – Der PowerShell-Katalog war am 10.10.17 für 2 Stunden nicht verfügbar.

__Zusammenfassung der Auswirkungen__: Beim PowerShell-Katalog kam es während eines Zeitraums zu sehr hohen Wartezeiten, wodurch am 10.10.17 ab ca. 17:00 Uhr (PDT) zeitweilige Verbindungsprobleme verursacht wurden. Zur Behebung des Problems wurde der Standort ab ca. 22 Uhr (PDT) für 2 Stunden offline geschaltet. Der Standort wurde am 10.10.2017 kurz vor Mitternacht wiederhergestellt. 
 
__Grundursache__: Die Grundursache für die hohe Wartezeit wird zurzeit noch untersucht.

__Lösung__: Die Webdienste mussten offline geschaltet und wiederhergestellt werden, um das primäre Problem zu beheben. 

__Nächste Schritte__: Die Grundursache für das ursprüngliche Problem wird zurzeit untersucht.

## <a name="06012017---deploy-to-azure-automation-currently-unavailable"></a>01.06.2017: Bereitstellung in Azure Automation aktuell nicht verfügbar

__Zusammenfassung der Auswirkungen__: Aktuell können vom PowerShell-Katalog aus keine Elemente mit Abhängigkeiten in Azure Automation bereitgestellt werden.  Von Azure Automation aus ist es weiterhin möglich, Elemente aus dem PowerShell-Katalog zu importieren.  
 
__Grundursache__: Elemente, die von anderen Elementen abhängen und zuvor in Azure Automation bereitgestellt wurden, können nicht in Azure Automation bereitgestellt werden. Techniker haben ein Problem damit festgestellt, wie ARM-Vorlagen für Elemente mit Abhängigkeiten zur Bereitstellung in Azure Automation generiert werden.

__Lösung__: Unsere Techniker arbeiten an einer Lösung für dieses Problem.  Die aktuelle Problemumgehung für Benutzer besteht darin, das Element mithilfe von Azure Automation aus dem PowerShell-Katalog zu importieren. 

__Nächste Schritte__: Unsere Techniker stellen in Kürze einen Fix bereit.  Verwenden Sie in der Zwischenzeit die empfohlene Problemumgehung. 


## <a name="04112017---users-unable-to-log-in-with-azure-active-directory-aad-accounts"></a>11.04.2017: Benutzer können sich nicht mit Azure Active Directory-Konten (AAD) anmelden

__Zusammenfassung der Auswirkungen__: Einige Benutzer konnten sich mit ihren Azure AD-Konten nicht beim PowerShell-Katalog anmelden. 
 
__Grundursache__: Bei einem Update für eine sicherere Interaktion mit AAD wurde eine Einstellung nicht geändert. Die Tests zur Überprüfung der Änderung umfassten bestimmte Arten von AAD-Konten nicht, daher wurde die Bereitstellung fortgesetzt.

__Lösung__: Techniker haben die fehlende Einstellung ermittelt und das Problem behoben. 

__Nächste Schritte__: Wir ändern unsere Tests, sodass eine größere Gruppe von AAD-Kontotypen einbezogen wird.

## <a name="03272017---resolved-unable-to-see-individual-module-and-script-pages"></a>27.03.2017 – GELÖST: Einzelne Modul- und Skriptseiten können nicht angezeigt werden

__Zusammenfassung der Auswirkungen__: Die direkten Links zu einzelnen Modul- und Skriptseiten auf https://www.powershellgallery.com haben nicht funktioniert. Dies wurde aus allen Regionen gemeldet. Dies hat sich nicht auf alle PowerShellGet-Cmdlets ausgewirkt, d.h. Install-Module, Install-Script, Update-Module, Update-Script, Publish-Module, Publish-Script haben weiterhin funktioniert.

__Grundursache__: Laut unseren Technikern ist die Ursache ein Problem bei der Einbindung von Schaltflächen für soziale Netzwerke, z.B. Facebook, auf der Seite.  

__Lösung__: Die Techniker haben das Problem gelöst, indem sie die Facebook-Kontoinformationen deaktiviert haben.

__Nächste Schritte__: Wir haben ein internes Nachverfolgungsproblem geöffnet, um unseren Gebrauch der Facebook-API zu reparieren.

## <a name="12152016---unable-to-send-emails-via-powershellgallery-website"></a>15.12.2016 – Es konnten keine E-Mails über die PowerShell-Katalogwebsite gesendet werden.

__Zusammenfassung der Auswirkungen__: Zwischen dem 13. und 15. Dezember 2016 über „Contact owners“ (Besitzer kontaktieren), „Manage Owners“ (Besitzer verwalten), „Support kontaktieren“ oder „Missbrauch melden“ gesendete E-Mails wurden von den Administratoren des PowerShell-Katalogs nicht empfangen.  
__Grundursache__: Das Problem wurde von Technikern auf einen Authentifizierungsfehler beim SMTP-Server zurückgeführt.  
__Lösung__: Techniker konnten das Authentifizierungsproblem lösen und die Verbindung mit dem SMTP-Server wiederherstellen.  
__Nächste Schritte__: Wenn Sie die Links „Contact owners“ (Besitzer kontaktieren), „Manage Owners“ (Besitzer verwalten), „Support kontaktieren“ oder „Missbrauch melden“ während dieses Zeitraums an cgadmin@microsoft.com gesendet und keine Antwort erhalten haben, versuchen Sie es erneut. Wir entschuldigen uns für eventuelle Unannehmlichkeiten.  



## <a name="8102016---resolved-unable-to-send-emails-to-cgadminmicrosoftcom"></a>10.08.2016 – Gelöst: Senden von E-Mails an cgadmin@microsoft.com nicht möglich

__Zusammenfassung der Auswirkungen__: Vom 05.08.2016 bis zum 10.08.2016 konnten Kunden keine E-Mails an cgadmin@microsoft.com senden bzw. die Funktion zur Kontaktaufnahme nicht nutzen.  
__Grundursache__: Als Ursache haben Techniker eine Konfigurationsänderung des E-Mail-Kontos ausgemacht.  
__Lösung__: Techniker haben das Konfigurationsproblem behoben.  
__Nächste Schritte__: Wenn Sie in diesem Zeitraum den Link zur Kontaktaufnahme genutzt oder eine E-Mail an cgadmin@microsoft.com gesendet und wir nicht geantwortet haben, versuchen Sie es erneut. Vielen Dank für Ihre Geduld.



## <a name="7132016---download-items-failed"></a>13.07.2016 – Herunterladen von Elementen nicht möglich

__Zusammenfassung der Auswirkungen__: Vom 11.7.2016 bis 13.7.2016 hatten Kunden teilweise Probleme beim Herunterladen von Elementen aus dem PowerShell-Katalog. Das Problem manifestierte sich in der folgenden Fehlermeldung, die von „Install-Module/Install-Script“ und „Save-Module/Save-Script“ zurückgegeben wurde:

```powershell
PS C:\> Install-Module xStorage 
PackageManagement\Install-Package : Package 'xStorage' failed to be installed because: 
End of Central Directory record could not be found. At C:\Program 
Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1375 char:21 + ... 
$null = PackageManagement\Install-Package @PSBoundParameters + 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ + CategoryInfo : InvalidResult: 
(xStorage:String) [Install-Package], Exception + FullyQualifiedErrorId : Package '{0}' 
failed to be installed because: {1},Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage 
```

__Vorläufige Grundursache__: Techniker haben ein Problem mit dem Azure Content Delivery Network (CDN) ausgemacht, das am 11.7.2016 im PowerShell-Katalog bereitgestellt wurde.  
__Lösung__: Techniker haben Azure CDN im PowerShell-Katalog deaktiviert.  
__Nächste Schritte__: Untersuchen der Grundursache und Entwickeln einer Lösung, um zu verhindern, dass dies künftig erneut vorkommt.


## <a name="5192016---download-items-failed"></a>19.05.2016 – Herunterladen von Elementen nicht möglich
__Zusammenfassung der Auswirkungen__: Vom 17.5.2016 bis 19.5.2016 hatten Kunden teilweise Probleme beim Herunterladen von Elementen aus dem PowerShell-Katalog. Das Problem manifestierte sich in der folgenden Fehlermeldung, die von „Install-Module/Install-Script“ und „Save-Module/Save-Script“ zurückgegeben wurde:

```powershell
VERBOSE: Hash for package 'AzureRM.OperationalInsights' does not match hash provided from the server.
VERBOSE: InstallPackageLocal' - name='AzureRM.OperationalInsights', version='1.0.8',
destination='C:\Users\jbritt\AppData\Local\Temp\2\1741355729'
WARNING: Package 'AzureRM.OperationalInsights' failed to be installed because: 
End of Central Directory record could not be found. 
WARNING: Dependent Package 'AzureRM.OperationalInsights' failed to install. 
WARNING: Package 'AzureRM' failed to install. 
VERBOSE: Module 'AzureRM.Network' was saved successfully. 
VERBOSE: Saving the dependency module 'AzureRM.NotificationHubs' with version '1.0.8' for the 
module 'AzureRM'. 
VERBOSE: Module 'AzureRM.NotificationHubs' was saved successfully. 
PackageManagement\Save-Package : Unable to save the module 'AzureRM'. At C:\Program 
Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1187 char:21 + 
$null = PackageManagement\Save-Package @PSBoundParameters + 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ + 
CategoryInfo : InvalidOperation: (Microsoft.Power...ets.SavePackage:SavePackage) 
[Save-Package], Exception + FullyQualifiedErrorId : ProviderFailToDownloadFile,
Microsoft.PowerShell.PackageManagement.Cmdlets.SavePackage 
```

__Vorläufige Grundursache__: Techniker haben ein Problem mit dem Azure Content Delivery Network (CDN) ausgemacht, das am 17.5.2016 im PowerShell-Katalog bereitgestellt wurde.  
__Lösung__: Techniker haben Azure CDN im PowerShell-Katalog deaktiviert.  
__Nächste Schritte__: Untersuchen der Grundursache und Entwickeln einer Lösung, um zu verhindern, dass dies künftig erneut vorkommt.

