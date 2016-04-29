---
title: Installieren von Windows PowerShell
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6fbb0409-5a54-48ec-95e6-7f8b7d8c4969
---
# Installieren von Windows PowerShell
[!INCLUDE[win8_client_1](../Token/win8_client_1_md.md)] und [!INCLUDE[win8_server_1](../Token/win8_server_1_md.md)] enthalten [!INCLUDE[psversion3](../Token/psversion3_md.md)] und alle erforderlichen Komponenten. Das System enthält auch das [!INCLUDE[psversion2](../Token/psversion2_md.md)]-Modul für Abwärtskompatibilität mit Hostprogrammen, die [!INCLUDE[psversion3](../Token/psversion3_md.md)] nicht verwenden können.

In diesem Thema wird erläutert, wie Sie [!INCLUDE[psversion3](../Token/psversion3_md.md)] auf älteren Systemen installieren und die erforderlichen Features aktivieren.

Dieses Thema enthält die folgenden Abschnitte:

-   [Installieren von Windows PowerShell unter Windows 8 und Windows Server 2012](../Topic/Installing-Windows-PowerShell.md#BKMK_InstallingOnWindows8andWindowsServer2012)

-   [Installieren von Windows PowerShell unter Windows 7 und Windows Server 2008 R2](../Topic/Installing-Windows-PowerShell.md#BKMK_InstallingOnWindows7andWindowsServer2008R2)

-   [Installieren von Windows PowerShell unter Windows Server 2008](../Topic/Installing-Windows-PowerShell.md#BKMK_InstallingOnWindowsServer2008LH)

-   [Installieren von Windows PowerShell unter Server Core](../Topic/Installing-Windows-PowerShell.md#BKMK_InstallingOnServerCore)

-   [Bereitstellen von Windows PowerShell Web Access](assetId:///639d0eff-98a3-4124-b52c-26921ebd98b0)

-   [Installieren des Windows PowerShell 2.0-Moduls](../Topic/Installing-the-Windows-PowerShell-2.0-Engine.md)

## <a name="BKMK_InstallingOnWindows8andWindowsServer2012"></a>Installieren von Windows PowerShell unter Windows 8 und Windows Server 2012
[!INCLUDE[psversion3](../Token/psversion3_md.md)] ist installiert, konfiguriert und einsatzbereit. [!INCLUDE[mshgraphicalhost](../Token/mshgraphicalhost_md.md)] ist installiert und aktiviert. Weitere Informationen zum Starten von [!INCLUDE[mshshort](../Token/mshshort_md.md)] finden Sie unter [Starten von Windows PowerShell unter Windows 8](assetId:///d7be1668-8617-4890-ad90-dd9765fbd2c3) und [Starten von Windows PowerShell unter Windows Server 2012](assetId:///4fc0110a-cc0c-42a4-bbb5-3cc89a0fc968).

## <a name="BKMK_InstallingOnWindows7andWindowsServer2008R2"></a>Installieren von Windows PowerShell unter Windows 7 und Windows Server 2008 R2
Diese Anleitung erläutert die Installation von [!INCLUDE[psversion3](../Token/psversion3_md.md)] auf Computern mit [!INCLUDE[win7_client_secondref](../Token/win7_client_secondref_md.md)] mit Service Pack 1 und [!INCLUDE[win7_server_secondref](../Token/win7_server_secondref_md.md)] mit Service Pack 1. Für Computer mit der Installationsoption Server Core von [!INCLUDE[win7_server_secondref](../Token/win7_server_secondref_md.md)] finden Sie nachstehend gesonderte Installationsanweisungen.

#### Vorbereiten der Installation

-   Deinstallieren Sie vor der Installation von [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] alle früheren Versionen von Windows Management Framework 3.0.

#### So installieren Sie [!INCLUDE[psversion3](../Token/psversion3_md.md)]

1.  Installieren Sie die vollständige Installation von Microsoft .NET Framework 4 (dotNetFx40_Full_setup.exe), die Sie im Microsoft Download Center unter [http://go.microsoft.com/fwlink/?LinkID=212547](http://go.microsoft.com/fwlink/?LinkID=212547) finden.

    Oder installieren Sie Microsoft .NET Framework 4.5 (dotNetFx45_Full_setup.exe), das Sie im Microsoft Download Center unter [http://go.microsoft.com/fwlink/?LinkID=242919](http://go.microsoft.com/fwlink/?LinkID=242919) finden.

2.  Installieren Sie [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] aus dem Microsoft Download Center unter [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290).

Weitere Informationen zum Starten von [!INCLUDE[psversion3](../Token/psversion3_md.md)] finden Sie unter [Starten von Windows PowerShell unter früheren Versionen von Windows](../Topic/Starting-Windows-PowerShell-on-Earlier-Versions-of-Windows.md).

## <a name="BKMK_InstallingOnServerCore"></a>Installieren von Windows PowerShell unter Server Core
Diese Anleitungen erläutern die Installation von [!INCLUDE[psversion3](../Token/psversion3_md.md)] auf Computern mit der Installationsoption Server Core von [!INCLUDE[win7_server_secondref](../Token/win7_server_secondref_md.md)] mit Service Pack 1.

In den ersten Schritten des Verfahrens werden DISM-Befehle (Deployment Image Servicing and Management, Abbildverwaltung für die Bereitstellung) zum Installieren von Microsoft [!INCLUDE[dnprdnlong](../Token/dnprdnlong_md.md)] für Server Core und [!INCLUDE[psversion2](../Token/psversion2_md.md)] verwendet. Diese Programme sind Voraussetzungen für [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)], das in einem späteren Schritt installiert wird.

#### Vorbereiten der Installation

-   Deinstallieren Sie vor der Installation von [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] alle früheren Versionen von Windows Management Framework 3.0.

#### So installieren Sie [!INCLUDE[psversion3](../Token/psversion3_md.md)]

1.  Starten Sie „Cmd.exe“.

2.  Führen Sie die folgenden DISM-Befehle aus. Diese Befehle installieren [!INCLUDE[dnprdnlong](../Token/dnprdnlong_md.md)] und [!INCLUDE[psversion2](../Token/psversion2_md.md)].

    ```
    dism /online /enable-feature:NetFx2-ServerCore
    dism /online /enable-feature:MicrosoftWindowsPowerShell
    dism /online /enable-feature:NetFx2-ServerCore-WOW64
    ```

3.  Installieren Sie die vollständige Installation von Microsoft [!INCLUDE[netfx40_short](../Token/netfx40_short_md.md)] für Server Core, die Sie im Microsoft Download Center unter [http://go.microsoft.com/fwlink/?LinkID=248450](http://go.microsoft.com/fwlink/?LinkID=248450) finden.

4.  Installieren Sie [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] aus dem Microsoft Download Center unter [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290).

## <a name="BKMK_InstallingOnWindowsServer2008LH"></a>Installieren von Windows PowerShell unter Windows Server 2008
Diese Anleitungen erläutern die Installation von [!INCLUDE[psversion3](../Token/psversion3_md.md)] auf Computern mit [!INCLUDE[lserver](../Token/lserver_md.md)] mit Service Pack 2.

Auf [!INCLUDE[lserver](../Token/lserver_md.md)]-Systemen ist Windows Management Framework ([!INCLUDE[psversion2](../Token/psversion2_md.md)], 968930 KB) eine Voraussetzung für [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)]. Das Feature „Erweiterter Schutz für Authentifizierung“ schützt den Computer vor Angriffen mittels Weiterleitung der Authentifizierung und ermöglicht beim Starten von Remotesitzungen die Verwendung des **UseSSL**-Parameters. Befolgen Sie das folgende Verfahren zum Installieren von [!INCLUDE[psversion3](../Token/psversion3_md.md)] und des [!INCLUDE[psversion2](../Token/psversion2_md.md)]-Moduls.

#### Vorbereiten der Installation

-   Deinstallieren Sie vor der Installation von [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] alle früheren Versionen von Windows Management Framework 3.0.

#### So installieren Sie [!INCLUDE[psversion3](../Token/psversion3_md.md)]

1.  Installieren Sie Microsoft .NET Framework 3.5 mit Service Pack 1, das Sie im Microsoft Download Center unter [http://go.microsoft.com/fwlink/?LinkID=242910](http://go.microsoft.com/fwlink/?LinkID=242910) finden.

2.  Installieren Sie Windows Management Framework ([!INCLUDE[psversion2](../Token/psversion2_md.md)], KB 968930) aus dem Microsoft Download Center unter [http://go.microsoft.com/fwlink/?LinkID=243035](http://go.microsoft.com/fwlink/?LinkId=243035).

3.  Installieren Sie die vollständige Installation von Microsoft .NET Framework 4 (dotNetFx40_Full_setup.exe), die Sie im Microsoft Download Center unter [http://go.microsoft.com/fwlink/?LinkID=212547](http://go.microsoft.com/fwlink/?LinkID=212547) finden.

    Oder installieren Sie Microsoft .NET Framework 4.5 (dotNetFx45_Full_setup.exe), das Sie im Microsoft Download Center unter [http://go.microsoft.com/fwlink/?LinkID=242919](http://go.microsoft.com/fwlink/?LinkID=242919) finden.

4.  Installieren Sie „Erweiterter Schutz für Authentifizierung“ (KB 968389) unter [http://go.microsoft.com/fwlink/?LinkID=186398](http://go.microsoft.com/fwlink/?LinkID=186398).

5.  Installieren Sie [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] aus dem Microsoft Download Center unter [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290).

## Weitere Informationen
[Windows PowerShell-Systemanforderungen](../Topic/Windows-PowerShell-System-Requirements.md)
[Starten von Windows PowerShell [ps]](assetId:///8ec8c2d7-8e7c-4722-a3d2-498fe5739a8e)



<!--HONumber=Apr16_HO1-->


