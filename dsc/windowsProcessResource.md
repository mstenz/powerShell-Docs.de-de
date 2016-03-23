# DSC-Ressource „WindowsProcess“

> Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0

Die Ressource **WindowsProcess** in Windows PowerShell DSC bietet einen Mechanismus zum Konfigurieren von Prozessen auf einem Zielknoten.

## Syntax

```
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ DependsOn = [string[]] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ StandardOutputPath = [string] ]
    [ WorkingDirectory = [string] ]
}
```

## Eigenschaften
|  Eigenschaft  |  Beschreibung   | 
|---|---| 
| Argumente| Gibt eine Zeichenfolge von Argumenten an, die wie vorhanden an den Prozess übergeben wird. Wenn Sie mehrere Argumente übergeben müssen, fügen Sie sie alle dieser Zeichenfolge hinzu.| 
| Path| Gibt den Pfad zur ausführbaren Prozessdatei an. Wenn Sie diese Eigenschaft auf den Namen der ausführbaren Datei festlegen, untersucht DSC die __Path__-Variable. Wenn Sie einen vollständig qualifizierten Domänennamen angeben, muss der Prozess vorhanden sein, da DSC in diesem Fall nicht die __Path__-Variable untersucht.| 
| Credential| Gibt die Anmeldeinformationen zum Starten des Prozesses an.| 
| Ensure| Gibt an, ob der Prozess vorhanden ist. Legen Sie diese Eigenschaft auf „Present“ fest, um sicherzustellen, dass der Prozess vorhanden ist. Legen Sie sie andernfalls auf „Absent“ fest. Die Standardeinstellung ist „Present“.| 
| DependsOn | Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird. Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, __ResourceName__ und dessen Typ __ResourceType__ ist, lautet die Syntax für das Verwenden dieser Eigenschaft „DependsOn = „[ResourceType]ResourceName“.| 
| StandardErrorPath| Gibt den Verzeichnispfad an, in den der Standardfehler geschrieben wird. Eine vorhandene Datei wird überschrieben.| 
| StandardInputPath| Gibt den Standardpfad für die Eingabe an.| 
| StandardOutputPath| Gibt den Speicherort an, in den die Standardausgabe geschrieben wird. Eine vorhandene Datei wird überschrieben.| 
| WorkingDirectory| Gibt den Speicherort an, der als das aktuelle Arbeitsverzeichnis für den Prozess verwendet wird.| 
<!--HONumber=Feb16_HO4-->
