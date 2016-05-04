---
title: Vorbereiten des Verwendens von WindowsPowerShell
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6dc7052d-cc5a-4220-950f-98f963a2b587
---
# Vorbereiten des Verwendens von WindowsPowerShell
Wenn [!INCLUDE[wps_2](../Token/wps_2_md.md)] installiert und gestartet wurde, sollten Sie die folgenden Setupoptionen berücksichtigen. Sie können diese Aufgaben zu einem beliebigen Zeitpunkt ausführen.

-   **Installieren von Hilfedateien.** Die Cmdlets, die in [!INCLUDE[psversion3](../Token/psversion3_md.md)] enthalten sind, werden zunächst ohne Hilfedateien bereitgestellt. Sie können aber das Cmdlet [Update-Help](https://technet.microsoft.com/en-us/library/93e1d870-ace6-432b-8778-8920291d7545) verwenden, um die neuesten Hilfedateien auf Ihren Computer herunterzuladen und zu installieren. Wenn diese Dateien installiert sind, können Sie das Cmdlet [Get-Help](https://technet.microsoft.com/en-us/library/1f46eeb4-49d7-4bec-bb29-395d9b42f54a) verwenden, um sie direkt über die Befehlszeile anzuzeigen. Weitere Informationen hierzu finden Sie unter [about_Updatable_Help](https://technet.microsoft.com/en-us/library/10bba75c-f4ac-4ca1-bbf3-8f34dd521ffe).

    Wenn Sie sich entscheiden, die Hilfedateien nicht zu installieren, können Sie die Hilfethemen weiterhin online lesen. Um die Onlineversion eines Cmdlet-Hilfethemas zu finden, geben Sie `Get-Help <CmdletName> -Online` ein. Wenn Sie die [!INCLUDE[wps_2](../Token/wps_2_md.md)]-Hilfethemen in der TechNet-Bibliothek durchsuchen möchten, beginnen Sie bei [http://go.microsoft.com/fwlink/?LinkID=107116](http://go.microsoft.com/fwlink/?LinkID=107116).

-   **Ausführen von Skripts.** Damit [!INCLUDE[mshshort](../Token/mshshort_md.md)] sicher bleibt, ist die Standardausführungsrichtlinie für [!INCLUDE[mshshort](../Token/mshshort_md.md)] gleich **Restricted**. Diese Richtlinie lässt das Ausführen von Cmdlets, aber nicht das Ausführen von Skripts zu. Wenn Sie Skripts ausführen möchten, verwenden Sie das Cmdlet [Set-ExecutionPolicy[PSITPro5_Security]](https://technet.microsoft.com/en-us/library/5690a0e1-495b-4e63-8280-65ead7bf01ab), um die Ausführungsrichtlinie in **AllSigned** oder **RemoteSigned** zu ändern. Dieses Cmdlet kann nur von Mitgliedern der Gruppe „Administratoren“ auf dem Computer ausgeführt werden. Weitere Informationen hierzu finden Sie unter [about_Execution_Policies [v4]](https://technet.microsoft.com/en-us/library/347708dc-1515-4d74-978b-8334603472e6).

-   **Aktivieren von Remoting.** Das System ist bereits so konfiguriert, dass es Remotebefehle auf anderen Computern ausführen kann. Unter [!INCLUDE[winblue_server_2](../Token/winblue_server_2_md.md)] und [!INCLUDE[win8_server_2](../Token/win8_server_2_md.md)] ist das System ebenfalls für das Empfangen von Remotebefehlen konfiguriert, d. h., es gestattet anderen Computern, Remotebefehle auf dem lokalen Computer auszuführen. Wenn Sie für einen Computer, auf dem eine andere Version von Windows ausgeführt wird, das Empfangen von Remotebefehlen ermöglichen möchten, führen Sie das Cmdlet [Enable-PSRemoting](https://technet.microsoft.com/en-us/library/19437c28-33b8-4ac1-9113-8439cc8beffb) auf diesem Computer aus. Dieses Cmdlet kann nur von Mitgliedern der Gruppe „Administratoren“ auf dem Computer ausgeführt werden. Weitere Informationen hierzu finden Sie unter [about_Remote](https://technet.microsoft.com/en-us/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970).

    HINWEIS: Ist Remoting auf einem Computer unter [!INCLUDE[psversion2](../Token/psversion2_md.md)] aktiviert, ist Remoting weiterhin aktiviert, nachdem Sie [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] installiert haben. Unter [!INCLUDE[lserver](../Token/lserver_md.md)] (nicht [!INCLUDE[win7_server_secondref](../Token/win7_server_secondref_md.md)]) müssen Sie Remoting nach der Installation von [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] aber erneut aktivieren.

## Weitere Informationen
[Installieren von Windows PowerShell](../Topic/Installing-Windows-PowerShell.md)
[Starten von Windows PowerShell [ps]](https://technet.microsoft.com/en-us/library/8ec8c2d7-8e7c-4722-a3d2-498fe5739a8e)



<!--HONumber=Apr16_HO2-->


