---
title: Installieren des Windows PowerShell 2.0-Moduls
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 82928f2b-f96a-4ae6-a0d0-6e7b181da308
---
# Installieren des Windows PowerShell 2.0-Moduls
In diesem Thema wird erläutert, wie Sie das [!INCLUDE[psversion2](../Token/psversion2_md.md)]-Modul installieren.

[!INCLUDE[psversion3](../Token/psversion3_md.md)] ist mit [!INCLUDE[psversion2](../Token/psversion2_md.md)] abwärtskompatibel. Cmdlets, Anbieter, Snap-Ins, Module und Skripts, die für [!INCLUDE[psversion2](../Token/psversion2_md.md)] geschrieben wurden, können in [!INCLUDE[psversion3](../Token/psversion3_md.md)] und [!INCLUDE[psversion4](../Token/psversion4_md.md)] unverändert ausgeführt werden. Doch aufgrund einer Änderung der Richtlinie für die Laufzeitaktivierung in Microsoft .NET Framework 4 können Windows PowerShell-Hostprogramme, die für [!INCLUDE[psversion2](../Token/psversion2_md.md)] geschrieben und mit Common Language Runtime (CLR) 2.0 kompiliert wurden, nicht unverändert in späteren Versionen von [!INCLUDE[wps_2](../Token/wps_2_md.md)] ausgeführt werden, die mit CLR 4.0 kompiliert wurden.

Um die Abwärtskompatibilität mit Befehlen und Hostprogrammen zu erhalten, die von diesen Änderungen betroffen sind, können die [!INCLUDE[psversion2](../Token/psversion2_md.md)]-, [!INCLUDE[psversion3](../Token/psversion3_md.md)]- und [!INCLUDE[psversion4](../Token/psversion4_md.md)]-Module parallel ausgeführt werden. Das [!INCLUDE[psversion2](../Token/psversion2_md.md)]-Modul ist außerdem in [!INCLUDE[winblue_server_2](../Token/winblue_server_2_md.md)], [!INCLUDE[winblue_client_2](../Token/winblue_client_2_md.md)], [!INCLUDE[win8_client_2](../Token/win8_client_2_md.md)], [!INCLUDE[win8_server_2](../Token/win8_server_2_md.md)] und [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] enthalten. Das [!INCLUDE[psversion2](../Token/psversion2_md.md)]-Modul soll ausschließlich verwendet werden, wenn ein vorhandenes Skript oder Hostprogramm nicht ausgeführt werden kann, da es nicht mit [!INCLUDE[psversion3](../Token/psversion3_md.md)], [!INCLUDE[psversion4](../Token/psversion4_md.md)] oder Microsoft .NET Framework 4 kompatibel ist. Solche Fälle sind allerdings eher selten.

Das [!INCLUDE[psversion2](../Token/psversion2_md.md)]-Modul ist ein optionales Feature von [!INCLUDE[winblue_server_2](../Token/winblue_server_2_md.md)], [!INCLUDE[winblue_client_2](../Token/winblue_client_2_md.md)], [!INCLUDE[win8_client_1](../Token/win8_client_1_md.md)] und [!INCLUDE[win8_server_1](../Token/win8_server_1_md.md)]. Wenn Sie unter früheren Versionen von Windows [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] installieren, ersetzt die [!INCLUDE[psversion3](../Token/psversion3_md.md)]-Installation vollständig die [!INCLUDE[psversion2](../Token/psversion2_md.md)]-Installation im [!INCLUDE[wps_2](../Token/wps_2_md.md)]-Installationsverzeichnis. Das [!INCLUDE[psversion2](../Token/psversion2_md.md)]-Modul wird allerdings beibehalten.

Informationen zum Starten des [!INCLUDE[psversion2](../Token/psversion2_md.md)]-Moduls finden Sie unter [Starten des Windows PowerShell 2.0-Moduls](../Topic/Starting-the-Windows-PowerShell-2.0-Engine.md).

## Unter [!INCLUDE[winblue_client_2](../Token/winblue_client_2_md.md)] und [!INCLUDE[win8_client_2](../Token/win8_client_2_md.md)]
Unter [!INCLUDE[winblue_client_2](../Token/winblue_client_2_md.md)] und [!INCLUDE[win8_client_2](../Token/win8_client_2_md.md)] ist das Feature „[!INCLUDE[psversion2](../Token/psversion2_md.md)]-Modul“ standardmäßig aktiviert. Um es verwenden zu können, müssen Sie jedoch die Option für Microsoft .NET Framework 3.5 aktivieren, das erforderlich ist. In diesem Abschnitt wird auch erläutert, wie das Feature „[!INCLUDE[psversion2](../Token/psversion2_md.md)]-Modul“ aktiviert und deaktiviert wird.

#### So aktivieren Sie .NET Framework 3.5

1.  Geben Sie **Windows-Features** auf dem** **Startbildschirm ein.

2.  Klicken Sie auf der Leiste **Apps** auf **Einstellungen**, und klicken Sie dann auf **Windows-Features aktivieren oder deaktivieren**.

3.  Klicken Sie im Feld **Windows-Features** auf **.NET Framework 3.5 (enthält .NET 2.0 und 3.0)**, um es auszuwählen.

    Wenn Sie die Option **NET Framework 3.5 (enthält .NET 2.0 und 3.0)** auswählen, wird das Feld aufgefüllt, um anzugeben, dass nur ein Teil des Features ausgewählt ist. Dies ist jedoch für das [!INCLUDE[psversion2](../Token/psversion2_md.md)]-Modul ausreichend.

