---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: Arbeiten mit Druckern
ms.openlocfilehash: 1d6b9a57ec61f06af694757dc8017d50b4dd40fe
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "78935209"
---
# <a name="working-with-printers-in-windows"></a>Arbeiten mit Druckern in Windows

Sie können Windows PowerShell zum Verwalten von Druckern mit WMI und dem COM-Objekt **WScript.Network** vom WSH verwenden. Wir werden eine Kombination beider Tools verwenden, um bestimmte Aufgaben zu veranschaulichen.

## <a name="listing-printer-connections"></a>Auflisten von Druckerverbindungen

Die einfachste Möglichkeit, die auf einem Computer installierten Drucker aufzulisten, ist die Verwendung der WMI-Klasse **Win32_Printer**:

```powershell
Get-CimInstance -Class Win32_Printer
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
$printer = Get-CimInstance -Class Win32_Printer -Filter "Name='HP LaserJet 5Si'"
Invoke-CimMethod -InputObject $printer -MethodName SetDefaultPrinter
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
