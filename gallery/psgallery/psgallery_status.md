---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: PowerShell, Cmdlet, Katalog
ms.date: 2016-10-14
contributor: manikb
title: PowerShell-Katalogstatus | MSDN
ms.technology: powershell
ms.openlocfilehash: 40ebfa510abe647d80a85fa15f0b777d697ffdfb
ms.sourcegitcommit: 26c3acb3dae9f7c3868a5f0d6144e9e1a0d02557
translationtype: HT
---
<a name="powershell-gallery-status"></a>PowerShell-Katalogstatus
=========================


## <a name="12152016---unable-to-send-emails-via-powershellgallery-website"></a>15.12.2016 – Es konnten keine E-Mails über die PowerShell-Katalogwebsite gesendet werden.

__Zusammenfassung der Auswirkungen__: Zwischen dem 13. und 15. Dezember 2016 über „Contact owners“ (Besitzer kontaktieren), „Manage Owners“ (Besitzer verwalten), „Support kontaktieren“ oder „Missbrauch melden“ gesendete E-Mails wurden von den Administratoren des PowerShell-Katalogs nicht empfangen.  
__Grundursache__: Das Problem wurde von Technikern auf einen Authentifizierungsfehler beim SMTP-Server zurückgeführt.  
__Lösung__: Techniker konnten das Authentifizierungsproblem lösen und die Verbindung mit dem SMTP-Server wiederherstellen.  
__Nächste Schritte__: Wenn Sie die Links „Contact owners“ (Besitzer kontaktieren), „Manage Owners“ (Besitzer verwalten), „Support kontaktieren“ oder „Missbrauch melden“ während dieses Zeitraums an cgadmin@microsoft.com gesendet und keine Antwort erhalten haben, versuchen Sie es erneut. Wir entschuldigen uns für eventuelle Unannehmlichkeiten.  



## <a name="8102016---resolved-unable-to-send-emails-to-cgadminmicrosoftcom"></a>10.08.2016 – Gelöst: Senden von E-Mails an cgadmin@microsoft.com nicht möglich

__Zusammenfassung der Auswirkungen__: Vom 05.08.2016 bis zum 10.08.2016 konnten Kunden keine E-Mails an cgadmin@microsoft.com, senden bzw. die Funktion zur Kontaktaufnahme nicht nutzen.  
__Ursache__: Als Ursache haben Techniker eine Konfigurationsänderung des E-Mail-Kontos ausgemacht.  
__Lösung__: Techniker haben das Konfigurationsproblem behoben.  
__Nächste Schritte__: Wenn Sie in diesem Zeitraum den Link zur Kontaktaufnahme genutzt oder eine E-Mail an cgadmin@microsoft.com gesendet und wir nicht geantwortet haben, versuchen Sie es erneut. Vielen Dank für Ihre Geduld.



## <a name="7132016---download-items-failed"></a>13.07.2016 – Herunterladen von Elementen nicht möglich

__Zusammenfassung der Auswirkungen__: Vom 11.7.2016 bis 13.7.2016 hatten Kunden teilweise Probleme beim Herunterladen von Elementen aus dem PowerShell-Katalog. Das Problem manifestierte sich in der folgenden Fehlermeldung, die von „Install-Module/Install-Script“ und „Save-Module/Save-Script“ zurückgegeben wurde:

```PowerShell
PS C:\> Install-Module xStorage 
PackageManagement\Install-Package : Package 'xStorage' failed to be installed because: 
End of Central Directory record could not be found. At C:\Program 
Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1375 char:21 + ... 
$null = PackageManagement\Install-Package @PSBoundParameters + 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ + CategoryInfo : InvalidResult: 
(xStorage:String) [Install-Package], Exception + FullyQualifiedErrorId : Package '{0}' 
failed to be installed because: {1},Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage 
```

__Vorläufige Ursache__: Techniker haben ein Problem mit dem Azure Content Delivery Network (CDN) ausgemacht, das am 11.7.2016 im PowerShell-Katalog bereitgestellt wurde.  
__Lösung__: Techniker haben Azure CDN im PowerShell-Katalog deaktiviert.  
__Nächste Schritte__: Untersuchen der Ursache und Entwickeln einer Lösung, um zu verhindern, dass dies künftig erneut vorkommt.


## <a name="5192016---download-items-failed"></a>19.05.2016 – Herunterladen von Elementen nicht möglich
__Zusammenfassung der Auswirkungen__: Vom 17.5.2016 bis 19.5.2016 hatten Kunden teilweise Probleme beim Herunterladen von Elementen aus dem PowerShell-Katalog. Das Problem manifestierte sich in der folgenden Fehlermeldung, die von „Install-Module/Install-Script“ und „Save-Module/Save-Script“ zurückgegeben wurde:

```PowerShell
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

__Vorläufige Ursache__: Techniker haben ein Problem mit dem Azure Content Delivery Network (CDN) ausgemacht, das am 17.5.2016 im PowerShell-Katalog bereitgestellt wurde.  
__Lösung__: Techniker haben Azure CDN im PowerShell-Katalog deaktiviert.  
__Nächste Schritte__: Untersuchen der Ursache und Entwickeln einer Lösung, um zu verhindern, dass dies künftig erneut vorkommt.

