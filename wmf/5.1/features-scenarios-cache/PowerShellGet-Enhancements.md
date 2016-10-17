---
title: "Beispielvorlage für das Hochschreiben eines Features"
contributor: KeithB
translationtype: Human Translation
ms.sourcegitcommit: 8c55ca4b972c8d708a09b922f27eec585ddc33d0
ms.openlocfilehash: 025565404b60cebefac27e51c70d70edb5e47bc9

---

>Hinweis: Vorschlag für einen aussagekräftigen Namen und eine Kurzbeschreibung bereitstellen

## Verbesserungen von PowerShellGet ##
Die Cmdlets im PowerShellGet-Modul wurden in WMF 5.1 erheblich aktualisiert. Die folgenden neuen Szenarios werden nun unterstützt:

- **Proxy-Unterstützung:** Die Verwendung der PowerShellGet-Cmdlets in Kombination mit einem internen Proxy wird jetzt unterstützt, und die Parameter „Proxy“ und „ProxyCredential“ wurden zu allen Find-, Install-, Save- und Publish-Cmdlets des PowerShellGet-Moduls hinzugefügt (z.B.: Find-Module, Install-Module, Save-Module, Publish-Module). 
- **Erzwungene Signierung durch den Katalog:** Alle PowerShellGet-Cmdlets prüfen nun die Verfügbarkeit von Updates für signierte Module und erzwingen diese. Module, die mit den neuen Katalog-Cmdlets signiert wurden, werden von den PowerShellGet-Cmdlets geprüft, um sicherzustellen, dass das Modul während der Übertragung nicht geändert wurde und dass Updates für das Modul ausschließlich vom ursprünglichen Verleger stammen. Dies betrifft die Cmdlets „Install-Module“ und „Update-Module“. 
- **Freigeben und Erwerben von Rollenfunktionen:** Rollenfunktionen sind die Endpunktdefinitionen, die zum Konfigurieren Berechtigungen in Just Enough Administration verwendet werden, und werden über den PowerShell-Katalog in PowerShell-Modulen freigegeben. Betroffene Cmdlets sind Find-RoleCapability und New-PSRoleCapabilityFile. 
- **Suchen von Befehlen:** Find-Command ermöglicht es Benutzern, ein Modul im PowerShell-Katalog zu suchen, das einen gesuchten Befehl enthält. 
- **Authentifizierte Repositorys:** Der Feed der Paketverwaltung in Visual Studio erfordert eine Authentifizierung, und dies wird nun über die PowerShellGet-Cmdlets unterstützt.

Dank des Feedbacks von Benutzern haben wir weitere Problembereiche identifiziert, die in 5.1 behoben wurden, wie z.B.:

- **Anpassungen bei Install-Script:** Der von Install-Script verwendete Speicherort wird in 5.1 nicht automatisch zu dem Benutzerpfad hinzugefügt. Diese Änderung wurde in der eigenständigen Version von PowerShellGet vorgenommen und wurde nun in WMF 5.1 aufgenommen.
- **Hinzufügen von Metadatenfeldern zu vorhandenen Skripts:** Update-ScriptFileInfo kann mit vorhandenen Skripts verwendet werden, um die für die Veröffentlichung im PowerShell-Katalog notwendigen Standard-Metadatenfelder hinzuzufügen. Zuvor mussten Benutzer die Felder manuell mit einem vorhandenen Skript einfügen.
- **Veröffentlichen eines Moduls mit einer niedrigeren Version im Katalog:** Es ist jetzt möglich, im Katalog ein Modul mit einer niedrigeren Versionsnummer als der aktuell höchsten Version mithilfe von Publish-Module zu veröffentlichen. Wenn ein Verleger Version 2.0.0 seines Moduls mit wichtigen Änderungen hinsichtlich der Versionen 1.x veröffentlicht hätte, könnte er nur schwer eine Fehlerbehebung für Version 1.5.0 veröffentlichen. Jetzt können Sie eine 1.5.1-Version veröffentlichen, die die Unterstützung für die Verwaltung von Modulen im PowerShell-Katalog verbessert. 
- **Überprüfen, ob bei der Installation von Skripts und Modulen Befehle überschrieben wurden:** Install-Module und Install-Script überprüfen nun, ob sie Befehle enthalten, die bereits auf dem System vorhanden sind, und geben standardmäßig einen Fehler zurück, wenn dem so ist. 
- **Bootstrapping von NuGet in Publish-Cmdlets:** Zuvor gab es keine Möglichkeit, den NuGet-Anbieter mithilfe von Publish-Module oder Publish-Script automatisch zu installieren, was bestimmte Automatisierungsaufgaben schwer machte. Jetzt können Benutzer -Force zu Publish-Befehlen hinzufügen, um diese Meldung zu umgehen. 

>Hinweis: Zusätzliche Details über neue Konzepte, Implementierung, Beispiele usw. sollten mit der kanonischen technischen Dokumentation verknüpft werden

**Erfahren Sie mehr zur Verwendung von PowerShellGet**
- [About-CatalogSigning]()
- []()
- [Der Filter „Get-Module“ hat „CompatiblePSEditions“ als Ergebnis]()
- [Verhindern der Ausführung von Skripts außer bei Ausführung in einer kompatiblen Edition von PowerShell]()






<!--HONumber=Aug16_HO3-->


