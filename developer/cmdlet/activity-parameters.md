---
title: Aktivitätsparameter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6e4e0cf6-19e0-44b8-8b40-d6f6075276cf
caps.latest.revision: 5
ms.openlocfilehash: 489d8bcdabe904d6a3d2bc6cdb9d7e23d09cbef2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075187"
---
# <a name="activity-parameters"></a>Aktivitätsparameter

Die folgende Tabelle enthält die empfohlenen Namen und die Funktionalität für den Aktivitätsparameter.

|Parameter|Funktion|
|---|---|
|**Anfügen**<br>Datentyp: SwitchParameter|Implementieren Sie diesen Parameter, damit der Benutzer Inhalt am Ende eine Ressource hinzufügen kann, wenn der Parameter angegeben wird.|
|**CaseSensitive**<br>Datentyp: SwitchParameter|Implementieren Sie diesen Parameter aus, damit der Benutzer Groß-/Kleinschreibung erforderlich sein kann, wenn der Parameter angegeben wird.|
|**Befehl**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter aus, damit die Benutzer eine Befehlszeichenfolge ausgeführt angeben können.|
|**CompatibleVersion**<br>Datentyp: System.Version object|Implementieren Sie diesen Parameter aus, damit die Benutzer die Semantik angeben können, denen mit dem-Cmdlet mit für Kompatibilität mit früheren Versionen kompatibel sein müssen.|
|**Komprimieren**<br>Datentyp: SwitchParameter|Implementieren Sie diesen Parameter, sodass die datenkomprimierung verwendet wird, wenn der Parameter angegeben wird.|
|**Komprimieren**<br>Datentyp: Schlüsselwort|Implementieren Sie diesen Parameter, damit der Benutzer den Algorithmus für die datenkomprimierung angeben kann.|
|**fortlaufende**<br>Datentyp: SwitchParameter|Implementieren Sie diesen Parameter, sodass Daten verarbeitet werden, bis der Benutzer das-Cmdlet beendet wird, wenn der Parameter angegeben wird. Wenn der Parameter nicht angegeben ist, wird das Cmdlet eine vordefinierte Menge an Daten verarbeitet und beendet dann den Vorgang.|
|**Erstellen**<br>Datentyp: SwitchParameter|Implementieren Sie diesen Parameter, um anzugeben, dass eine Ressource erstellt wird, wenn eine nicht bereits vorhanden ist, wenn der Parameter angegeben wird.|
|**Löschen**<br>Datentyp: SwitchParameter|Implementieren Sie diesen Parameter, sodass Ressourcen gelöscht werden, wenn das-Cmdlet der Vorgang abgeschlossen ist, wenn der Parameter angegeben wird.|
|**Abfluss**<br>Datentyp: SwitchParameter|Implementieren Sie diesen Parameter, um anzugeben, dass ausstehende Arbeitsobjekte verarbeitet werden, bevor Sie das Cmdlet neue Daten verarbeitet, wenn der Parameter angegeben wird. Wenn der Parameter nicht angegeben ist, werden die Arbeitselemente sofort verarbeitet.|
|**Löschen**<br>Datentyp: Int32|Implementieren Sie diesen Parameter, damit die Benutzer an, wie oft angeben können, die eine Ressource gelöscht wird, bevor er gelöscht wird.|
|**ErrorLevel**<br>Datentyp: Int32|Implementieren Sie diesen Parameter, damit der Benutzer die Ebene der Fehler gemeldet angeben kann.|
|**Ausschließen**<br>Datentyp: String[]|Implementieren Sie diesen Parameter, damit der Benutzer etwas von einer Aktivität ausschließen kann. Weitere Informationen zur Verwendung von Eingabefilter finden Sie unter [Eingabeparameter Filter](input-filter-parameters.md).|
|**Filter**<br>Datentyp: Schlüsselwort|Implementieren Sie diesen Parameter, damit der Benutzer einen Filter angeben kann, der die Ressourcen auf dem zum Ausführen der Cmdlet-Aktion auswählt. Weitere Informationen zur Verwendung von Eingabefilter finden Sie unter [Eingabeparameter Filter](./input-filter-parameters.md).|
|**Gehen Sie folgendermaßen vor**<br>Datentyp: SwitchParameter|Implementieren Sie diesen Parameter, sodass Status nachverfolgt wird, wenn der Parameter angegeben wird.|
|**Force**<br>Datentyp: SwitchParameter|Implementieren Sie diesen Parameter, um anzugeben, dass der Benutzer eine Aktion ausführen kann, selbst wenn Einschränkungen gefunden werden, wenn der Parameter angegeben wird. Der Parameter lässt keine Sicherheit, kompromittiert zu sein. Dieser Parameter kann z. B. einen Benutzer, die eine schreibgeschützte Datei zu überschreiben.|
|**einschließen**<br>Datentyp: String[]|Implementieren Sie diesen Parameter, damit der Benutzer etwas in einer Aktivität einfügen kann. Weitere Informationen zur Verwendung von Eingabefilter finden Sie unter [Eingabeparameter Filter](input-filter-parameters.md).|
|**Inkrementelle**<br>Datentyp: SwitchParameter|Implementieren Sie diesen Parameter, um anzugeben, dass die Verarbeitung inkrementell ausgeführt wird, wenn der Parameter angegeben wird. Dieser Parameter kann z. B. einen Benutzer, die inkrementelle Sicherungen durchführen, die seit der letzten Sicherung nur Dateien zu sichern.|
|**InputObject**<br>Datentyp: Objekt|Implementieren Sie diesen Parameter aus, wenn das Cmdlet von anderen Cmdlets verwendet. Beim Definieren einer **inputobject-Parameter** Parameter immer angeben, die **ValueFromPipeline** Schlüsselwort beim Deklarieren der **Parameter** Attribut. Weitere Informationen zur Verwendung von Eingabefilter finden Sie unter [Eingabeparameter Filter](./input-filter-parameters.md).|
|**Einfügen**<br>Datentyp: SwitchParameter|Implementieren Sie diesen Parameter, sodass das Cmdlet ein Element einfügt, wenn der Parameter angegeben wird.|
|**Interaktive**<br>Datentyp: SwitchParameter|Implementieren Sie diesen Parameter, sodass das Cmdlet interaktiv mit dem Benutzer funktioniert, wenn der Parameter angegeben wird.|
|**Intervall**<br>Datentyp: HashTable|Implementieren Sie diesen Parameter, damit der Benutzer eine Hashtabelle mit Schlüsselwörtern angeben kann, die das Werte enthält. Das folgende Beispiel zeigt Beispielwerte für die **Intervall** Parameter: `-interval @{ResumeScan=15; Retry=3}`.|
|**Log**<br>Datentyp: SwitchParameter|Implementieren Sie diese Prüfung Parameter die Aktionen des-Cmdlets, wenn der Parameter angegeben wird.|
|**NoClobber**<br>Datentyp: SwitchParameter|Implementieren Sie diesen Parameter, sodass die Ressource nicht überschrieben wird, wenn der Parameter angegeben wird. Dieser Parameter gilt im Allgemeinen um Cmdlets, mit die neue Objekte erstellen, sodass sie können verhindert werden vorhandene Objekte mit demselben Namen überschreiben.|
|**Notify**<br>Datentyp: SwitchParameter|Implementieren Sie diesen Parameter, sodass der Benutzer benachrichtigt, dass die Aktivität abgeschlossen ist, wenn der Parameter angegeben wird.|
|**NotifyAddress**<br>Datentyp: E-Mail-Adresse|Implementieren Sie diesen Parameter, damit der Benutzer die e-Mail-Adresse verwenden, um das Senden einer Benachrichtigung angeben, kann bei der **benachrichtigen** Parameter angegeben ist.|
|**Overwrite**<br>Datentyp: SwitchParameter|Implementieren Sie diesen Parameter, sodass das Cmdlet alle vorhandenen Daten überschreibt, wenn der Parameter angegeben wird.|
|**Prompt**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, damit der Benutzer eine Eingabeaufforderung für das Cmdlet angeben kann.|
|**Quiet**<br>Datentyp: SwitchParameter|Implementieren Sie diesen Parameter, sodass das Cmdlet unterdrückt Feedback von Benutzern bei der die Aktionen, wenn der Parameter angegeben wird.|
|**Recurse**<br>Datentyp: SwitchParameter|Implementieren Sie diesen Parameter, sodass das Cmdlet rekursiv führt die Aktionen für Ressourcen, wenn der Parameter angegeben wird.|
|**Reparieren**<br>Datentyp: SwitchParameter|Implementieren Sie diesen Parameter, sodass das Cmdlet versucht, etwas aus einem unterbrochenen Zustand zu beheben, wenn der Parameter angegeben wird.|
|**RepairString**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, damit die Benutzer verwenden, wenn eine Zeichenfolge angeben, können die **Reparatur** Parameter angegeben ist.|
|**"Wiederholen"**<br>Datentyp: Int32|Implementieren Sie diesen Parameter aus, damit die Benutzer angeben können, wie oft das-Cmdlet eine Aktion versucht.|
|**Wählen Sie**<br>Datentyp: Schlüsselwort-array|Implementieren Sie diesen Parameter, damit der Benutzer auf ein Array von Typen von Elementen angeben kann.|
|**Stream**<br>Datentyp: SwitchParameter|Implementieren Sie diesen Parameter aus, damit der Benutzer mehrere Ausgabeobjekte über die Pipeline streamen kann, wenn der Parameter angegeben wird.|
|**Strict**<br>Datentyp: SwitchParameter|Implementieren Sie diesen Parameter, sodass alle Fehler als Fehler behandelt werden, wenn der Parameter angegeben wird.|
|**TempLocation**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter aus, damit die Benutzer den Speicherort der temporären Daten angeben können, die während des Vorgangs des-Cmdlets verwendet wird.|
|**Timeout**<br>Datentyp: Int32|Implementieren Sie diesen Parameter, damit der Benutzer das Timeout-Intervall (in Millisekunden) angeben kann.|
|**Truncate**<br>Datentyp: SwitchParameter|Implementieren Sie diesen Parameter, sodass das Cmdlet die Aktionen abgeschnitten wird, wenn der Parameter angegeben wird. Wenn der Parameter nicht angegeben wird, führt das Cmdlet eine andere Aktion aus.|
|**Verify**<br>Datentyp: SwitchParameter|Implementieren Sie diesen Parameter, sodass das Cmdlet prüft wird, um festzustellen, ob eine Aktion durchgeführt wurde, wenn der Parameter angegeben wird.|
|**Warte**<br>Datentyp: SwitchParameter|Implementieren Sie diesen Parameter, sodass das-Cmdlet für Benutzereingaben gewartet wird, bevor Sie fortfahren, wenn der Parameter angegeben wird.
|**WaitTime**<br>Datentyp: Int32|Implementieren Sie diesen Parameter, damit der Benutzer die Dauer (in Sekunden) angeben kann, dass das Cmdlet für den Benutzer warten soll, geben Sie bei der **warten** Parameter angegeben ist.|

## <a name="see-also"></a>Weitere Informationen

[Cmdlet-Parameter](./cmdlet-parameters.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
