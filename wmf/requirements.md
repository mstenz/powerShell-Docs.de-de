# Systemanforderungen

- Vor der Installation von WMF 5.0 RTM müssen Sie die neuesten Windows-Updates installieren.
- Sie können WMF 5.0 RTM nur unter folgenden Betriebssystemen installieren:

    | Betriebssystem | Editionen | Voraussetzungen | Links zu Paketen |
    |------------------------|--------------|------------------|----------------------| --------------|
    | Windows Server 2012 R2 |  |  | <ctype="x-NOTFOUND" mdpre="[" mdpost="](http://go.microsoft.com/fwlink/?LinkId=717507)">Win8.1AndW2K12R2-KB3134758-x64.msu</ctype="x-NOTFOUND"> |
    | Windows Server 2012    |  |  | <ctype="x-NOTFOUND" mdpre="[" mdpost="](http://go.microsoft.com/fwlink/?LinkId=717506)">W2K12-KB3134759-x64.msu</ctype="x-NOTFOUND"> |
    | Windows Server 2008 R2 SP1 | Alle außer IA64 | <ctype="x-NOTFOUND" mdpre="[" mdpost="](http://www.microsoft.com/en-us/download/details.aspx?id=40855)">WMF 4.0</ctype="x-NOTFOUND"> und <ctype="x-NOTFOUND" mdpre="[" mdpost="](https://msdn.microsoft.com/en-us/library/5a4x27ek.aspx)">.NET Framework 4.5 oder höher</ctype="x-NOTFOUND"> sind installiert | <ctype="x-NOTFOUND" mdpre="[" mdpost="](http://go.microsoft.com/fwlink/?LinkId=717504)">Win7AndW2K8R2-KB3134760-x64.msu</ctype="x-NOTFOUND">|
    | Windows 8.1 | Pro, Enterprise | | <ctype="x-NOTFOUND" mdpre="**" mdpost="**">x64:</ctype="x-NOTFOUND"> <ctype="x-NOTFOUND" mdpre="[" mdpost="](http://go.microsoft.com/fwlink/?LinkId=717507)">Win8.1AndW2K12R2-KB3134758-x64.msu</ctype="x-NOTFOUND"> </br> <ctype="x-NOTFOUND" mdpre="**" mdpost="**">x86:</ctype="x-NOTFOUND"> <ctype="x-NOTFOUND" mdpre="[" mdpost="](http://go.microsoft.com/fwlink/?LinkID=717963)">Win8.1-KB3134758-x86.msu</ctype="x-NOTFOUND">|
    | Windows 7 SP1 | Alle | <ctype="x-NOTFOUND" mdpre="[" mdpost="](http://www.microsoft.com/en-us/download/details.aspx?id=40855)">WMF 4.0</ctype="x-NOTFOUND"> und <ctype="x-NOTFOUND" mdpre="[" mdpost="](https://msdn.microsoft.com/en-us/library/5a4x27ek.aspx)">.NET Framework 4.5 oder höher</ctype="x-NOTFOUND"> sind installiert | <ctype="x-NOTFOUND" mdpre="**" mdpost="**">x64:</ctype="x-NOTFOUND"> <ctype="x-NOTFOUND" mdpre="[" mdpost="](http://go.microsoft.com/fwlink/?LinkId=717504)">Win7AndW2K8R2-KB3134760-x64.msu</ctype="x-NOTFOUND">  </br> <ctype="x-NOTFOUND" mdpre="**" mdpost="**">x86:</ctype="x-NOTFOUND"> <ctype="x-NOTFOUND" mdpre="[" mdpost="](http://go.microsoft.com/fwlink/?LinkID=717962)">Win7-KB3134760-x86.msu</ctype="x-NOTFOUND">|

# Installationsanweisungen

### So installieren Sie WMF 5.0 über Windows-Explorer (oder Datei-Explorer)

1. Wechseln Sie zum Ordner, in den Sie die MSU-Datei heruntergeladen haben.

2. Doppelklicken Sie auf die MSU-Datei, um sie auszuführen.

### So installieren Sie WMF 5.0 über die Befehlszeile

