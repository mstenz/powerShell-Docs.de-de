---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Arbeiten mit Druckern
ms.assetid: 4f29ead3-f83b-4706-ac3e-f2154ff38dc5
ms.openlocfilehash: fce1bc129ada3c509c55941a59a70de230edf68f
ms.sourcegitcommit: bc42c9166857147a1ecf9924b718d4a48eb901e3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/03/2019
ms.locfileid: "66470955"
---
# <a name="working-with-printers"></a>Arbeiten mit Druckern

Sie können Windows PowerShell zum Verwalten von Druckern mit WMI und dem COM-Objekt „WScript.Network“ vom WSH verwenden. Wir werden eine Kombination beider Tools verwenden, um bestimmte Aufgaben zu veranschaulichen.

## <a name="listing-printer-connections"></a>Auflisten von Druckerverbindungen

Die einfachste Möglichkeit, die auf einem Computer installierten Drucker aufzulisten, ist die Verwendung der WMI-Klasse **Win32_Printer**:

```powershell
Get-WmiObject -Class Win32_Printer
```

Sie können die Drucker auch mit dem COM-Objekt **WScript.Network** auflisten, das normalerweise in WSH-Skripts verwendet wird:

```powershell
(New-Object -ComObject WScript.Network).EnumPrinterConnections()
```

Da dieser Befehl eine einfache Zeichenfolgenauflistung von Portnamen und Druckergerätenamen ohne unterscheidende Bezeichnungen zurückgibt, ist die Ausgabe nicht leicht zu interpretieren.

## <a name="adding-a-network-printer"></a>Hinzufügen eines Netzwerkdruckers

Verwenden Sie zum Hinzufügen eines neuen Netzwerkdruckers **WScript.Network**:

```powershell
(New-Object -ComObject WScript.Network).AddWindowsPrinterConnection("\\Printserver01\Xerox5")
```

## <a name="setting-a-default-printer"></a>Festlegen eines Standarddruckers

Um mithilfe von WMI den Standarddrucker festzulegen, suchen Sie den Drucker in der **Win32_Printer**-Sammlung, und rufen Sie dann die Methode **SetDefaultPrinter** auf:

```powershell
(Get-WmiObject -ComputerName . -Class Win32_Printer -Filter "Name='HP LaserJet 5Si'").SetDefaultPrinter()
```

**WScript.Network** ist etwas einfacher zu verwenden, da es eine **SetDefaultPrinter**-Methode besitzt, die nur den Druckernamen als Argument akzeptiert:

```powershell
(New-Object -ComObject WScript.Network).SetDefaultPrinter('HP LaserJet 5Si')
```

## <a name="removing-a-printer-connection"></a>Entfernen einer Druckerverbindung

Um eine Druckerverbindung zu entfernen, verwenden Sie die Methode **WScript.Network RemovePrinterConnection**:

```powershell
(New-Object -ComObject WScript.Network).RemovePrinterConnection("\\Printserver01\Xerox5")
```
