---
title: Windows PowerShell-Systemanforderungen
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6d1d3c75-3be4-4fc9-8805-ca9b2c454d42
---
# Windows PowerShell-Systemanforderungen
In diesem Thema werden die Systemanforderungen für [!INCLUDE[psversion3](../Token/psversion3_md.md)] und [!INCLUDE[psversion4](../Token/psversion4_md.md)] sowie für spezielle Features vorgestellt, wie z. B. [!INCLUDE[mshgraphicalhost](../Token/mshgraphicalhost_md.md)], CIM-Befehle und Workflows.

[!INCLUDE[winblue_client_1](../Token/winblue_client_1_md.md)] und [!INCLUDE[winblue_server_1](../Token/winblue_server_1_md.md)] enthalten alle erforderlichen Programme. Dieses Thema ist für Benutzer früherer Versionen von Windows gedacht.

## Betriebssystemanforderungen
[!INCLUDE[psversion4](../Token/psversion4_md.md)] wird unter den folgenden Versionen von Windows ausgeführt.

-   [!INCLUDE[winblue_client_2](../Token/winblue_client_2_md.md)], standardmäßig installiert

-   [!INCLUDE[winblue_server_2](../Token/winblue_server_2_md.md)], standardmäßig installiert

-   [!INCLUDE[win7_client_firstref](../Token/win7_client_firstref_md.md)] mit Service Pack 1, [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkId=293881) zum Ausführen von [!INCLUDE[psversion4](../Token/psversion4_md.md)] installieren

-   [!INCLUDE[win7_server_firstref](../Token/win7_server_firstref_md.md)] mit Service Pack 1, [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkId=293881) zum Ausführen von [!INCLUDE[psversion4](../Token/psversion4_md.md)] installieren

[!INCLUDE[psversion3](../Token/psversion3_md.md)] wird unter den folgenden Versionen von Windows ausgeführt.

-   [!INCLUDE[win8_client_2](../Token/win8_client_2_md.md)], standardmäßig installiert

-   [!INCLUDE[win8_server_2](../Token/win8_server_2_md.md)], standardmäßig installiert

