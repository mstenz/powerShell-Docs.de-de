---
title: Erstellen einer PowerShell-Registerkarte in Windows PowerShell ISE
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c10c18c7-9ece-4fd0-83dc-a19c53d4fd83
---
# Erstellen einer PowerShell-Registerkarte in Windows PowerShell ISE
Registerkarten in der [!INCLUDE[ise_1](../Token/ise_1_md.md)] ermöglichen Ihnen, mehrere Ausführungsumgebungen innerhalb derselben Anwendung gleichzeitig zu erstellen und verwenden. Jede PowerShell-Registerkarte entspricht einer separaten Ausführungsumgebung bzw. Sitzung.

> [!NOTE]
> Variablen, Funktionen und Aliase, die Sie auf einer Registerkarte erstellen, werden nicht auf andere übertragen. Sie sind in verschiedenen Windows PowerShell-Sitzungen enthalten.

Gehen Sie folgendermaßen vor, um eine Registerkarte in [!INCLUDE[wps_2](../Token/wps_2_md.md)] zu öffnen oder schließen. Legen Sie zum Umbenennen einer Registerkarte die [DisplayName](assetId:///a9b58556-951b-4f48-b3ae-b351b7564360#Displayname)-Eigenschaft im [!INCLUDE[wps_2](../Token/wps_2_md.md)]-Skriptobjekt „Tab“ fest.

## So erstellen und verwenden Sie eine neue PowerShell-Registerkarte
Klicken Sie im Menü **Datei** auf **Neue PowerShell-Registerkarte**. Die neue PowerShell-Registerkarte wird immer als aktives Fenster geöffnet. PowerShell-Registerkarten sind in der Reihenfolge ihres Öffnens aufsteigend nummeriert. Jede Registerkarte ist einem eigenen Windows PowerShell-Konsolenfenster zugeordnet. Sie können bis zu 32 PowerShell-Registerkarten mit jeweils eigener Sitzung gleichzeitig geöffnet haben (bei [!INCLUDE[ise_2](../Token/ise_2_md.md)] 2.0 maximal 8.)

Beachten Sie, dass durch Klicken auf die Symbole **Neu** oder **Öffnen** auf der Symbolleiste keine neue Registerkarte mit einer separaten Sitzung erstellt wird.  Über diese Schaltflächen wird stattdessen eine neue oder vorhandene Skriptdatei auf der derzeit in einer Sitzung aktiven Registerkarte geöffnet. Auf jeder Registerkarte und in jeder Sitzung können mehrere Skriptdateien geöffnet sein. Die Skriptregisterkarten für eine Sitzung werden nur unter den Sitzungsregisterkarten angezeigt, wenn die zugehörige Sitzung aktiv ist.

Um eine PowerShell-Registerkarte zu aktivieren, klicken Sie auf die Registerkarte. Zum Auswählen aller PowerShell-Registerkarten, die im Menü **Ansicht** geöffnet sind, klicken Sie auf die PowerShell-Registerkarte, die Sie verwenden möchten.

## So erstellen und verwenden Sie eine Remote-PowerShell-Registerkarte
Klicken Sie im Menü **Datei** auf **Neue Remote-PowerShell-Registerkarte**, um eine Sitzung auf einem Remotecomputer zu starten. Ein Dialogfeld wird angezeigt und fordert Sie zur Eingabe von Details auf, die zum Herstellen der Remoteverbindung erforderlich sind. Die Remoteregisterkarte funktioniert wie eine lokale PowerShell-Registerkarte, doch die Befehle und Skripts werden auf dem Remotecomputer ausgeführt.

## So schließen Sie eine PowerShell-Registerkarte
Zum Schließen einer Registerkarte können Sie eine der folgenden Methoden verwenden:

-   Klicken Sie auf die Registerkarte, die Sie schließen möchten.

-   Klicken Sie im Menü **Datei** auf **PowerShell-Registerkarte schließen**, oder klicken Sie auf einer aktiven Registerkarte auf die Schaltfläche „Schließen“ (**X**), um sie zu schließen.

Wenn Sie auf der PowerShell-Registerkarte nicht gespeicherte Dateien geöffnet sind, werden Sie aufgefordert, sie zu speichern oder zu verwerfen. Weitere Informationen zum Speichern eines Skripts finden Sie unter [Speichern eines Skripts](assetId:///162f594d-efd3-4234-9960-45e56e6eadc8).

## Weitere Informationen
[Verwenden der Windows PowerShell ISE](../Topic/Using-the-Windows-PowerShell-ISE.md)
[Verwenden des Konsolenbereichs in der Windows PowerShell ISE](../Topic/How-to-Use-the-Console-Pane-in-the-Windows-PowerShell-ISE.md)



<!--HONumber=Apr16_HO1-->


