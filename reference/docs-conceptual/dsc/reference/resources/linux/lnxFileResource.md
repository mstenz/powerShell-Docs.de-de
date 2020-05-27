---
ms.date: 09/20/2019
keywords: DSC,PowerShell,Konfiguration,Setup,Einrichtung
title: DSC für Linux-Resource „nxFile“
ms.openlocfilehash: 71096b2d269340b3568c95071089e114ef5c5db9
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560864"
---
# <a name="dsc-for-linux-nxfile-resource"></a>DSC für Linux-Resource „nxFile“

Die Ressource **nxFile** in PowerShell DSC (Desired State Configuration) bietet einen Mechanismus zum Verwalten von Dateien und Verzeichnissen auf einem Linux-Knoten.

## <a name="syntax"></a>Syntax

```Syntax
nxFile <string> #ResourceName
{
    DestinationPath = <string>
    [ SourcePath = <string> ]
    [ Type = <string> { directory | file | link } ]
    [ Contents = <string> ]
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Recurse = <bool> ]
    [ Force = <bool> ]
    [ Links = <string> { follow | manage | ignore } ]
    [ Group = <string> ]
    [ Mode = <string> ]
    [ Owner = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a>Eigenschaften

|Eigenschaft |BESCHREIBUNG |
|---|---|
|DestinationPath |Gibt den Speicherort an, an dem Sie den Zustand einer Datei oder eines Verzeichnisses sicherstellen möchten. |
|SourcePath |Gibt den Pfad an, aus dem die Datei- oder Ordnerressource kopiert werden soll. Dieser Pfad kann ein lokaler Pfad oder eine URL des Typs `http/https/ftp` sein. Remote-URLs des Typs `http/https/ftp` werden nur unterstützt, wenn der Wert der **Type**-Eigenschaft **file** ist. |
|type |Gibt an, ob die zu konfigurierende Ressource ein Verzeichnis oder eine Datei ist. Legen Sie diese Eigenschaft auf **directory** fest, um anzugeben, dass die Ressource ein Verzeichnis ist. Legen Sie sie auf **file** fest, um anzugeben, dass die Ressource eine Datei ist. Der Standardwert ist **file**. |
|Contents |Gibt den Inhalt einer Datei an, z. B. eine bestimmte Zeichenfolge. |
|Checksum |Definiert den zu verwendenden Typ, wenn bestimmt wird, ob zwei Dateien identisch sind. Wenn **Checksum** nicht angegeben ist, wird nur der Datei- oder Verzeichnisnamen für den Vergleich verwendet. Werte sind: **ctime**, **mtime** oder **md5**. |
|Recurse |Gibt an, ob Unterverzeichnisse enthalten sind. Legen Sie diese Eigenschaft auf `$true` fest, um anzugeben, dass Unterverzeichnisse enthalten sein sollen. Der Standardwert lautet `$false`. Diese Eigenschaft ist nur gültig, wenn die **Type**-Eigenschaft auf **directory** festgelegt ist. |
|Force |Bestimmte Dateioperationen (z. B. das Überschreiben einer Datei oder Löschen eines Verzeichnisses, das nicht leer ist), führen zu einem Fehler. Bei Verwenden der **Force**-Eigenschaft werden solche Fehler überschrieben. Standardwert: `$false`. |
|Links |Gibt das gewünschte Verhalten für symbolische Verknüpfungen an. Legen Sie diese Eigenschaft auf **follow** fest, um symbolischen Verknüpfungen zu folgen und Aktionen auf das Ziel der Verknüpfung anzuwenden. Ein Beispiel ist das Kopieren der Datei anstatt der Verknüpfung. Legen Sie diese Eigenschaft auf **manage** fest, um eine Aktion auf die Verknüpfung anzuwenden. Ein Beispiel ist das Kopieren der Verknüpfung selbst. Legen Sie diese Eigenschaft auf **ignore** fest, um symbolische Verknüpfungen zu ignorieren. |
|Group |Der Name der **Gruppe**, die über Zugriffsberechtigungen auf die Datei oder das Verzeichnis besitzen soll. |
|Mode |Gibt die gewünschten Berechtigungen für die Ressource in der Oktal- oder symbolischen Schreibweise an. Beispiele hierfür sind **777** oder **rwxrwxrwx**. Geben Sie bei Verwenden der symbolischen Schreibweise nicht das erste Zeichen an, welches Verzeichnis oder Datei angibt. |
|Besitzer |Der Name der Gruppe, die die Datei oder das Verzeichnis besitzen soll. |

## <a name="common-properties"></a>Allgemeine Eigenschaften

|Eigenschaft |BESCHREIBUNG |
|---|---|
|DependsOn |Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird. Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, „ResourceName“ und dessen Typ „ResourceType“ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Bestimmt, ob das Vorhandensein der Datei geprüft werden soll. Legen Sie diese Eigenschaft auf **Present** fest, um sicherzustellen, dass die Datei vorhanden ist. Legen Sie sie auf **Absent** fest, um sicherzustellen, dass die Datei nicht vorhanden ist. Der Standardwert ist **Present**. |

## <a name="additional-information"></a>Zusätzliche Informationen

Linux und Windows verwenden in Textdateien standardmäßig unterschiedliche Zeilenumbruchzeichen. Diese kann zu unerwarteten Ergebnissen führen, wenn einige Dateien mit **nxFile** auf einem Linux-Computer konfiguriert werden. Es gibt mehrere Möglichkeiten, den Inhalt einer Linux-Datei zu verwalten, um durch unerwartete Zeilenumbruchzeichen verursachte Probleme zu vermeiden:

1. Kopieren der Datei aus einer Remotequelle (HTTP, HTTPS oder FTP)

   Erstellen Sie eine Datei unter Linux mit dem gewünschten Inhalt, und stellen Sie sie auf einem Web- oder FTP-Server bereit, auf den die Knoten zugreifen können, die Sie konfigurieren. Legen Sie die **SourcePath**-Eigenschaft in der Ressource **nxFile** auf die Web- oder FTP-URL zur Datei fest.

   ```powershell
   Import-DSCResource -Module nx

   Node $Node
   {
      nxFile resolvConf
      {
         SourcePath = "http://10.185.85.11/conf/resolv.conf"
         DestinationPath = "/etc/resolv.conf"
         Mode = "644"
         Type = "file"
      }
   }
   ```

1. Lesen Sie den Inhalt der Datei im PowerShell-Skript mit [Get-Content](https://technet.microsoft.com/library/hh849787.aspx), nachdem Sie die **$OFS**-Eigenschaft auf das Verwenden des Linux-Zeilenumbruchzeichens festgelegt haben.

   ```powershell
   Import-DSCResource -Module nx

   Node $Node
   {
      $OFS = "`n"
      $Contents = Get-Content C:\temp\resolv.conf

      nxFile resolvConf
      {
         DestinationPath = "/etc/resolv.conf"
         Mode = "644"
         Type = "file"
         Contents = "$Contents"
      }
   }
   ```

1. Verwenden Sie eine PowerShell-Funktion, um Windows-Zeilenumbrüche durch Linux-Zeilenumbruchzeichen zu ersetzen.

   ```powershell
   Function LinuxString($inputStr){
      $outputStr = $inputStr.Replace("`r`n","`n")
      $outputStr += "`n"
      Return $outputStr
   }

   Import-DSCResource -Module nx

   Node $Node
   {
      $Contents = @'
   search contoso.com
   domain contoso.com
   nameserver 10.185.85.11
   '@
       $Contents = LinuxString $Contents

      nxFile resolvConf
      {
         DestinationPath = "/etc/resolv.conf"
         Mode = "644"
         Type = "file"
         Contents = $Contents
      }
   }
   ```

## <a name="example"></a>Beispiel

Im folgende Beispiel wird sichergestellt, dass das Verzeichnis `/opt/mydir` vorhanden ist und dass eine Datei mit dem angegebenen Inhalt in diesem Verzeichnis vorhanden ist.

```powershell
Import-DSCResource -Module nx

Node $node {
    nxFile DirectoryExample
    {
        Ensure = "Present"
        DestinationPath = "/opt/mydir"
        Type = "Directory"
    }

    nxFile FileExample
    {
        Ensure = "Present"
        Destinationpath = "/opt/mydir/myfile"
        Contents=@"
#!/bin/bash`necho "hello world"`n
"@
        Mode = "755"
        DependsOn = "[nxFile]DirectoryExample"
    }
}
```