-   [!INCLUDE[win7_client_firstref](../Token/win7_client_firstref_md.md)] mit Service Pack 1, [Windows Management Framework 3.0](http://www.microsoft.com/download/details.aspx?id=34595) zum Ausführen von [!INCLUDE[psversion3](../Token/psversion3_md.md)] installieren

-   [!INCLUDE[win7_server_firstref](../Token/win7_server_firstref_md.md)] mit Service Pack 1, [Windows Management Framework 3.0](http://www.microsoft.com/download/details.aspx?id=34595) zum Ausführen von [!INCLUDE[psversion3](../Token/psversion3_md.md)] installieren

-   [!INCLUDE[lserver](../Token/lserver_md.md)] mit Service Pack 2, [Windows Management Framework 3.0](http://www.microsoft.com/download/details.aspx?id=34595) zum Ausführen von [!INCLUDE[psversion3](../Token/psversion3_md.md)] installieren

## Microsoft .NET Framework-Anforderungen
[!INCLUDE[psversion4](../Token/psversion4_md.md)] erfordert die vollständige Installation von Microsoft .NET Framework 4.5. [!INCLUDE[winblue_client_2](../Token/winblue_client_2_md.md)] und [!INCLUDE[winblue_server_2](../Token/winblue_server_2_md.md)] sind in Microsoft .NET Framework 4.5 standardmäßig enthalten.

[!INCLUDE[psversion3](../Token/psversion3_md.md)] erfordert die vollständige Installation von Microsoft .NET Framework 4. In [!INCLUDE[win8_client_2](../Token/win8_client_2_md.md)] und [!INCLUDE[win8_server_2](../Token/win8_server_2_md.md)] ist Microsoft .NET Framework 4.5 standardmäßig enthalten, wodurch diese Anforderung erfüllt ist.

Informationen zum Installieren von Microsoft .NET Framework 4.5 (dotNetFx45_Full_setup.exe) finden Sie im Microsoft Download Center unter [Microsoft .NET Framework 4.5](http://go.microsoft.com/fwlink/?LinkID=242919).

Informationen zur vollständigen Installation von Microsoft .NET Framework 4 (dotNetFx40_Full_setup.exe) finden Sie im Microsoft Download Center unter [Microsoft .NET Framework 4](http://go.microsoft.com/fwlink/?LinkID=212931).

## WS-Management 3.0
[!INCLUDE[psversion3](../Token/psversion3_md.md)] und [!INCLUDE[psversion4](../Token/psversion4_md.md)] erfordern WS-Management-3.0, das den WinRM-Dienst und das WSMan-Protokoll unterstützt. Dieses Programm ist in [!INCLUDE[winblue_client_2](../Token/winblue_client_2_md.md)], [!INCLUDE[winblue_server_2](../Token/winblue_server_2_md.md)], [!INCLUDE[win8_client_2](../Token/win8_client_2_md.md)], [!INCLUDE[win8_server_2](../Token/win8_server_2_md.md)], Windows Management Framework 4.0 und [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] enthalten.

## Windows-Verwaltungsinstrumentation 3.0 (Windows Management Instrumentation, WMI)
[!INCLUDE[psversion3](../Token/psversion3_md.md)] und [!INCLUDE[psversion4](../Token/psversion4_md.md)] erfordern Windows-Verwaltungsinstrumentation 3.0 (WMI). Dieses Programm ist in [!INCLUDE[winblue_client_2](../Token/winblue_client_2_md.md)], [!INCLUDE[winblue_server_2](../Token/winblue_server_2_md.md)], [!INCLUDE[win8_client_2](../Token/win8_client_2_md.md)], [!INCLUDE[win8_server_2](../Token/win8_server_2_md.md)], Windows Management Framework 4.0 und [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] enthalten. Wenn dieses Programm nicht auf dem Computer installiert ist, werden Features, die WMI erfordern, wie z. B. CIM-Befehle, nicht ausgeführt.

## Common Language Runtime 4.0
[!INCLUDE[psversion3](../Token/psversion3_md.md)] und [!INCLUDE[psversion4](../Token/psversion4_md.md)] werden für Common Language Runtime (CLR) 4.0 kompiliert.

## Anforderungen an die grafische Benutzeroberfläche
[!INCLUDE[wps_2](../Token/wps_2_md.md)] ist eine konsolenbasierte Anwendung, die keine grafische Benutzeroberfläche erfordert. Deshalb eignet sie sich gut für Computer ohne Bildschirm oder Monitor bzw. ohne Benutzeroberfläche, wie z. B. die Server Core-Installationsoptionen von [!INCLUDE[winblue_server_2](../Token/winblue_server_2_md.md)] oder [!INCLUDE[win8_server_2](../Token/win8_server_2_md.md)].

Allerdings erfordern einige Elemente, wie z. B. die folgenden, eine grafische Benutzeroberfläche. Weitere Informationen finden Sie im Hilfethema des jeweiligen Elements.

-   [!INCLUDE[mshgraphicalhost](../Token/mshgraphicalhost_md.md)]

-   Cmdlets

    1.  [Out-GridView](https://technet.microsoft.com/en-us/library/70915a86-d753-464e-8349-cba02316154c)

    2.  [Show-Command](https://technet.microsoft.com/en-us/library/65bba50b-91a8-49d5-80a2-a30fc684ba41)

    3.  [Show-ControlPanelItem](https://technet.microsoft.com/en-us/library/0685d42c-37cc-498f-acf6-0ecfeb0cb162)

    4.  [Show-EventLog](https://technet.microsoft.com/en-us/library/a3b0f5ad-0438-42c7-915b-d1b4793a431c)

-   Parameter

    1.  **ShowWindow**-Parameter des Cmdlets [Get-Help](https://technet.microsoft.com/en-us/library/1f46eeb4-49d7-4bec-bb29-395d9b42f54a).

    2.  **ShowSecurityDescriptorUi**-Parameter der Cmdlets [Register-PSSessionConfiguration](https://technet.microsoft.com/en-us/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) und [Set-PSSessionConfiguration](https://technet.microsoft.com/en-us/library/b21fbad3-1759-4260-b206-dcb8431cd6ea).

## Anforderungen an das Windows PowerShell-Modul
[!INCLUDE[psversion4](../Token/psversion4_md.md)] ist mit [!INCLUDE[psversion3](../Token/psversion3_md.md)] und [!INCLUDE[psversion2](../Token/psversion2_md.md)] abwärtskompatibel. Cmdlets, Anbieter, Snap-Ins, Module und Skripts, die für [!INCLUDE[psversion2](../Token/psversion2_md.md)] und [!INCLUDE[psversion3](../Token/psversion3_md.md)] geschrieben wurden, können in [!INCLUDE[psversion4](../Token/psversion4_md.md)] unverändert ausgeführt werden.

Doch aufgrund einer Änderung der Richtlinie für die Laufzeitaktivierung in Microsoft .NET Framework 4 können [!INCLUDE[wps_2](../Token/wps_2_md.md)]-Hostprogramme, die für [!INCLUDE[psversion2](../Token/psversion2_md.md)] geschrieben und mit Common Language Runtime (CLR) 2.0 kompiliert wurden, nicht in [!INCLUDE[psversion3](../Token/psversion3_md.md)] ausgeführt werden, das mit CLR 4.0 kompiliert wurde.

Das [!INCLUDE[psversion2](../Token/psversion2_md.md)]-Modul erfordert mindestens Microsoft .NET Framework 2.0.50727. Diese Anforderung wird durch Microsoft .NET Framework 3.5 Service Pack 1 erfüllt. Diese Anforderung wird nicht durch Microsoft .NET Framework 4 und höhere Versionen von Microsoft .NET Framework erfüllt.

Informationen zum Hinzufügen oder Installieren des [!INCLUDE[psversion2](../Token/psversion2_md.md)]-Moduls sowie zum Hinzufügen oder Installieren der erforderlichen Versionen von Microsoft .NET Framework finden Sie unter [Installieren des Windows PowerShell 2.0-Moduls](../Topic/Installing-the-Windows-PowerShell-2.0-Engine.md). Informationen zum Starten des [!INCLUDE[psversion2](../Token/psversion2_md.md)]-Moduls finden Sie unter [Starten des Windows PowerShell 2.0-Moduls](../Topic/Starting-the-Windows-PowerShell-2.0-Engine.md).

## Windows Preinstallation Environment
[!INCLUDE[psversion2](../Token/psversion2_md.md)], [!INCLUDE[psversion3](../Token/psversion3_md.md)] und [!INCLUDE[psversion4](../Token/psversion4_md.md)] können in der Windows Preinstallation Environment (Windows PE) ausgeführt werden. Die folgenden Cmdlets werden jedoch nicht unterstützt.

-   [Cmdlets für den intelligenten Hintergrundübertragungsdienst (Background Intelligent Transfer Service, BITS)](http://go.microsoft.com/fwlink/?LinkId=257514)

-   [Get-EventLog](https://technet.microsoft.com/en-us/library/b4985b11-82bf-487d-928d-becd96fc0419)

-   [Get-WinEvent[PSITPro5_Diagnostic]](https://technet.microsoft.com/en-us/library/5fe94870-ed6b-4ce2-9500-93846cc65c95)

-   [Save-Help](https://technet.microsoft.com/en-us/library/aed94f90-b73f-4e25-a25d-7c18d9f161fa)

-   [Update-Help](https://technet.microsoft.com/en-us/library/93e1d870-ace6-432b-8778-8920291d7545)

Darüber hinaus ist der **WinRm**-Dienst nicht in der Windows PE vorhanden.

## Weitere Informationen
[Erste Schritte mit Windows PowerShell](../Topic/Getting-Started-with-Windows-PowerShell.md)
[Installieren von Windows PowerShell](../Topic/Installing-Windows-PowerShell.md)
[Starten von Windows PowerShell [ps]](https://technet.microsoft.com/en-us/library/8ec8c2d7-8e7c-4722-a3d2-498fe5739a8e)



<!--HONumber=Apr16_HO2-->


