# Bekannte Probleme und Einschränkungen

PowerShell-Verknüpfungen sind beim ersten Verwenden unterbrochen
------------------------------------------------------------

**Lösung:** Führen Sie eine der folgenden Aktionen aus:

1.  Klicken Sie mit der rechten Maustaste auf die PowerShell-Verknüpfung. Wählen Sie „Windows PowerShell“ aus, um in einem Modus ohne erhöhte Rechte zu starten.
2.  Klicken Sie mit der rechten Maustaste auf die PowerShell-Verknüpfung. Klicken Sie mit der rechten Maustaste auf „Windows PowerShell“, und wählen Sie „Als Administrator ausführen“ aus, um im Modus mit erhöhten Rechten zu starten.

Nachdem Sie eine der oben aufgeführten Aktionen ausgeführt haben, funktionieren die PowerShell-Verknüpfungen. Diese Aktionen müssen nur einmal ausgeführt werden.


PowerShell-Module und DSC-Ressourcen melden Fehler zu „ExecutionPolicy“ unter Windows 7
-------------------------------------------------------------------------------------
Unter Windows 7 kann die Verwendung von PowerShell-Modulen und DSC-Ressourcen zu Fehlern führen, die zu „ExecutionPolicy“ gemeldet werden.

**Lösung:** Legen Sie „ExecutionPolicy“ auf „RemoteSigned“ fest, indem Sie den folgenden Befehl mit erhöhten Rechten in einer PowerShell-Sitzung ausführen (Als Administrator ausführen):

```powershell
Set-ExecutionPolicy RemoteSigned
```

Herstellen einer Verbindung mit einem alten Exchange- Remoteendpunkt führt zum Absturz
------------------------------------------------------------

Der alte Exchange-Endpunkt wird zu einem neuen Endpunkt umgeleitet. Die Umleitungslogik weist einen Fehler auf, der zu einem Absturz führt.

**Lösung:** Stellen Sie eine direkte Verbindung mit dem neuen Endpunkt her.


Das Feature „Protokollierung des Softwarebestands“ wird nach der Installation von WMF 5.0 unter Windows Server 2012 R2 fälschlicherweise beendet
-------------------------------------------------------------------------------------------------------------

Wenn WMF 5.0 auf einem Computer mit Windows Server 2012 R2 installiert wird, auf dem die Protokollierung des Softwarebestands bereits ausgeführt wird, wird dieses Feature nach der Installation fälschlicherweise beendet.

**Lösung:** Führen Sie das Cmdlet „Start-SilLogging“ nach der Installation von WMF aus, da der Installationsvorgang fälschlicherweise das Feature „Protokollierung des Softwarebestands“ beendet.

„Get-ChildItem“ funktioniert nicht, wenn „-LiteralPath“ und „-Recurse“ zusammen verwendet werden
--------------------------------------------------------------------------

Wenn ein Verzeichnisname ein ungültiges Platzhalterzeichen enthält, liefert „Get-ChildItem“ nicht die erwarteten Ergebnisse, wenn
„-LiteralPath“ und „-Recurse“ zusammen verwendet werden.

**Lösung:** Die aktuelle, allerdings nicht ideale Umgehung ist das Implementieren der Rekursion im Skript, anstatt das Cmdlet zu verwenden.
<!--HONumber=Mar16_HO2-->
