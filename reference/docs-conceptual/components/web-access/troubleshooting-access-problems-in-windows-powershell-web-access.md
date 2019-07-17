---
ms.date: 08/23/2017
keywords: powershell,cmdlet
title: Behandeln von Zugriffsproblemen in Windows PowerShell Web Access
ms.openlocfilehash: 66e913504cf0c34f8d9ab18b088fb06173aca24c
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733865"
---
# <a name="troubleshooting-access-problems-in-windows-powershell-web-access"></a>Behandeln von Zugriffsproblemen in Windows PowerShell Web Access

Aktualisiert: 24. Juni 2013 (überarbeitet: 23. August 2017)

Gilt für: Windows Server 2012 R2, Windows Server 2012

Im folgenden Abschnitt sind einige allgemeine Probleme aufgeführt, die auftreten können, wenn versucht wird, über Windows PowerShell Web Access eine Verbindung mit einem Remotecomputer herzustellen. Außerdem enthält die Tabelle Vorschläge zur Behebung der Probleme.

## <a name="sign-in-failure"></a>Fehler bei der Anmeldung.

Ein Fehler kann aufgrund einer der folgenden Bedingungen auftreten.

- Es gibt keine Autorisierungsregel, die dem Benutzer den Zugriff auf den Computer oder eine bestimmte Sitzungskonfiguration auf dem Remotecomputer erlaubt.

  Die Windows PowerShell Web Access-Sicherheit ist restriktiv. Benutzern muss der Zugriff auf Remotecomputer mithilfe von Autorisierungsregeln explizit gewährt werden.

  Weitere Informationen zum Erstellen von Autorisierungsregeln finden Sie unter [Autorisierungsregeln und Sicherheitsfeatures von Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

- Der Benutzer hat keinen autorisierten Zugriff auf den Zielcomputer. Dies wird durch Zugriffssteuerungslisten bestimmt.

  Weitere Informationen finden Sie unter [Anmelden bei Windows PowerShell Web Access](use-the-web-based-windows-powershell-console.md#signing-in-to-windows-powershell-web-access) oder im Windows PowerShell-Teamblog.

- Die Windows PowerShell-Remoteverwaltung ist auf dem Zielcomputer möglicherweise nicht aktiviert.

  Stellen Sie sicher, dass die Remoteverwaltung auf dem Computer aktiviert ist, mit dem der Benutzer eine Verbindung herstellen möchte.

  Weitere Informationen finden Sie unter [How to Configure Your Computer for Remoting (Vorgehensweise: Konfigurieren Ihres Computers für das Remoting)](/powershell/module/microsoft.powershell.core/about/about_remote_requirements#how-to-configure-your-computer-for-remoting).

## <a name="internal-server-error"></a>Interner Serverfehler.

Wenn Benutzer versuchen, sich in einem Internet Explorer-Fenster bei Windows PowerShell Web Access anzumelden, wird die Seite **Interner Serverfehler** angezeigt, oder der *Internet Explorer* reagiert nicht mehr.

Dieses Problem tritt speziell in Internet Explorer auf.

### <a name="possible-cause"></a>Mögliche Ursache

Dies kann bei Benutzern der Fall sein, die sich mit einem Domänennamen angemeldet haben, der chinesische Zeichen enthält, oder wenn der Gatewayservername mindestens ein chinesisches Zeichen aufweist.

#### <a name="workaround"></a>Problemumgehung

1. [Install and run Internet Explorer 10 (Installieren und Ausführen von Internet Explorer 10)](https://ie.microsoft.com/testdrive/info/downloads/Default.html)
1. Ändern Sie für Internet Explorer die Einstellung **Dokumentmodus** in *IE10-Standards*.
   1. Drücken Sie die Taste **F12**, um die Konsole mit den Entwicklertools zu öffnen.
   1. Klicken Sie in Internet Explorer 10 auf **Browsermodus**, und wählen Sie die Option *Internet Explorer 10* aus.
   1. Klicken Sie auf **Dokumentmodus** und dann auf *IE10-Standards*.
   1. Drücken Sie die Taste **F12** erneut, um die Konsole mit den Entwicklertools zu schließen.
1. Deaktivieren Sie die automatische Proxykonfiguration in Internet Explorer 10.
   1. Klicken Sie auf **Tools**und dann auf **Internetoptionen**.
   1. Klicken Sie im Dialogfeld **Internetoptionen** auf der Registerkarte **Verbindungen** auf **LAN-Einstellungen**.
   1. Deaktivieren Sie das Kontrollkästchen **Automatische Suche der Einstellungen**. Klicken Sie auf **OK** und dann erneut auf **OK**, um das Dialogfeld *Internetoptionen* zu schließen.

## <a name="cannot-connect-to-a-remote-workgroup-computer"></a>Es kann keine Verbindung mit einem Remotecomputer in einer Arbeitsgruppe hergestellt werden.

Wenn der Zielcomputer Mitglied einer Arbeitsgruppe ist, können Sie die folgende Syntax verwenden, um den Benutzernamen anzugeben und sich am Computer anzumelden: `<workgroup_name>\<user_name>`.

## <a name="cannot-find-web-server-iis-management-tools-even-though-the-role-was-installed"></a>Die Verwaltungstools des Webservers (IIS) sind nicht verfügbar, obwohl die Rolle installiert wurde.

Wenn Sie Windows PowerShell Web Access mit dem Cmdlet `Install-WindowsFeature` installiert haben, werden die Verwaltungstools nur installiert, wenn dem Cmdlet der Parameter `-IncludeManagementTools` hinzugefügt wird.

Ein Beispiel finden Sie unter [To install Windows PowerShell Web Access by using Windows PowerShell cmdlets (Installieren von Windows PowerShell Web Access mithilfe von Windows PowerShell-Cmdlets)](install-and-use-windows-powershell-web-access.md#to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets).

Sie können die IIS-Manager-Konsole und andere benötigte IIS-Verwaltungstools hinzufügen, indem Sie die Tools in einer Sitzung des **Assistenten zum Hinzufügen von Rollen und Features** auswählen, die auf den Gatewayserver ausgerichtet sind.
Der Assistent zum Hinzufügen von Rollen und Features wird über den Server-Manager geöffnet.

## <a name="windows-powershell-web-access-website-is-not-accessible"></a>Auf die Windows PowerShell Web Access-Website kann nicht zugegriffen werden

Wenn die verstärkte Sicherheitskonfiguration in Internet Explorer (IE ESC) aktiviert ist, können Sie die Windows PowerShell Web Access-Website der Liste der vertrauenswürdigen Websites hinzufügen.

Ein wenig empfohlener Ansatz ist wegen Sicherheitsrisiken das Deaktivieren von IE ESC.
Sie können IE ESC auf der Kachel „Eigenschaften“ der Seite „Lokaler Server“ im Server-Manager deaktivieren.

## <a name="an-authorization-failure-occurred-verify-that-you-are-authorized-to-connect-to-the-destination-computer"></a>Fehler bei der Autorisierung. Stellen Sie sicher, dass Sie zum Herstellen einer Verbindung mit dem Zielcomputer autorisiert sind.

Die obenstehende Fehlermeldung wird beim Versuch angezeigt, eine Verbindung herzustellen, wenn der Gatewayserver der Zielcomputer ist und sich auch in einer Arbeitsgruppe befindet.

Wenn der Gatewayserver auch der Zielserver ist und sich in einer Arbeitsgruppe befindet, geben Sie den Benutzernamen, den Computernamen und den Benutzergruppennamen an.
Verwenden Sie nicht nur einen Punkt (.) als Computernamen.

### <a name="scenarios-and-proper-values"></a>Szenarios und richtige Werte

#### <a name="all-cases"></a>Alle Fälle

Parameter | Wert
-- | --
UserName | Server\_name\\user\_name<br/>Localhost\\user\_name<br/>.\\user\_name
UserGroup | Server\_name\\user\_group<br/>Localhost\\user\_group<br/>.\\user\_group
ComputerGroup | Server\_name\\computer\_group<br/>Localhost\\computer\_group<br/>.\\computer\_group

#### <a name="gateway-server-is-in-a-domain"></a>Gatewayserver befindet sich in Domäne

Parameter | Wert
-- | --
ComputerName | Vollqualifizierter Name des Gatewayservers oder Localhost

#### <a name="gateway-server-is-in-a-workgroup"></a>Gatewayserver befindet sich in Arbeitsgruppe

Parameter | Wert
-- | --
ComputerName | Servername

### <a name="gateway-credentials"></a>Gateway-Anmeldeinformationen

Melden Sie sich bei einem Gatewayserver als Zielcomputer an, indem Sie Anmeldeinformationen in einem der folgenden Formate verwenden.

- Server\_name\\user\_name
- Localhost\\user\_name
- .\\user\_name

## <a name="a-security-identifier-sid-is-displayed-in-an-authorization-rule"></a>Eine Sicherheits-ID (SID) wird in einer Autorisierungsregel angezeigt.

Eine Sicherheits-ID wird in einer Autorisierungsregel anstelle der Syntax user\_name/computer\_name angezeigt.

Entweder ist die Regel nicht mehr gültig, oder bei der Active Directory-Domänendienste-Abfrage ist ein Fehler aufgetreten.
Eine Autorisierungsregel ist normalerweise nicht in Fällen gültig, in denen der Gatewayserver zuerst einer Arbeitsgruppe angehörte, dann jedoch einer Domäne beigetreten ist.

## <a name="cannot-sign-in-with-rule-as-an-ipv6-address-with-a-domain"></a>Es ist nicht möglich, sich bei einer Regel mit einer IPv6-Adresse mit einer Domäne anzumelden.

Anmeldung an einem Zielcomputer, der in Autorisierungsregeln als IPv6-Adresse mit einer Domäne angegeben wurde, nicht möglich

Autorisierungsregeln unterstützen keine IPv6-Adresse in Form eines Domänennamens.

Verwenden Sie zum Angeben eines Zielcomputers mithilfe einer IPv6-Adresse die ursprüngliche IPv6-Adresse (mit Doppelpunkten) in der Autorisierungsregel.
Sowohl domänenbezogene als auch numerische IPv6-Adressen (mit Doppelpunkten) werden auf der Anmeldeseite von Windows PowerShell Web Access als Zielcomputername unterstützt. Dies gilt jedoch nicht für Autorisierungsregeln.

Weitere Informationen zu IPv6-Adressen finden Sie unter [Funktionsweise von IPv6](https://technet.microsoft.com/library/cc781672(v=ws.10).aspx).

## <a name="see-also"></a>Weitere Informationen

- [Authorization Rules and Security Features of Windows PowerShell Web Access (Autorisierungsregeln und Sicherheitsfeatures von Windows PowerShell Web Access)](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)
- [Use the Web-based Windows PowerShell Console (Verwenden der webbasierten Windows PowerShell-Konsole)](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)
- [about_Remote_Requirements](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_requirements)
