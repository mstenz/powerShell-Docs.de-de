---
title: Entwerfen Ihres Windows PowerShell-Anbieters | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- providers [PowerShell Programmer's Guide], designing
ms.assetid: 11d20319-cc40-4227-b810-4af33372b182
caps.latest.revision: 10
ms.openlocfilehash: bfb29fd5df87ffa9ae270c18ce8bfb0c59ee6f90
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870658"
---
# <a name="designing-your-windows-powershell-provider"></a>Entwerfen eines Windows PowerShell-Anbieters

Sie sollten einen Windows PowerShell-Anbieter implementieren, wenn Ihr Produkt oder Ihre Konfiguration einen Satz gespeicherter Daten verfügbar macht, z. b. eine Datenbank, die der Benutzer navigieren oder durchsuchen soll. Außerdem ist es sinnvoll, einen Windows PowerShell-Anbieter zu implementieren, wenn Ihr Produkt einen Container bereitstellt, selbst wenn es sich nicht um einen Container mit mehreren Ebenen handelt. Beispielsweise können Sie einen Windows PowerShell-Container Anbieter implementieren, wenn das Cmdlet-Verb kopieren, verschieben, umbenennen, neu oder Entfernen als Vorgang für Ihr Produkt oder Ihre Konfigurationsdaten sinnvoll ist.

## <a name="windows-powershell-paths-identify-your-provider"></a>Windows PowerShell-Pfade identifizieren Ihren Anbieter

Windows PowerShell Runtime verwendet Windows PowerShell-Pfade, um auf den entsprechenden Windows PowerShell-Anbieter zuzugreifen. Wenn ein Cmdlet einen dieser Pfade angibt, weiß die Laufzeit, welcher Anbieter für den Zugriff auf den zugeordneten Datenspeicher verwendet werden soll. Diese Pfade umfassen Laufwerk qualifizierte Pfade, vom Anbieter qualifizierte Pfade, direkte Anbieter Pfade und Anbieter interne Pfade. Jeder Windows PowerShell-Anbieter muss mindestens einen dieser Pfade unterstützen.

Weitere Informationen zu Windows PowerShell-Pfaden finden Sie unter Funktionsweise von Windows PowerShell.

### <a name="defining-a-drive-qualified-path"></a>Definieren eines Laufwerk qualifizierten Pfads

Um dem Benutzer den Zugriff auf Daten zu ermöglichen, die sich auf einem physischen Laufwerk befinden, muss der Windows PowerShell-Anbieter einen Laufwerk qualifizierten Pfad unterstützen. Dieser Pfad beginnt mit dem Namen des Laufwerks, gefolgt von einem Doppelpunkt:) (z. b. mydrive: \ abc\bar.

### <a name="defining-a-provider-qualified-path"></a>Definieren eines vom Anbieter qualifizierten Pfads

Damit die Windows PowerShell-Laufzeit den Anbieter initialisieren und deren Initialisierung initialisieren kann, muss der Windows PowerShell-Anbieter einen von einem Anbieter qualifizierten Pfad unterstützen. File System::\\\uncshare\abc\bar ist beispielsweise der vom Anbieter qualifizierte Pfad für den File System-Anbieter, der von Windows PowerShell bereitgestellt wird.

### <a name="defining-a-provider-direct-path"></a>Definieren eines direkten Pfads für einen Anbieter

Um den Remote Zugriff auf Ihren Windows PowerShell-Anbieter zuzulassen, sollte er einen Anbieter-Direct-Pfad unterstützen, um direkt an den Windows PowerShell-Anbieter für den aktuellen Speicherort zu übergeben. Der Windows PowerShell-Anbieter für die Registrierung kann z. b. \\\server\regkeypath als Anbieter-Direct-Pfad verwenden.

### <a name="defining-a-provider-internal-path"></a>Definieren eines internen Anbieter Pfads

Um dem Anbieter-Cmdlet den Zugriff auf Daten mit nicht-Windows PowerShell-APIs (Application Programming Interface) zu gestatten, sollte der Windows PowerShell-Anbieter einen Anbieter internen Pfad unterstützen. Dieser Pfad wird nach dem "::" im vom Anbieter qualifizierten Pfad angegeben. Beispielsweise ist der Anbieter interne Pfad für den Windows PowerShell-Anbieter "File System" \\\uncshare\abc\bar.

## <a name="changing-stored-data"></a>Ändern gespeicherter Daten

Wenn Sie Methoden außer Kraft setzen, die den zugrunde liegenden Datenspeicher ändern, müssen Sie immer die [System. Management. Automation. Provider. cmdletprovider. Write teitefibject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) -Methode mit der aktuellen Version des Elements, die von dieser Methode geändert wurde, abrufen. Die Anbieter Infrastruktur bestimmt, ob das Item-Objekt an die Pipeline übergeben werden muss, z. b. wenn der Benutzer den-passthru-Parameter angibt. Wenn das aktuelle Element ein kostspieliger Vorgang ist (leistungsorientiert), können Sie die Context. passthru-Eigenschaft testen, um zu bestimmen, ob Sie das resultierende Element tatsächlich schreiben müssen.

## <a name="choose-a-base-class-for-your-provider"></a>Auswählen einer Basisklasse für Ihren Anbieter

Windows PowerShell bietet eine Reihe von Basisklassen, die Sie verwenden können, um Ihren eigenen Windows PowerShell-Anbieter zu implementieren. Wenn Sie einen Anbieter entwerfen, wählen Sie die Basisklasse aus, die in diesem Abschnitt beschrieben wird und die am besten für Ihre Anforderungen geeignet ist.

Jede Windows PowerShell-Anbieter-Basisklasse stellt eine Reihe von Cmdlets zur Verfügung. In diesem Abschnitt werden die-Cmdlets beschrieben, aber ihre Parameter werden nicht beschrieben.

Mithilfe des Sitzungs Zustands werden von der Windows PowerShell-Runtime verschiedene Location-Cmdlets für bestimmte Windows PowerShell-Anbieter bereitgestellt, wie z. b. die `Get-Location`-, `Set-Location`-, `Pop-Location`-und `Push-Location`-Cmdlets. Mit dem Cmdlet "`Get-Help`" können Sie Informationen zu diesen Location-Cmdlets abrufen.

### <a name="cmdletprovider-base-class"></a>Cmdletprovider-Basisklasse

Die [System. Management. Automation. Provider. cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) -Klasse definiert einen einfachen Windows PowerShell-Anbieter. Diese Klasse unterstützt die Anbieter Deklaration und bietet eine Reihe von Eigenschaften und Methoden, die für alle Windows PowerShell-Anbieter verfügbar sind.
Die-Klasse wird vom-Cmdlet `Get-PSProvider` aufgerufen, um alle verfügbaren Anbieter für eine Sitzung aufzulisten.
Die Implementierung dieses Cmdlets wird durch den Sitzungszustand bereitgestellt.

> [!NOTE]
> Windows PowerShell-Anbieter sind für alle Windows PowerShell-Sprachbereiche verfügbar.

### <a name="drivecmdletprovider-base-class"></a>Drivecmdletprovider-Basisklasse

Die [System. Management. Automation. Provider. drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) -Klasse definiert einen Windows PowerShell-Laufwerks Anbieter, der Vorgänge zum Hinzufügen neuer Laufwerke, zum Entfernen vorhandener Laufwerke und zum Initialisieren von Standardlaufwerken unterstützt. Beispielsweise initialisiert der von Windows PowerShell bereitgestellte File System-Anbieter Laufwerke für alle bereitgestellten Volumes, z. b. Festplatten und CD/DVD-Geräte Laufwerke.

Diese Klasse wird von der [System. Management. Automation. Provider. cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) -Basisklasse abgeleitet. In der folgenden Tabelle sind die Cmdlets aufgelistet, die von dieser Klasse verfügbar gemacht werden. Zusätzlich zu den aufgelisteten-Cmdlets (durch den Sitzungszustand verfügbar gemacht) ist das Cmdlet "`Get-PSDrive`", das zum Abrufen der verfügbaren Laufwerke verwendet wird.

|      Cmdlet      |                             Definition                              |
| ---------------- | ------------------------------------------------------------------- |
| `New-PSDrive`    | Erstellt ein neues Laufwerk für die Sitzung und streamt Laufwerks Informationen. |
| `Remove-PSDrive` | Entfernt ein Laufwerk aus der Sitzung.                                   |

### <a name="itemcmdletprovider-base-class"></a>Itemcmdletprovider-Basisklasse

Die [System. Management. Automation. Provider. itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) -Klasse definiert einen Windows PowerShell-Element Anbieter, der Vorgänge für die einzelnen Elemente des Datenspeicher ausführt und keine Container-oder Navigationsfunktionen annimmt. Diese Klasse wird von der [System. Management. Automation. Provider. drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) -Basisklasse abgeleitet. In der folgenden Tabelle sind die Cmdlets aufgelistet, die von dieser Klasse verfügbar gemacht werden.

|     Cmdlet     |                                                                                                                                                            Definition                                                                                                                                                            |
| -------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Clear-Item`   | Löscht den aktuellen Inhalt von Elementen an der angegebenen Position und ersetzt ihn durch den vom Anbieter angegebenen "Clear"-Wert. Dieses Cmdlet übergibt kein Ausgabe Objekt über die Pipeline, es sei denn, der `PassThru` Parameter ist angegeben.                                                                                   |
| `Get-Item`     | Ruft Elemente aus der angegebenen Position ab und streamt die resultierenden Objekte.                                                                                                                                                                                                                                                  |
| `Invoke-Item`  | Ruft die Standardaktion für das Element im angegebenen Pfad auf.                                                                                                                                                                                                                                                                   |
| `Set-Item`     | Legt ein Element an der angegebenen Position mit dem angegebenen Wert fest. Dieses Cmdlet übergibt kein Ausgabe Objekt über die Pipeline, es sei denn, der `PassThru` Parameter ist angegeben.                                                                                                                                                   |
| `Resolve-Path` | Löst die Platzhalter für einen Windows PowerShell-Pfad auf und streamt Pfadinformationen.                                                                                                                                                                                                                                              |
| `Test-Path`    | Testet auf den angegebenen Pfad und gibt `true` zurück, sofern vorhanden, und andernfalls `false`. Dieses Cmdlet wird implementiert, um den `IsContainer`-Parameter für die [System. Management. Automation. Provider. cmdletprovider. Write teitemject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) -Methode zu unterstützen. |

### <a name="containercmdletprovider-base-class"></a>Containercmdletprovider-Basisklasse

Die [System. Management. Automation. Provider. containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) -Klasse definiert einen Windows PowerShell-Container Anbieter, der dem Benutzer einen Container für Datenspeicher Elemente verfügbar macht. Beachten Sie, dass ein Windows PowerShell-Container Anbieter nur verwendet werden kann, wenn es einen Container (keine unter-Container) mit Elementen gibt. Wenn es sich um Container handelt, müssen Sie einen Windows PowerShell-Navigations Anbieter implementieren.

Diese Klasse wird von der [System. Management. Automation. Provider. itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) -Basisklasse abgeleitet. In der folgenden Tabelle sind die von dieser Klasse implementierten Cmdlets definiert.

|     Cmdlet      |                                                                        Definition                                                                        |
| --------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Copy-Item`     | Kopiert Elemente von einem Speicherort in einen anderen. Dieses Cmdlet übergibt kein Ausgabe Objekt über die Pipeline, es sei denn, der `PassThru` Parameter ist angegeben. |
| `Get-Childitem` | Ruft die untergeordneten Elemente an der angegebenen Position ab und streamt sie als-Objekte.                                                                        |
| `New-Item`      | Erstellt neue Elemente an der angegebenen Position und streamt das resultierende Objekt.                                                                           |
| `Remove-Item`   | Entfernt Elemente aus der angegebenen Position.                                                                                                               |
| `Rename-Item`   | Benennt ein Element an der angegebenen Position um. Dieses Cmdlet übergibt kein Ausgabe Objekt über die Pipeline, es sei denn, der `PassThru` Parameter ist angegeben. |

### <a name="navigationcmdletprovider-base-class"></a>Navigationcmdletprovider-Basisklasse

Die [System. Management. Automation. Provider. navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) -Klasse definiert einen Windows PowerShell-Navigations Anbieter, der Vorgänge für Elemente ausführt, die mehr als einen Container verwenden. Diese Klasse wird von der [System. Management. Automation. Provider. containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) -Basisklasse abgeleitet. In der folgenden Tabelle sind die Cmdlets aufgelistet, die von dieser Klasse verfügbar gemacht werden.

|    Cmdlet    |                                                                      Definition                                                                      |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| Kombinieren-Pfad | Kombiniert zwei Pfade zu einem einzelnen Pfad, wobei ein Anbieter spezifisches Trennzeichen zwischen Pfaden verwendet wird. Dieses Cmdlet streamt Zeichen folgen.                               |
| `Move-Item`  | Verschiebt Elemente an den angegebenen Speicherort. Dieses Cmdlet übergibt kein Ausgabe Objekt über die Pipeline, es sei denn, der `PassThru` Parameter ist angegeben. |

Ein verwandtes Cmdlet ist das grundlegende Cmdlet "Cmdlet", das von Windows PowerShell bereitgestellt wird. Dieses Cmdlet kann zum Analysieren eines Windows PowerShell-Pfads verwendet werden, um den `Parent`-Parameter zu unterstützen. Die übergeordnete Pfad Zeichenfolge wird gestreamt.

## <a name="select-provider-interfaces-to-support"></a>Anbieter Schnittstellen zur Unterstützung auswählen

Zusätzlich zur Ableitung von einer der Windows PowerShell-Basisklassen kann Ihr Windows PowerShell-Anbieter auch andere Funktionen unterstützen, indem er von einer oder mehreren der folgenden Anbieter Schnittstellen ableitet. In diesem Abschnitt werden die Schnittstellen und die von den einzelnen unterstützten Cmdlets definiert. Es werden nicht die Parameter für die von der Schnittstelle unterstützten Cmdlets beschrieben. Cmdlet-Parameterinformationen sind Online mithilfe der Cmdlets `Get-Command` und `Get-Help` verfügbar.

### <a name="icontentcmdletprovider"></a>Icontentcmdletprovider

Die [System. Management. Automation. Provider. icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) -Schnittstelle definiert einen Inhaltsanbieter, der Vorgänge für den Inhalt eines Datenelements ausführt. In der folgenden Tabelle sind die von dieser Schnittstelle verfügbar gemachten Cmdlets aufgeführt.

|     Cmdlet      |                                                                                        Definition                                                                                        |
| --------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Add-Content`   | Fügt den angegebenen Wert Längen an den Inhalt des angegebenen Elements an. Dieses Cmdlet übergibt kein Ausgabe Objekt über die Pipeline, es sei denn, der `PassThru` Parameter ist angegeben. |
| `Clear-Content` | Legt den Inhalt des angegebenen Elements auf den Wert "Clear" fest. Dieses Cmdlet übergibt kein Ausgabe Objekt über die Pipeline, es sei denn, der `PassThru` Parameter ist angegeben.               |
| `Get-Content`   | Ruft den Inhalt der angegebenen Elemente ab und streamt die resultierenden Objekte.                                                                                                         |
| `Set-Content`   | Ersetzt den vorhandenen Inhalt für die angegebenen Elemente. Dieses Cmdlet übergibt kein Ausgabe Objekt über die Pipeline, es sei denn, der `PassThru` Parameter ist angegeben.                     |

### <a name="ipropertycmdletprovider"></a>Ipropertycmdletprovider

Die [System. Management. Automation. Provider. ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) -Schnittstelle definiert einen Windows PowerShell-Eigenschaften Anbieter, der Vorgänge für die Eigenschaften von Elementen im Datenspeicher ausführt. In der folgenden Tabelle sind die von dieser Schnittstelle verfügbar gemachten Cmdlets aufgeführt.

> [!NOTE]
> Der `Path`-Parameter für diese Cmdlets gibt einen Pfad zu einem Element an, anstatt eine Eigenschaft zu identifizieren.

|        Cmdlet        |                                                                                   Definition                                                                                    |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Clear-ItemProperty` | Legt die Eigenschaften der angegebenen Elemente auf den "Clear"-Wert fest. Dieses Cmdlet übergibt kein Ausgabe Objekt über die Pipeline, es sei denn, der `PassThru` Parameter ist angegeben.      |
| `Get-ItemProperty`   | Ruft Eigenschaften aus den angegebenen Elementen ab und streamt die resultierenden Objekte.                                                                                                |
| `Set-ItemProperty`   | Legt die Eigenschaften der angegebenen Elemente mit den angegebenen Werten fest. Dieses Cmdlet übergibt kein Ausgabe Objekt über die Pipeline, es sei denn, der `PassThru` Parameter ist angegeben. |

### <a name="idynamicpropertycmdletprovider"></a>Idynamicpropertycmdletprovider

Die [System. Management. Automation. Provider. idynamicpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider) -Schnittstelle, die von [System. Management. Automation. Provider. ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider)abgeleitet wurde, definiert einen Anbieter, der dynamische Parameter für die unterstützten Cmdlets angibt. Diese Art von Anbieter verarbeitet Vorgänge, für die Eigenschaften zur Laufzeit definiert werden können, z. b. ein neuer Eigenschafts Vorgang. Solche Vorgänge sind für Elemente, die statisch definierte Eigenschaften haben, nicht möglich.
In der folgenden Tabelle sind die von dieser Schnittstelle verfügbar gemachten Cmdlets aufgeführt.

|        Cmdlet         |                                                                                Definition                                                                                |
| --------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `Copy-ItemProperty`   | Kopiert eine Eigenschaft aus dem angegebenen Element in ein anderes Element. Dieses Cmdlet übergibt kein Ausgabe Objekt über die Pipeline, es sei denn, der `PassThru` Parameter ist angegeben. |
| `Move-ItemProperty`   | Verschiebt eine Eigenschaft aus dem angegebenen Element in ein anderes Element. Dieses Cmdlet übergibt kein Ausgabe Objekt über die Pipeline, es sei denn, der `PassThru` Parameter ist angegeben.  |
| `New-ItemProperty`    | Erstellt eine Eigenschaft für die angegebenen Elemente und streamt die resultierenden Objekte.                                                                                             |
| `Remove-ItemProperty` | Entfernt eine Eigenschaft für die angegebenen Elemente.                                                                                                                              |
| `Rename-ItemProperty` | Benennt eine Eigenschaft der angegebenen Elemente um. Dieses Cmdlet übergibt kein Ausgabe Objekt über die Pipeline, es sei denn, der `PassThru` Parameter ist angegeben.                 |

### <a name="isecuritydescriptorcmdletprovider"></a>Isecuritydescriptor cmdletprovider

Die [System. Management. Automation. Provider. isecuritydescriptorcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ISecurityDescriptorCmdletProvider) -Schnittstelle fügt einem Anbieter Sicherheits deskriptorfunktionen hinzu. Diese Schnittstelle ermöglicht es dem Benutzer, Sicherheits Deskriptorinformationen für ein Element im Datenspeicher zu erhalten und festzulegen. In der folgenden Tabelle sind die von dieser Schnittstelle verfügbar gemachten Cmdlets aufgeführt.

|  Cmdlet   |                                                                                                                                                                                                          Definition                                                                                                                                                                                                          |
| --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Get-Acl` | Ruft die Informationen ab, die in einer Zugriffs Steuerungs Liste (Access Control List, ACL) enthalten sind. diese ist Teil einer Sicherheits Beschreibung, die zum Schutz von Betriebssystemressourcen verwendet wird, z. b. eine Datei oder ein Objekt.                                                                                                                                                                                                                                      |
| `Set-Acl` | Legt die Informationen für eine ACL fest. Sie befindet sich in der Form einer Instanz von [System. Security. AccessControl. ObjectSecurity](/dotnet/api/System.Security.AccessControl.ObjectSecurity) für die Elemente, die für den angegebenen Pfad festgelegt sind. Dieses Cmdlet kann Informationen zu Dateien, Schlüsseln und unter Schlüsseln in der Registrierung oder einem beliebigen anderen Anbieter Element festlegen, wenn der Windows PowerShell-Anbieter die Einstellung von Sicherheitsinformationen unterstützt. |

## <a name="see-also"></a>Siehe auch

[Erstellen von Windows PowerShell-Anbietern](./how-to-create-a-windows-powershell-provider.md)

[Funktionsweise von Windows PowerShell](/previous-versions/ms714658(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)