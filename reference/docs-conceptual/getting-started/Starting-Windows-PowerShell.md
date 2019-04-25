---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Starten von Windows PowerShell
ms.assetid: 59b649a2-c90c-4cf4-bf95-a740c59148e7
ms.openlocfilehash: 9184e8b0e508610e7f4775f1032f3a69c93bb8c1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058351"
---
# <a name="starting-windows-powershell"></a>Starten von Windows PowerShell
PowerShell ist eine Skript-Engine im DLL-Format, die in mehreren Hosts eingebettet ist.  Als Host werden am häufigsten die interaktive Befehlszeile „PowerShell.exe“ und die integrierte Skriptumgebung „PowerShell_ISE.exe“ verwendet.

Informationen zum Starten von Windows PowerShell® unter Windows Server® 2012 R2, Windows® 8.1, Windows Server 2012 und Windows 8 finden Sie unter [Allgemeine Verwaltungsaufgaben und Navigation in Windows](https://technet.microsoft.com/library/hh831491.aspx).

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a>Starten von Windows PowerShell unter früheren Versionen von Windows

In diesem Abschnitt wird das Starten von Windows PowerShell und Windows PowerShell Integrated Scripting Environment (ISE) unter Windows® 7, Windows Server® 2008 R2 und Windows Server® 2008 erläutert. Außerdem wird beschrieben, wie das optionale Feature für Windows PowerShell ISE in Windows PowerShell 2.0 in Windows Server® 2008 R2 und Windows Server® 2008 aktiviert wird.

Mit den folgenden Methoden können Sie die installierte Version von Windows PowerShell 3.0 oder Windows PowerShell 4.0 installieren, sofern zutreffend.

#### <a name="from-the-start-menu"></a>Über das Startmenü

- Klicken Sie auf **Start**, geben Sie **PowerShell** ein, und klicken Sie dann auf **Windows PowerShell**.
- Klicken Sie im **Start** Menü **Start** auf **Alle Programme**, danach auf **Zubehör**, anschließend auf den Ordner **Windows PowerShell** und schließlich auf **Windows PowerShell**.

#### <a name="at-the-command-prompt"></a>An der Eingabeaufforderung

Geben Sie zum Starten von Windows PowerShell in Cmd.exe, Windows PowerShell oder Windows PowerShell ISE Folgendes ein:

```
PowerShell
```

Sie können auch die Parameter des Programms „PowerShell.exe“ verwenden, um die Sitzung anzupassen. Weitere Informationen finden Sie unter [PowerShell.exe – Befehlszeilenhilfe](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).

#### <a name="with-administrative-privileges-run-as-administrator"></a>Mit administrativen Berechtigungen (Als Administrator ausführen)

Klicken Sie auf **Start**, geben Sie **PowerShell** ein, klicken Sie mit der rechten Maustaste auf **Windows PowerShell**, und klicken Sie dann auf **Als Administrator ausführen**.

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a>Starten von Windows PowerShell ISE unter früheren Versionen von Windows

Verwenden Sie eine der folgenden Methoden, um Windows PowerShell ISE zu starten:

#### <a name="from-the-start-menu"></a>Über das Startmenü

- Klicken Sie auf **Start**, geben Sie **ISE** ein, und klicken Sie dann auf **Windows PowerShell ISE**.
- Klicken Sie im **Menü** **Start** auf **Alle Programme**, danach auf **Zubehör**, anschließend auf den Ordner **Windows PowerShell** und schließlich auf **Windows PowerShell ISE**.

#### <a name="at-the-command-prompt"></a>An der Eingabeaufforderung

Geben Sie zum Starten von Windows PowerShell in Cmd.exe, Windows PowerShell oder Windows PowerShell ISE Folgendes ein:

```
PowerShell_ISE
```

oder

```
ISE
```

#### <a name="with-administrative-privileges-run-as-administrator"></a>Mit administrativen Berechtigungen (Als Administrator ausführen)

Klicken Sie auf **Start**, geben Sie **ISE** ein, klicken Sie mit der rechten Maustaste auf **Windows PowerShell ISE**, und klicken Sie dann auf **Als Administrator ausführen**.

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a>Aktivieren von Windows PowerShell ISE unter früheren Versionen von Windows

In Windows PowerShell 4.0 und Windows PowerShell 3.0 ist Windows PowerShell ISE standardmäßig für alle Versionen von Windows aktiviert. Falls es nicht bereits aktiviert ist, erfolgt die Aktivierung mithilfe von Windows Management Framework 4.0 oder Windows Management Framework 3.0.

In Windows PowerShell 2.0 ist Windows PowerShell ISE standardmäßig für Windows 7 aktiviert. Allerdings ist es in Windows Server 2008 R2 und Windows Server 2008 ein optionales Feature.

Gehen Sie wie folgt vor, um Windows PowerShell ISE in Windows PowerShell 2.0 unter Windows Server 2008 R2 oder Windows Server 2008 zu aktivieren.

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a>So aktivieren Sie Windows PowerShell Integrated Scripting Environment (ISE)

1. Starten Sie den Server-Manager.
2. Klicken Sie auf **Features** und dann auf **Features hinzufügen**.
3. Klicken Sie unter „Features auswählen“ auf „Windows PowerShell Integrated Scripting Environment (ISE)“.

## <a name="starting-the-32-bit-version-of-windows-powershell"></a>Starten der 32-Bit-Version von Windows PowerShell

Bei der Installation von Windows PowerShell auf einem 64-Bit-Computer wird **Windows PowerShell (x86)**, eine 32-Bit-Version von Windows PowerShell, zusätzlich zur 64-Bit-Version installiert. Wenn Sie Windows PowerShell ausführen, wird standardmäßig die 64-Bit-Version ausgeführt.

Es kann jedoch möglicherweise erforderlich sein, **Windows PowerShell (x86)** auszuführen, z.B. wenn Sie ein Modul verwenden, das die 32-Bit-Version verlangt, oder Sie eine Remoteverbindung mit einem 32-Bit-Computer herstellen.

Wählen Sie eines der folgenden Verfahren, um eine 32-Bit-Version von Windows PowerShell zu starten.

#### <a name="in-windows-server-2012-r2"></a>In Windows Server® 2012 R2

- Geben Sie im **Startbildschirm** **Windows PowerShell (x86)** ein. Klicken Sie auf die Kachel **Windows PowerShell x86**.
- Wählen Sie im **Server-Manager** im Menü **Extras** den Eintrag **Windows PowerShell (x86)** aus.
- Bewegen Sie auf dem Desktop den Cursor in die rechte obere Ecke, klicken Sie auf **Suchen**, geben Sie **PowerShell x86** ein, und klicken Sie dann auf **Windows PowerShell (x86)**.
- Geben Sie über die Befehlszeile Folgendes ein: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-server-2012"></a>In Windows Server® 2012

- Klicken Sie auf **Start**, geben Sie **PowerShell** ein, und klicken Sie dann auf **Windows PowerShell (x86)**.
- Wählen Sie im **Server-Manager** im Menü **Extras** den Eintrag **Windows PowerShell (x86)** aus.
- Bewegen Sie auf dem Desktop den Cursor in die rechte obere Ecke, klicken Sie auf **Suchen**, geben Sie **PowerShell** ein, und klicken Sie dann auf **Windows PowerShell (x86)**.
- Geben Sie über die Befehlszeile Folgendes ein: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-81"></a>In Windows® 8.1

- Geben Sie im **Startbildschirm** **Windows PowerShell (x86)** ein. Klicken Sie auf die Kachel **Windows PowerShell x86**.
- Falls Sie die [Remoteserver-Verwaltungstools](https://go.microsoft.com/fwlink/?LinkID=304145) für Windows 8.1 ausführen, können Sie Windows PowerShell x86 auch im Server-Manager-Menü **Extras** öffnen.
  Wählen Sie **Windows PowerShell (x86)** aus.
- Bewegen Sie auf dem Desktop den Cursor in die rechte obere Ecke, klicken Sie auf **Suchen**, geben Sie **PowerShell x86** ein, und klicken Sie dann auf **Windows PowerShell (x86)**.
- Geben Sie über die Befehlszeile Folgendes ein: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-8"></a>In Windows® 8

- Bewegen Sie auf dem Bildschirm **Start** den Cursor in die rechte obere Ecke, klicken Sie auf **Einstellungen**, dann auf **Kacheln**, und bewegen Sie den Schieberegler **Verwaltungstools anzeigen** auf „Ja“. Geben Sie dann **PowerShell** ein, und klicken Sie auf **Windows PowerShell (x86)**.
- Falls Sie die [Remoteserver-Verwaltungstools](https://www.microsoft.com/download/details.aspx?id=28972) für Windows 8 ausführen, können Sie Windows PowerShell x86 auch im Server-Manager-Menü **Extras** öffnen. Wählen Sie **Windows PowerShell (x86)** aus.
- Geben Sie auf dem Bildschirm **Start** oder dem Desktop **PowerShell (x86)** ein, und klicken Sie dann auf **Windows PowerShell (x86)**.
- Geben Sie über die Befehlszeile Folgendes ein: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`