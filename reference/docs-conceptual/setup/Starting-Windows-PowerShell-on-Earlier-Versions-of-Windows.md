---
ms.date: 2017-06-05T00:00:00.000Z
keywords: powershell,cmdlet
title: "Starten von Windows PowerShell unter früheren Versionen von Windows"
ms.assetid: 57125436-3d1e-4e7f-b5c4-8f0ecb49d642
ms.openlocfilehash: cb56fded1e67a4f4219d210dd95078314e855b1a
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2017
---
# <a name="starting-windows-powershell-on-earlier-versions-of-windows"></a>Starten von Windows PowerShell unter früheren Versionen von Windows
In diesem Abschnitt wird das Starten von Windows PowerShell und Windows PowerShell Integrated Scripting Environment (ISE) unter Windows® 7, Windows Server® 2008 R2 und Windows Server® 2008 erläutert. Außerdem wird beschrieben, wie das optionale Feature für Windows PowerShell ISE in Windows PowerShell 2.0 in Windows Server® 2008 R2 und Windows Server® 2008 aktiviert wird.

Zum Installieren von Windows PowerShell 4.0 in unterstützten Systemen müssen Sie [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881) herunterladen und installieren. Weitere Informationen finden Sie unter [Installieren von Windows PowerShell](Installing-Windows-PowerShell.md).

Zum Installieren von Windows PowerShell 3.0 in unterstützten Systemen müssen Sie [Windows Management Framework 3.0](http://go.microsoft.com/fwlink/?LinkID=240290) herunterladen und installieren. Weitere Informationen finden Sie unter [Installieren von Windows PowerShell](Installing-Windows-PowerShell.md).

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a>Starten von Windows PowerShell unter früheren Versionen von Windows
Mit den folgenden Methoden können Sie die installierte Version von Windows PowerShell 3.0 oder Windows PowerShell 4.0 installieren, sofern zutreffend.

#### <a name="from-the-start-menu"></a>Über das Startmenü

-   Klicken Sie auf **Start**, geben Sie **PowerShell** ein, und klicken Sie dann auf **Windows PowerShell**.

-   Klicken Sie im Menü **** **Start** auf **Alle Programme**, danach auf **Zubehör**, anschließend auf den Ordner **Windows PowerShell** und schließlich auf **Windows PowerShell**.

#### <a name="at-the-command-prompt"></a>An der Eingabeaufforderung

-   Geben Sie zum Starten von Windows PowerShell in Cmd.exe, Windows PowerShell oder Windows PowerShell ISE Folgendes ein:

    ```
    PowerShell
    ```

    Sie können auch die Parameter des Programms „PowerShell.exe“ verwenden, um die Sitzung anzupassen. Weitere Informationen finden Sie unter [PowerShell.exe – Befehlszeilenhilfe](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).

#### <a name="with-administrative-privileges-run-as-administrator"></a>Mit administrativen Berechtigungen (Als Administrator ausführen)

1.  Klicken Sie auf **Start**, geben Sie **PowerShell** ein, klicken Sie mit der rechten Maustaste auf **Windows PowerShell**, und klicken Sie dann auf **Als Administrator ausführen**.

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a>Starten von Windows PowerShell ISE unter früheren Versionen von Windows
Verwenden Sie eine der folgenden Methoden, um Windows PowerShell ISE zu starten:

#### <a name="from-the-start-menu"></a>Über das Startmenü

-   Klicken Sie auf **Start**, geben Sie **ISE** ein, und klicken Sie dann auf **Windows PowerShell ISE**.

-   Klicken Sie im Menü **** **Start** auf **Alle Programme**, danach auf **Zubehör**, anschließend auf den Ordner **Windows PowerShell** und schließlich auf **Windows PowerShell ISE**.

#### <a name="at-the-command-prompt"></a>An der Eingabeaufforderung

-   Geben Sie zum Starten von Windows PowerShell in Cmd.exe, Windows PowerShell oder Windows PowerShell ISE Folgendes ein:

    ```
    PowerShell_ISE
    ```

    oder

    ```
    ISE
    ```

#### <a name="with-administrative-privileges-run-as-administrator"></a>Mit administrativen Berechtigungen (Als Administrator ausführen)

1.  Klicken Sie auf **Start**, geben Sie **ISE** ein, klicken Sie mit der rechten Maustaste auf **Windows PowerShell ISE**, und klicken Sie dann auf **Als Administrator ausführen**.

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a>Aktivieren von Windows PowerShell ISE unter früheren Versionen von Windows
In Windows PowerShell 4.0 und Windows PowerShell 3.0 ist Windows PowerShell ISE standardmäßig für alle Versionen von Windows aktiviert. Falls es nicht bereits aktiviert ist, erfolgt die Aktivierung mithilfe von Windows Management Framework 4.0 oder Windows Management Framework 3.0.

In Windows PowerShell 2.0 ist Windows PowerShell ISE standardmäßig für Windows 7 aktiviert. Allerdings ist es in Windows Server 2008 R2 und Windows Server 2008 ein optionales Feature.

Gehen Sie wie folgt vor, um Windows PowerShell ISE in Windows PowerShell 2.0 unter Windows Server 2008 R2 oder Windows Server 2008 zu aktivieren.

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a>So aktivieren Sie Windows PowerShell Integrated Scripting Environment (ISE)

1.  Starten Sie den Server-Manager.

2.  Klicken Sie auf **Features** und dann auf **Features hinzufügen**.

3.  Klicken Sie unter „Features auswählen“ auf „Windows PowerShell Integrated Scripting Environment (ISE)“.