1. Öffnen Sie nach dem Herunterladen des richtigen Pakets für die Architektur Ihres Computers ein Eingabeaufforderungsfenster mit erhöhten Benutzerrechten (Als Administrator ausführen). Bei den Server Core-Installationsoptionen von Windows Server 2012 R2, Windows Server 2012 oder Windows Server 2008 R2 SP1 wird das Eingabeaufforderungsfenster standardmäßig mit erhöhten Benutzerrechten geöffnet.

2. Wechseln Sie zum Ordner, in den Sie das Installationspaket für WMF 5.0 heruntergeladen oder kopiert haben.

3. Führen Sie einen der folgenden Befehle aus:
    - Führen Sie auf Computern mit Windows Server 2012 R2 oder Windows 8.1 x64 <ctype="x-NOTFOUND" mdpre="**" mdpost="**">Win8.1AndW2K12R2-KB3134758-x64.msu /quiet</ctype="x-NOTFOUND"> aus.
    - Führen Sie auf Computern mit Windows Server 2012 <ctype="x-NOTFOUND" mdpre="**" mdpost="**">W2K12-KB3134759-x64.msu /quiet</ctype="x-NOTFOUND"> aus.
    - Führen Sie auf Computern mit Windows Server 2008 R2 SP1 oder Windows 7 SP1 x64 <ctype="x-NOTFOUND" mdpre="**" mdpost="**">Win7AndW2K8R2-KB3134760-x64.msu /quiet</ctype="x-NOTFOUND"> aus.
    - Führen Sie auf Computern mit Windows 8.1 x86 <ctype="x-NOTFOUND" mdpre="**" mdpost="**">Win8.1-KB3134758-x86.msu /quiet</ctype="x-NOTFOUND"> aus.
    - Führen Sie auf Computern mit Windows 7 SP1 x86 <ctype="x-NOTFOUND" mdpre="**" mdpost="**">Win7-KB3134760-x86.msu /quiet</ctype="x-NOTFOUND"> aus.

### Zusätzliche Installationshinweise für Windows Server 2008 R2 SP1 und Windows 7 SP1:

Überprüfen Sie, ob die folgenden Voraussetzungen erfüllt sind:
- Das neueste Service Pack ist installiert.
- <ctype="x-NOTFOUND" mdpre="[" mdpost="](http://www.microsoft.com/en-us/download/details.aspx?id=40855)">WMF 4.0</ctype="x-NOTFOUND"> ist installiert.
- <ctype="x-NOTFOUND" mdpre="[" mdpost="](https://msdn.microsoft.com/en-us/library/5a4x27ek.aspx)">.NET Framework 4.5 oder höher</ctype="x-NOTFOUND"> ist installiert.

**WMF 4.0-Abhängigkeit**

Auf Systemen mit Windows Server 2008 R2 SP1 bzw. Windows 7 SP1 sind PowerShell 2.0, WinRM und WMI integriert. WMF 3.0- und 4.0 von WMF-Pakete, mit denen diese integrierten Komponenten aktualisiert werden, wurden nach der Veröffentlichung von Windows Server 2008 R2 SP1 und Windows 7 SP1 veröffentlicht. Beim Installieren/Deinstallieren von WMF 3.0- und WMF 4.0-Paketen wurden einige Probleme unter dem folgenden Upgradepfad entdeckt:

- Integriert --> WMF 4.0
- Integriert --> WMF 3.0 --> WMF4.0. 

All diese Probleme wurden in den WMF 4.0-Paketen behoben. Daher ist WMF 4.0 Voraussetzung für die Installation von WMF 5.0 auf Windows Server 2008 R2 SP1 und Windows 7 SP1. Im Folgenden sind die spezifischen Probleme aufgelistet, die auftreten können, wenn Sie WMF 4.0 nicht vor dem Upgrade auf WMF 5.0 installieren:

