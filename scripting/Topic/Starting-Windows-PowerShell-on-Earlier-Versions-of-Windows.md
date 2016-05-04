---
title: Starten von Windows PowerShell unter früheren Versionen von Windows
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 57125436-3d1e-4e7f-b5c4-8f0ecb49d642
---
# Starten von Windows PowerShell unter früheren Versionen von Windows
In diesem Abschnitt wird erläutert, wie Sie [!INCLUDE[wps_2](../Token/wps_2_md.md)] und [!INCLUDE[mshgraphicalhost](../Token/mshgraphicalhost_md.md)] unter [!INCLUDE[win7_client_firstref](../Token/win7_client_firstref_md.md)], [!INCLUDE[win7_server_firstref](../Token/win7_server_firstref_md.md)] und [!INCLUDE[lserver](../Token/lserver_md.md)] starten. Außerdem wird erläutert, wie das optionale Feature für [!INCLUDE[mshgraphicalhostshort](../Token/mshgraphicalhostshort_md.md)] in [!INCLUDE[psversion2](../Token/psversion2_md.md)] unter [!INCLUDE[win7_server_firstref](../Token/win7_server_firstref_md.md)] und [!INCLUDE[lserver](../Token/lserver_md.md)] aktiviert wird.

Zum Installieren von [!INCLUDE[psversion4](../Token/psversion4_md.md)] auf unterstützten Systemen müssen Sie [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881) herunterladen und installieren. Weitere Informationen finden Sie unter [Installieren von Windows PowerShell](../Topic/Installing-Windows-PowerShell.md).

Zum Installieren von [!INCLUDE[psversion3](../Token/psversion3_md.md)] auf unterstützten Systemen müssen Sie [Windows Management Framework 3.0](http://go.microsoft.com/fwlink/?LinkID=240290) herunterladen und installieren. Weitere Informationen finden Sie unter [Installieren von Windows PowerShell](../Topic/Installing-Windows-PowerShell.md).

## Starten von [!INCLUDE[mshshort](../Token/mshshort_md.md)] unter früheren Versionen von Windows
Befolgen Sie eine der folgenden Methoden zum Starten der installierten Version von [!INCLUDE[psversion3](../Token/psversion3_md.md)], oder [!INCLUDE[psversion4](../Token/psversion4_md.md)], sofern zutreffend.

#### Über das Startmenü

-   Klicken Sie auf **Start**, geben Sie **PowerShell** ein, und klicken Sie dann auf **Windows PowerShell**.

-   Klicken Sie im Menü ** ****Start** auf **Alle Programme**, danach auf **Zubehör**, anschließend auf den Ordner **Windows PowerShell** und schließlich auf **Windows PowerShell**.

#### An der Eingabeaufforderung

-   Geben Sie in „Cmd.exe“, [!INCLUDE[wps_2](../Token/wps_2_md.md)] oder [!INCLUDE[wps_2](../Token/wps_2_md.md)] ISE zum Starten von [!INCLUDE[wps_2](../Token/wps_2_md.md)] Folgendes ein:

    ```
    PowerShell
    ```

    Sie können auch die Parameter des Programms „PowerShell.exe“ verwenden, um die Sitzung anzupassen. Weitere Informationen finden Sie unter [PowerShell.exe – Befehlszeilenhilfe](../Topic/PowerShell.exe-Command-Line-Help.md).

#### Mit administrativen Berechtigungen (Als Administrator ausführen)

1.  Klicken Sie auf **Start**, geben Sie **PowerShell** ein, klicken Sie mit der rechten Maustaste auf **Windows PowerShell**, und klicken Sie dann auf **Als Administrator ausführen**.

## Starten von [!INCLUDE[mshgraphicalhostshort](../Token/mshgraphicalhostshort_md.md)] unter früheren Versionen von Windows
Verwenden Sie eine der folgenden Methoden zum Starten von [!INCLUDE[mshgraphicalhostshort](../Token/mshgraphicalhostshort_md.md)].

#### Über das Startmenü

-   Klicken Sie auf **Start**, geben Sie **ISE** ein, und klicken Sie dann auf **Windows PowerShell ISE**.

-   Klicken Sie im Menü ** ****Start** auf **Alle Programme**, danach auf **Zubehör**, anschließend auf den Ordner **Windows PowerShell** und schließlich auf **Windows PowerShell ISE**.

#### An der Eingabeaufforderung

-   Geben Sie in „Cmd.exe“, [!INCLUDE[wps_2](../Token/wps_2_md.md)] oder [!INCLUDE[wps_2](../Token/wps_2_md.md)] ISE zum Starten von [!INCLUDE[wps_2](../Token/wps_2_md.md)] Folgendes ein:

    ```
    PowerShell_ISE
    ```

    oder

    ```
    ISE
    ```

#### Mit administrativen Berechtigungen (Als Administrator ausführen)

1.  Klicken Sie auf **Start**, geben Sie **ISE** ein, klicken Sie mit der rechten Maustaste auf **Windows PowerShell ISE**, und klicken Sie dann auf **Als Administrator ausführen**.

## Aktivieren von [!INCLUDE[mshgraphicalhostshort](../Token/mshgraphicalhostshort_md.md)] unter früheren Versionen von Windows
In [!INCLUDE[psversion4](../Token/psversion4_md.md)] und [!INCLUDE[psversion3](../Token/psversion3_md.md)] ist [!INCLUDE[mshgraphicalhostshort](../Token/mshgraphicalhostshort_md.md)] unter allen Versionen von Windows standardmäßig aktiviert. Falls nicht bereits aktiviert ist, erfolgt die Aktivierung mithilfe von Windows Management Framework 4.0 oder [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)].

In [!INCLUDE[psversion2](../Token/psversion2_md.md)] ist [!INCLUDE[mshgraphicalhostshort](../Token/mshgraphicalhostshort_md.md)] ist standardmäßig unter [!INCLUDE[win7_client_secondref](../Token/win7_client_secondref_md.md)] aktiviert. Unter [!INCLUDE[win7_server_secondref](../Token/win7_server_secondref_md.md)] und [!INCLUDE[lserver](../Token/lserver_md.md)] ist es allerdings ein optionales Feature.

Führen Sie die folgenden Schritte aus, um [!INCLUDE[mshgraphicalhostshort](../Token/mshgraphicalhostshort_md.md)] in [!INCLUDE[psversion2](../Token/psversion2_md.md)] unter [!INCLUDE[win7_server_secondref](../Token/win7_server_secondref_md.md)] und [!INCLUDE[lserver](../Token/lserver_md.md)] zu aktivieren.

#### So aktivieren Sie [!INCLUDE[mshgraphicalhost](../Token/mshgraphicalhost_md.md)]

1.  Starten Sie den Server-Manager.

2.  Klicken Sie auf **Features** und dann auf **Features hinzufügen**.

3.  Klicken Sie in „Features auswählen“ auf [!INCLUDE[mshgraphicalhost](../Token/mshgraphicalhost_md.md)].



<!--HONumber=Apr16_HO1-->


