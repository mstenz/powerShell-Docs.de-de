# DSC-Ressource „Group“

> Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0

Die Ressource „Group“ in Windows PowerShell DSC bietet einen Mechanismus zum Verwalten lokaler Gruppen auf dem Zielknoten.

##Syntax##
```
Group [string] #ResourceName
{
    GroupName = [string]
    [ Credential = [PSCredential] ]
    [ Description = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ Members = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ MembersToInclude = [string[]] ]
    [ DependsOn = [string[]] ]
}
```

## Eigenschaften

|  Eigenschaft  |  Beschreibung   | 
|---|---| 
| GroupName| Gibt den Namen der Gruppe an, für die Sie einen bestimmten Zustand sicherstellen möchten.| 
| Credential| Gibt die Anmeldeinformationen für den Zugriff auf Remoteressourcen an. **Hinweis**: Dieses Konto muss die entsprechenden Active Directory-Berechtigungen aufweisen, um alle nicht lokalen Konten zur Gruppe hinzuzufügen. Andernfalls tritt ein Fehler auf.
| Description| Gibt die Beschreibung der Gruppe an.| 
| Ensure| Gibt an, ob die Gruppe vorhanden ist. Legen Sie diese Eigenschaft auf „Absent“ fest, um sicherzustellen, dass die Gruppe nicht vorhanden ist. Das Festlegen auf „Present“ (den Standardwert) stellt sicher, dass die Gruppe vorhanden ist.| 
| Members| Gibt an, dass Sie sicherstellen möchten, dass diese Mitglieder die Gruppe bilden.| 
| MembersToExclude| Gibt die Benutzer an, die auf keinen Fall Mitglied dieser Gruppe werden sollen.| 
| MembersToInclude| Gibt die Benutzer an, die Mitglied dieser Gruppe werden sollen.| 
| DependsOn | Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird. Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, __ResourceName__ und dessen Typ __ResourceType__ ist, lautet die Syntax für das Verwenden dieser Eigenschaft „DependsOn = „[ResourceType]ResourceName“.| 

## Beispiel

Im folgenden Beispiel wird veranschaulicht, wie sichergestellt wird, dass eine Gruppe namens „TestGroup“ nicht vorhanden ist. 

```powershell
Group GroupExample
{
    # This will remove TestGroup, if present
    # To create a new group, set Ensure to "Present“
    Ensure = "Absent"
    GroupName = "TestGroup"
}
```
<!--HONumber=Feb16_HO4-->
