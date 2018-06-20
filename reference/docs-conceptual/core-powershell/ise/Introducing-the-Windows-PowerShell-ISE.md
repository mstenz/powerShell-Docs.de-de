---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Einführung in die Windows PowerShell ISE
ms.openlocfilehash: b09e64d0258d11f1f16f96b319ef232ebdfa0c49
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
ms.locfileid: "30952901"
---
# <a name="introducing-the-windows-powershell-ise"></a>Einführung in die Windows PowerShell ISE

Windows PowerShell Integrated Scripting Environment (ISE) ist eine Hostanwendung für Windows PowerShell. In der Windows PowerShell ISE können Sie Befehle ausführen und Skripts schreiben, testen und debuggen, und zwar auf einer einzigen Windows-basierten grafischen Benutzeroberfläche mit mehrzeiliger Bearbeitung, Vervollständigung mit der TAB-TASTE, Syntaxfarben, selektiver Ausführung, kontextbezogener Hilfe und Unterstützung für von rechts nach links geschriebene Sprachen. Sie können Menüelemente und Tastenkombinationen für viele der Aufgaben nutzen, die Sie auch in der Windows PowerShell-Konsole ausführen würden. Um beispielsweise beim Debuggen eines Skripts in der Windows PowerShell ISE einen Zeilenhaltepunkt in einem Skript festzulegen, klicken Sie mit der rechten Maustaste auf die Codezeile, und klicken Sie anschließende auf **Haltepunkt umschalten**.

Testen Sie diese neuen Features in der Windows PowerShell ISE.

- Mehrzeilige Bearbeitung: Drücken Sie zum Einfügen einer leeren Zeile unter der aktuellen Zeile im Befehlsbereich UMSCHALT+EINGABETASTE.
- Selektive Ausführung: Um einen Teil eines Skripts auszuführen, markieren Sie den Text, den Sie ausführen möchten, und klicken Sie dann auf die Schaltfläche **Skript ausführen**. Oder drücken Sie F5.
- Kontextbezogene Hilfe: Geben Sie **Invoke-Item** ein, und drücken Sie dann F1. Die Hilfedatei wird mit dem Hilfethema für das Cmdlet **Invoke-Item** geöffnet.

Die Windows PowerShell ISE ermöglicht Ihnen das Anpassen einiger Aspekte ihrer Darstellung. Sie hat auch ein eigenes Windows PowerShell-Profil, in dem Sie Funktionen, Aliase, Variablen und Befehle speichern können, die Sie in der Windows PowerShell ISE verwenden.

## <a name="to-start-the-windows-powershell-ise"></a>So starten Sie die Windows PowerShell ISE

Führen Sie eines der folgenden Verfahren aus:

- Klicken Sie auf **Start**, zeigen Sie auf **Alle Programme**, dann auf **Windows PowerShell 2.0**, und klicken Sie dann auf **Windows PowerShell ISE**.
- Geben Sie in der Windows PowerShell-Konsole „Cmd.exe“ oder im Feld „Ausführen“ **powershell_ise.exe** ein.

## <a name="to-get-help-in-the-windows-powershell-ise"></a>So rufen Sie Hilfe in der Windows PowerShell ISE ab

Klicken Sie im Menü **Hilfe** auf **Windows PowerShell-Hilfe**. Oder drücken Sie F1. Die Datei, die geöffnet wird, beschreibt die Windows PowerShell ISE und Windows PowerShell, einschließlich sämtlicher Hilfe, die über das Cmdlet „Get-Help“ verfügbar ist.