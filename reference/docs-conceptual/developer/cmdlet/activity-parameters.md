---
title: Aktivitäts Parameter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6e4e0cf6-19e0-44b8-8b40-d6f6075276cf
caps.latest.revision: 5
ms.openlocfilehash: 489d8bcdabe904d6a3d2bc6cdb9d7e23d09cbef2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364639"
---
# <a name="activity-parameters"></a>Aktivitätsparameter

In der folgenden Tabelle sind die empfohlenen Namen und Funktionen für Aktivitäts Parameter aufgeführt.

|Parameter|Funktion|
|---|---|
|**Anfügen**<br>Datentyp: Switchparameter|Implementieren Sie diesen Parameter, sodass der Benutzer Inhalt am Ende einer Ressource hinzufügen kann, wenn der-Parameter angegeben wird.|
|**CaseSensitive**<br>Datentyp: Switchparameter|Implementieren Sie diesen Parameter, damit der Benutzer bei Angabe des-Parameters die Groß-/Kleinschreibung unterscheidet.|
|**S**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, damit der Benutzer eine Befehls Zeichenfolge angeben kann, die ausgeführt wird.|
|**Compatibleversion**<br>Datentyp: System. Version-Objekt|Implementieren Sie diesen Parameter, sodass der Benutzer die Semantik angeben kann, mit der das Cmdlet für die Kompatibilität mit früheren Versionen kompatibel sein muss.|
|**Komprimieren**<br>Datentyp: Switchparameter|Implementieren Sie diesen Parameter, damit die Datenkomprimierung verwendet wird, wenn der-Parameter angegeben wird.|
|**Komprimieren**<br>Datentyp: Schlüsselwort|Implementieren Sie diesen Parameter, sodass der Benutzer den Algorithmus angeben kann, der für die Datenkomprimierung verwendet werden soll.|
|**Continuous**<br>Datentyp: Switchparameter|Implementieren Sie diesen Parameter, damit die Daten verarbeitet werden, bis der Benutzer das Cmdlet beendet, wenn der-Parameter angegeben wird. Wenn der-Parameter nicht angegeben wird, verarbeitet das Cmdlet eine vordefinierte Datenmenge und beendet dann den Vorgang.|
|**Stelle**<br>Datentyp: Switchparameter|Implementieren Sie diesen Parameter, um anzugeben, dass eine Ressource erstellt wird, wenn Sie nicht bereits vorhanden ist, wenn der-Parameter angegeben wird.|
|**Lösch**<br>Datentyp: Switchparameter|Implementieren Sie diesen Parameter, damit Ressourcen gelöscht werden, wenn das Cmdlet den Vorgang abgeschlossen hat, wenn der-Parameter angegeben wird.|
|**Erschütterung**<br>Datentyp: Switchparameter|Implementieren Sie diesen Parameter, um anzugeben, dass ausstehende Arbeitselemente verarbeitet werden, bevor das Cmdlet neue Daten verarbeitet, wenn der Parameter angegeben wird. Wenn der-Parameter nicht angegeben wird, werden die Arbeitselemente sofort verarbeitet.|
|**Löschen**<br>Datentyp: Int32|Implementieren Sie diesen Parameter, sodass der Benutzer angeben kann, wie oft eine Ressource gelöscht werden soll, bevor Sie gelöscht wird.|
|**ERRORLEVEL**<br>Datentyp: Int32|Implementieren Sie diesen Parameter, sodass der Benutzer die Ebene der Fehler angeben kann, die gemeldet werden sollen.|
|**Schli**<br>Datentyp: Zeichenfolge []|Implementieren Sie diesen Parameter, sodass der Benutzer etwas von einer Aktivität ausschließen kann. Weitere Informationen zum Verwenden von Eingabe Filtern finden Sie unter [Eingabe Filter Parameter](input-filter-parameters.md).|
|**Filter**<br>Datentyp: Schlüsselwort|Implementieren Sie diesen Parameter, sodass der Benutzer einen Filter angeben kann, mit dem die Ressourcen ausgewählt werden, für die die Cmdlet-Aktion ausgeführt werden soll. Weitere Informationen zum Verwenden von Eingabe Filtern finden Sie unter [Eingabe Filter Parameter](./input-filter-parameters.md).|
|**Führen Sie**<br>Datentyp: Switchparameter|Implementieren Sie diesen Parameter, sodass der Fortschritt nachverfolgt wird, wenn der-Parameter angegeben wird.|
|**Geltende**<br>Datentyp: Switchparameter|Implementieren Sie diesen Parameter, um anzugeben, dass der Benutzer eine Aktion ausführen kann, auch wenn Einschränkungen auftreten, wenn der-Parameter angegeben wird. Der-Parameter lässt nicht zu, dass die Sicherheit gefährdet wird. Mit diesem Parameter kann ein Benutzer beispielsweise eine schreibgeschützte Datei überschreiben.|
|**Darunter**<br>Datentyp: Zeichenfolge []|Implementieren Sie diesen Parameter, sodass der Benutzer etwas in eine Aktivität einschließen kann. Weitere Informationen zum Verwenden von Eingabe Filtern finden Sie unter [Eingabe Filter Parameter](input-filter-parameters.md).|
|**Inkrementelle**<br>Datentyp: Switchparameter|Implementieren Sie diesen Parameter, um anzugeben, dass die Verarbeitung inkrementell ausgeführt wird, wenn der Parameter angegeben wird. Mit diesem Parameter kann ein Benutzer beispielsweise inkrementelle Sicherungen durchführen, die Dateien nur seit der letzten Sicherung sichern.|
|**InputObject**<br>Datentyp: Object|Implementieren Sie diesen Parameter, wenn das Cmdlet Eingaben von anderen Cmdlets annimmt. Wenn Sie einen **Inputobject** -Parameter definieren, geben Sie immer das Schlüsselwort **valuefrompipeline** an, wenn Sie das **Parameter** Attribut deklarieren. Weitere Informationen zum Verwenden von Eingabe Filtern finden Sie unter [Eingabe Filter Parameter](./input-filter-parameters.md).|
|**Setze**<br>Datentyp: Switchparameter|Implementieren Sie diesen Parameter, damit das Cmdlet ein Element einfügt, wenn der Parameter angegeben wird.|
|**Interaktive**<br>Datentyp: Switchparameter|Implementieren Sie diesen Parameter, damit das Cmdlet interaktiv mit dem Benutzer arbeitet, wenn der Parameter angegeben wird.|
|**Tri**<br>Datentyp: Hashtable|Implementieren Sie diesen Parameter, sodass der Benutzer eine Hash Tabelle mit Schlüsselwörtern angeben kann, die die Werte enthält. Das folgende Beispiel zeigt Beispiel Werte für den **Interval** -Parameter: `-interval @{ResumeScan=15; Retry=3}`.|
|**Log**<br>Datentyp: Switchparameter|Implementieren Sie diesen Parameter, um die Aktionen des-Cmdlets zu überwachen, wenn der-Parameter angegeben wird.|
|**NoClobber**<br>Datentyp: Switchparameter|Implementieren Sie diesen Parameter, damit die Ressource nicht überschrieben wird, wenn der-Parameter angegeben wird. Dieser Parameter gilt in der Regel für Cmdlets, die neue Objekte erstellen, sodass Sie daran gehindert werden können, vorhandene Objekte mit demselben Namen zu überschreiben.|
|**Informiert**<br>Datentyp: Switchparameter|Implementieren Sie diesen Parameter, sodass der Benutzer benachrichtigt wird, dass die Aktivität beendet ist, wenn der-Parameter angegeben wird.|
|**Notifyaddress**<br>Datentyp: e-Mail-Adresse|Implementieren Sie diesen Parameter, sodass der Benutzer die e-Mail-Adresse angeben kann, mit der eine Benachrichtigung gesendet wird, wenn **der Benachrichtigungs Parameter angegeben** wird.|
|**XX**<br>Datentyp: Switchparameter|Implementieren Sie diesen Parameter, damit das Cmdlet alle vorhandenen Daten überschreibt, wenn der-Parameter angegeben wird.|
|**Nahen**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, sodass der Benutzer eine Eingabeaufforderung für das Cmdlet angeben kann.|
|**Geschwiegen**<br>Datentyp: Switchparameter|Implementieren Sie diesen Parameter, damit das Cmdlet Benutzer Feedback während seiner Aktionen unterdrückt, wenn der Parameter angegeben wird.|
|**Recurse**<br>Datentyp: Switchparameter|Implementieren Sie diesen Parameter, damit das Cmdlet rekursiv seine Aktionen für Ressourcen ausführt, wenn der Parameter angegeben wird.|
|**Reparatur**<br>Datentyp: Switchparameter|Implementieren Sie diesen Parameter, damit das Cmdlet versucht, etwas aus einem fehlerfreien Zustand zu korrigieren, wenn der Parameter angegeben wird.|
|**Repairren String**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, sodass der Benutzer eine Zeichenfolge angeben kann, die verwendet wird, wenn der **Repair** -Parameter angegeben wird.|
|**Wiederholen Sie**<br>Datentyp: Int32|Implementieren Sie diesen Parameter, sodass der Benutzer angeben kann, wie oft das Cmdlet versucht, eine Aktion durchzuführen.|
|**Auswahl**<br>Datentyp: Schlüsselwort Array|Implementieren Sie diesen Parameter, sodass der Benutzer ein Array der Elementtypen angeben kann.|
|**Streich**<br>Datentyp: Switchparameter|Implementieren Sie diesen Parameter, sodass der Benutzer mehrere Ausgabe Objekte über die Pipeline streamen kann, wenn der-Parameter angegeben wird.|
|**Strengeren**<br>Datentyp: Switchparameter|Implementieren Sie diesen Parameter, sodass alle Fehler als Fehler beim Abbrechen behandelt werden, wenn der-Parameter angegeben wird.|
|**Templocation**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, sodass der Benutzer den Speicherort der temporären Daten angeben kann, die während der Ausführung des Cmdlets verwendet werden.|
|**Zeit**<br>Datentyp: Int32|Implementieren Sie diesen Parameter, sodass der Benutzer das Timeout Intervall (in Millisekunden) angeben kann.|
|**TRUNCATE**<br>Datentyp: Switchparameter|Implementieren Sie diesen Parameter, damit das Cmdlet seine Aktionen abschneidet, wenn der-Parameter angegeben wird. Wenn der-Parameter nicht angegeben ist, führt das Cmdlet eine weitere Aktion aus.|
|**Weisen**<br>Datentyp: Switchparameter|Implementieren Sie diesen Parameter, damit das Cmdlet testet, ob eine Aktion aufgetreten ist, wenn der Parameter angegeben wird.|
|**Warte**<br>Datentyp: Switchparameter|Implementieren Sie diesen Parameter, damit das Cmdlet auf Benutzereingaben wartet, bevor es fortgesetzt wird, wenn der Parameter angegeben wird.
|**Wartezeit –**<br>Datentyp: Int32|Implementieren Sie diesen Parameter, sodass der Benutzer die Dauer (in Sekunden) angeben kann, die das Cmdlet auf die Benutzereingabe wartet, wenn der **Wait** -Parameter angegeben wird.|

## <a name="see-also"></a>Weitere Informationen

[Cmdlet-Parameter](./cmdlet-parameters.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