- Das Protokoll der weitergeleiteten Ereignisse ist nicht verfügbar, und das EventCollector-Protokoll wird in der Ereignisanzeige nach der Deinstallation von WMF 3.0 oder WMF 5.0 (ohne die erforderliche Installation von WMF 4.0) in Windows 7 SP1 und Windows Server 2008 R2 SP1 nicht angezeigt (<ctype="x-NOTFOUND" mdpre="[" mdpost="](https://support.microsoft.com/en-us/kb/2809215)">KB2809215</ctype="x-NOTFOUND">).
- Die Anpassung der Umgebungsvariable <ctype="x-NOTFOUND" mdpre="*" mdpost="*">PSModulePath</ctype="x-NOTFOUND"> wird auf den Standardwert zurückgesetzt, wenn Sie in Windows 7 SP1 und in Windows Server 2008 R2 SP1 vom integrierten PowerShell 2.0 direkt auf WMF 5.0 (<ctype="x-NOTFOUND" mdpre="[" mdpost="](https://support.microsoft.com/en-us/kb/2872035)">KB2872035</ctype="x-NOTFOUND">) oder von WMF 3.0 zu WMF 5.0 (<ctype="x-NOTFOUND" mdpre="*" mdpost="*">KB2872047</ctype="x-NOTFOUND">) aktualisieren. (<bpt id="p1">[</bpt>KB2872047<ept id="p1">](https://support.microsoft.com/en-us/kb/2872047)</ept>) in Windows 7 SP1 and in Windows Server 2008 R2 SP1.

**WinRM-Abhängigkeit**

Windows PowerShell DSC (Desired State Configuration) hängt von WinRM ab. Unter Windows Server 2008 R2 SP1 und Windows 7 SP1 ist WinRM nicht standardmäßig aktiviert. Führen Sie zum Aktivieren von WinRM in einer Windows PowerShell-Sitzung mit erhöhten Benutzerrechten <ctype="x-NOTFOUND" mdpre="**" mdpost="**">Set-WSManQuickConfig</ctype="x-NOTFOUND"> aus.

# Deinstallationsanweisungen

### Verwenden der Eingabeaufforderung

1.  Öffnen Sie die <ctype="x-NOTFOUND" mdpre="**" mdpost="**">Eingabeaufforderung</ctype="x-NOTFOUND">.

2.  Führen Sie das <ctype="x-NOTFOUND" mdpre="[" mdpost="](https://support.microsoft.com/en-us/kb/934307)">eigenständige Windows Update-Startprogramm</ctype="x-NOTFOUND"> wie unten dargestellt aus:

Unter Windows Server 2012 R2 und Windows 8.1:
```powershell
wusa /uninstall /kb:3134758
```
Unter Windows Server 2012:
```powershell
wusa /uninstall /kb:3134759
```
Unter Windows Server 2008 R2 SP1 und Windows 7 SP1:
```powershell
wusa /uninstall /kb:3134760
```

### Über die Systemsteuerung

1.  Öffnen Sie die <ctype="x-NOTFOUND" mdpre="**" mdpost="**">Systemsteuerung</ctype="x-NOTFOUND">.

2.  Öffnen Sie <ctype="x-NOTFOUND" mdpre="**" mdpost="**">Programme</ctype="x-NOTFOUND"> und dann <ctype="x-NOTFOUND" mdpre="**" mdpost="**">Programm deinstallieren</ctype="x-NOTFOUND">.

3.  Klicken Sie auf <ctype="x-NOTFOUND" mdpre="**" mdpost="**">Installierte Updates anzeigen</ctype="x-NOTFOUND">.

4.  Wählen Sie in der Liste der installierten Updates <ctype="x-NOTFOUND" mdpre="**" mdpost="**">Windows Management Framework 5.0</ctype="x-NOTFOUND"> aus. Dies entspricht <ctype="x-NOTFOUND" mdpre="*" mdpost="*">KB3134758</ctype="x-NOTFOUND">, <ctype="x-NOTFOUND" mdpre="*" mdpost="*">KB3134759</ctype="x-NOTFOUND"> oder <ctype="x-NOTFOUND" mdpre="*" mdpost="*">KB3134760</ctype="x-NOTFOUND">. Klicken Sie auf <ctype="x-NOTFOUND" mdpre="**" mdpost="**">Deinstallieren</ctype="x-NOTFOUND">.


<!--HONumber=Mar16_HO4-->


