---
ms.date: 08/14/2018
keywords: powershell,cmdlet
title: Einführung in die Windows PowerShell ISE
ms.openlocfilehash: 09a28b295855fd2a3c62bba8a681399dae3454f8
ms.sourcegitcommit: 3402a478cf118c11a5642038eb117bc76553e3ab
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53411581"
---
# <a name="the-windows-powershell-ise"></a>Der Windows PowerShell ISE

Windows PowerShell Integrated Scripting Environment (ISE) ist eine Hostanwendung für Windows PowerShell. Sie können in der ISE Ausführen von Befehlen und schreiben, testen und Debuggen von Skripts in einer einzelnen Windows-basierten grafischen Benutzeroberfläche. Die ISE bietet mehrzeiliger Bearbeitung, Vervollständigung mit der Tab, Syntaxfarben, Selektiver Ausführung, kontextbezogener Hilfe und Support für rechts-nach-links-Sprachen. Menüelemente und Tastenkombinationen sind vielen der Aufgaben zugeordnet, die Sie auch in der Windows PowerShell-Konsole ausführen würden. Z. B. Wenn Sie ein Skript in der ISE Debuggen, können Sie auf eine einzige Zeile Code im Bearbeitungsbereich "zum Festlegen eines Haltepunkts mit der rechten Maustaste.

## <a name="support"></a>Support

Die ISE wurde erstmals mit Windows PowerShell V2 und erneut mit PowerShell V3 entwickelt wurde. Die ISE ist in allen unterstützten Versionen von Windows PowerShell bis zur und einschließlich Windows PowerShell 5.1 unterstützt. Die ISE ist jedoch im Maintennce Modus aus, und keine neuen Features sind wahrscheinlich hinzugefügt werden.
Darüber hinaus besteht keine Unterstützung für die ISE mit PowerShell IPv6 und darüber hinaus zur Verfügung. Benutzer möchte ein grafisches Tool zum Verwalten von PowerShell Scrips usw. sollten [Visual Studio Code](https://code.visualstudio.com/).

## <a name="key-features"></a>Hauptmerkmale

Wichtige Features in Windows PowerShell ISE sind:

- Mehrzeilige Bearbeitung: Zum Einfügen einer leeren Zeile unter der aktuellen Zeile im Befehlsbereich drücken Sie Umschalt + Eingabe.
- Selektive Ausführung: Um Teil eines Skripts auszuführen, wählen Sie den Text, die Sie ausführen möchten, und klicken Sie dann auf die **Skript ausführen** Schaltfläche. Oder drücken Sie F5.
- Kontextbezogene Hilfe: Typ **Invoke-Item**, und drücken Sie dann F1. Die Hilfedatei wird mit dem Artikel für das Cmdlet **Invoke-Item** geöffnet.

Die Windows PowerShell ISE ermöglicht Ihnen das Anpassen einiger Aspekte ihrer Darstellung. Sie enthält auch ein eigenes Windows PowerShell-Profilskript.

## <a name="to-start-the-windows-powershell-ise"></a>So starten Sie die Windows PowerShell ISE

Klicken Sie auf **Start**, wählen Sie **Windows PowerShell** aus, und klicken Sie dann auf **Windows PowerShell ISE**.
Alternativ können Sie `powershell_ise.exe` in eine Befehlsshell oder im Feld „Ausführen“ eingeben.

## <a name="to-get-help-in-the-windows-powershell-ise"></a>So rufen Sie Hilfe in der Windows PowerShell ISE ab

Klicken Sie im Menü **Hilfe** auf **Windows PowerShell-Hilfe**. Oder drücken Sie F1. Die Datei, die geöffnet wird, beschreibt die Windows PowerShell ISE und Windows PowerShell, einschließlich sämtlicher Hilfe, die über das Cmdlet „Get-Help“ verfügbar ist.