#### So aktivieren bzw. deaktivieren Sie das [!INCLUDE[psversion2](../Token/psversion2_md.md)]-Modul

1.  Geben Sie **Windows-Features** auf dem** **Startbildschirm ein.

2.  Klicken Sie auf der Leiste **Apps** auf **Einstellungen**, und klicken Sie dann auf **Windows-Features aktivieren oder deaktivieren**.

3.  Erweitern Sie im Feld **Windows-Features** den Knoten **[!INCLUDE[psversion2](../Token/psversion2_md.md)]**, und klicken Sie auf das Feld **[!INCLUDE[psversion2](../Token/psversion2_md.md)]-Modul**, um es zu aktivieren oder zu deaktivieren.

## Unter [!INCLUDE[winblue_server_2](../Token/winblue_server_2_md.md)] und [!INCLUDE[win8_server_2](../Token/win8_server_2_md.md)]
Mithilfe der folgenden Verfahren können Sie das [!INCLUDE[psversion2](../Token/psversion2_md.md)]-Modul und Microsoft .NET Framework 3.5-Features hinzufügen. Das [!INCLUDE[psversion2](../Token/psversion2_md.md)]-Modul erfordert mindestens Microsoft .NET Framework 2.0.50727. Diese Anforderung wird durch Microsoft .NET Framework 3.5 erfüllt.

#### So fügen Sie das Feature „.NET Framework 3.5“ hinzu

1.  Klicken Sie im **Server-Manager** im Menü **Verwalten** auf **Rollen und Features hinzufügen**.

    Oder klicken Sie im **Server-Manager** auf **Alle Server**, klicken Sie mit der rechten Maustaste auf einen Servernamen, und wählen Sie dann **Rollen und Features hinzufügen** aus.

2.  Wählen Sie auf der Seite **Installationstyp auswählen** die Option **Rollenbasierte oder featurebasierte Installation** aus.

3.  Klappen Sie auf der Seite **Features** den Knoten **Features von .NET Framework 3.5** auf, und wählen **NET Framework 3.5 (enthält .NET 2.0 und 3.0)** aus.

    Die anderen Optionen unter diesem Knoten sind für das [!INCLUDE[psversion2](../Token/psversion2_md.md)]-Modul nicht erforderlich.

#### So fügen Sie das Feature „[!INCLUDE[psversion2](../Token/psversion2_md.md)]-Modul“ hinzu

-   Klicken Sie im **Server-Manager** im Menü **Verwalten** auf **Rollen und Features hinzufügen**.

    Oder klicken Sie im **Server-Manager** auf **Alle Server**, klicken Sie mit der rechten Maustaste auf einen Servernamen, und wählen Sie dann **Rollen und Features hinzufügen** aus.

-   Wählen Sie auf der Seite **Installationstyp auswählen** die Option **Rollenbasierte oder featurebasierte Installation** aus.

-   Klappen Sie auf der Seite **Features** den Knoten **[!INCLUDE[mshshort](../Token/mshshort_md.md)] (installiert)** auf, und wählen Sie **[!INCLUDE[psversion2](../Token/psversion2_md.md)]-Modul** aus.

Informationen zum Starten des [!INCLUDE[psversion2](../Token/psversion2_md.md)]-Moduls finden Sie unter [Starten des Windows PowerShell 2.0-Moduls](../Topic/Starting-the-Windows-PowerShell-2.0-Engine.md).

## Auf älteren Systemen
Das [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881)-Paket, das [!INCLUDE[psversion4](../Token/psversion4_md.md)] unter [!INCLUDE[win7_client_secondref](../Token/win7_client_secondref_md.md)], [!INCLUDE[win7_server_secondref](../Token/win7_server_secondref_md.md)] und [!INCLUDE[win8_server_2](../Token/win8_server_2_md.md)] installiert, enthält das [!INCLUDE[psversion2](../Token/psversion2_md.md)]-Modul. Das [!INCLUDE[psversion2](../Token/psversion2_md.md)]-Modul ist aktiviert und einsatzbereit, falls erforderlich, ohne zusätzliche Installation, Einrichtung und Konfiguration.

Das [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)]-Paket, das [!INCLUDE[psversion3](../Token/psversion3_md.md)] unter [!INCLUDE[win7_client_secondref](../Token/win7_client_secondref_md.md)], [!INCLUDE[win7_server_secondref](../Token/win7_server_secondref_md.md)] und [!INCLUDE[lserver](../Token/lserver_md.md)] installiert, enthält das [!INCLUDE[psversion2](../Token/psversion2_md.md)]-Modul. Das [!INCLUDE[psversion2](../Token/psversion2_md.md)]-Modul ist aktiviert und einsatzbereit, falls erforderlich, ohne zusätzliche Installation, Einrichtung und Konfiguration.

## Weitere Informationen
[Windows PowerShell-Systemanforderungen](../Topic/Windows-PowerShell-System-Requirements.md)
[Installieren von Windows PowerShell](../Topic/Installing-Windows-PowerShell.md)
[Starten von Windows PowerShell [ps]](assetId:///8ec8c2d7-8e7c-4722-a3d2-498fe5739a8e)
[Starten des Windows PowerShell 2.0-Moduls](../Topic/Starting-the-Windows-PowerShell-2.0-Engine.md)



<!--HONumber=Apr16_HO1-->


