---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Verwalten von Paketbesitzern
ms.openlocfilehash: 5cf26a7195ac446177cbb7f3a055e8e0a78569cc
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71328261"
---
# <a name="managing-package-owners"></a>Verwalten von Paketbesitzern

Der Besitz eines Pakets im PowerShell-Katalog wird durch die Person definiert, die das Paket im Katalog veröffentlicht hat.
Mitunter müssen diese Metadaten über die erste Veröffentlichung des Pakets hinaus verwaltet werden, was bedeutet, dass die Besitzermetadaten veränderlich sein müssen, das Paket hingegen nicht.

Alle Paketbesitzer sind Peers.
Das bedeutet, dass alle Paketbesitzer eine neue Version eines Pakets veröffentlichen können. Es bedeutet aber auch, dass jeder Paketbesitzer jeden anderen Paketbesitzer entfernen kann.
Kein Besitzer verfügt über mehr Berechtigungen als andere Besitzer.

## <a name="setting-a-packages-initial-owner"></a>Festlegen des anfänglichen Besitzers eines Pakets

Beim Veröffentlichen eines neues Pakets im PowerShell-Katalog wird der anfängliche Besitzer durch den Benutzer definiert, der das Paket veröffentlicht. Dies richtet sich danach, wessen API-Schlüssel im Cmdlet „Publish-Modul“ verwendet wurde.

## <a name="adding-owners"></a>Hinzufügen von Besitzern

Sobald ein Paket im PowerShell-Katalog veröffentlicht wurde, können ganz einfach zusätzliche Benutzer als Besitzer eines Pakets eingeladen werden.

1. [Melden Sie sich beim PowerShell-Katalog mit dem Konto an](https://powershellgallery.com/users/account/LogOn), das der aktuelle Besitzer eines Pakets ist.
2. Navigieren Sie zu einer Paketseite, indem Sie die Registerkarte „Pakete“ verwenden, suchen oder auf Ihren Benutzernamen und dann auf [**Meine Pakete verwalten**](https://www.powershellgallery.com/account/Packages) klicken.
3. Wenn Sie als Besitzer eines Pakets angemeldet sind, finden Sie auf der linken Seite einen Link „Besitzer verwalten“, auf den Sie klicken können.
4. Geben Sie den Benutzernamen der Person ein, die Sie als Besitzer hinzufügen möchten, und klicken Sie auf „Hinzufügen“.
5. Eine E-Mail wird an den neuen Mitbesitzer gesendet, um ihn als Besitzer eines Pakets einzuladen.
6. Sobald der Benutzer auf den Link klickt, ist er ein vollständiger Mitbesitzer mit Vollzugriff auf ein Paket, einschließlich der Möglichkeit, andere Benutzer als Besitzer zu entfernen.

**HINWEIS**: Der neue Besitzer wird *erst dann* als Besitzer eines Pakets aufgeführt, wenn er den Besitz bestätigt.
Beim Anzeigen der Seite **Besitzer verwalten** sehen Sie bei den aktuellen Besitzern einen Eintrag „Genehmigung steht aus“.
Diese Einladung kann ebenso entfernt werden wie andere Besitzer entfernt werden können.
Dieser Einladungsprozess verhindert, dass Benutzer fälschlicherweise andere Benutzer als Besitzer ihrer Pakete hinzufügen.

Beachten Sie, dass die Metadaten „Autoren“ in reinem Freiformtext vorliegen. Nur „Besitzer“ werden gesteuert.


## <a name="removing-owners"></a>Entfernen von Besitzern

Wenn ein Paket mehrere Besitzer aufweist und einer entfernt werden muss, ist der Prozess einfach:

1. [Melden Sie sich beim PowerShell-Katalog mit dem Konto an](https://powershellgallery.com/users/account/LogOn), das der aktuelle Besitzer eines Paket ist.
2. Navigieren Sie zu einer Paketseite, indem Sie die Registerkarte „Pakete“ verwenden, suchen oder auf Ihren Benutzernamen und dann auf [**Meine Pakete verwalten**](https://www.powershellgallery.com/account/Packages) klicken.
3. Wenn Sie als Besitzer eines Pakets angemeldet sind, finden Sie auf der linken Seite einen Link „Besitzer verwalten“, auf den Sie klicken können.
4. Klicken Sie neben dem Besitzer, der entfernt werden soll, auf den Link „Entfernen“.



## <a name="transferring-package-ownership"></a>Übertragen des Paketbesitzes

Gelegentlich erhalten wir Supportanfragen, um den Besitz eines Pakets von einem Benutzer auf einen anderen zu übertragen. Diesen Vorgang können Sie allerdings fast immer selbst durchführen.
Das Übertragen des Besitzes von einem Benutzer auf einen anderen ist einfach eine Kombination aus den beiden oben genannten Funktionen.

1. Der aktuelle Besitzer lädt den neuen Benutzer als Mitbesitzer ein, und der neue Benutzer akzeptiert die Einladung.
2. Der neue Benutzer entfernt den alten Benutzer aus der Liste der Besitzer.

Diese Anfrage ist über mehrere Formulare eingegangen, der Prozess funktioniert aber immer gleich.

- Der Besitz eines Pakets wechselt von einem Entwickler zu einem anderen.
- Das Paket wurde versehentlich über das falsche Konto veröffentlicht.


## <a name="orphaned-packages"></a>Verwaiste Pakete

Ein letztes Szenario ist aufgetreten, wenn auch nicht häufig.
Pakete waren verwaist und das einzige Paketbesitzerkonto kann nicht zum Hinzufügen neuer Besitzer verwendet werden.
Im Folgenden sind einige Beispiele für dieses Szenario aufgeführt:

- Dem Konto des Besitzers ist eine E-Mail-Adresse zugeordnet, die nicht mehr existiert, und der Benutzer hat das Kennwort vergessen.
- Der registrierte Besitzer hat das Unternehmen verlassen, in dem das Paket erzeugt wird, und kann nicht erreicht werden, um den Besitz des Pakets zu aktualisieren.
- Aufgrund eines Fehlers, der nur wenige Pakete betrifft, befindet sich das Paket ohne Besitzer im Katalog.

Die PowerShell-Katalogadministratoren können für jedes Paket auf den Link „Besitzer verwalten“ zugreifen.
Wenn Sie der rechtmäßige Besitzer eines Pakets sind und den aktuellen Besitzer nicht erreichen können, um Besitzberechtigungen zu erlangen, wenden Sie sich über den Link „Missbrauch melden“ im Katalog an die PowerShell-Katalogadministratoren.
Wir überprüfen dann Ihren Besitz des Pakets anhand eines festgelegten Prozesses.
Wenn wir feststellen, dass Sie der Besitzer des Pakets sein sollten, verwenden wir selbst den Link „Besitzer verwalten“ für das Paket und senden Ihnen die Einladung als Besitzer.
Dies erfolgt jedoch erst, nachdem wir Sie als Besitzer bestätigt haben, und der Vorgang variiert je nach den Umständen.
Oft verwenden wir die Projekt-URL des Pakets, um eine Möglichkeit zum Kontaktieren des Projektbesitzers zu finden. Gelegentlich wenden wir uns jedoch auch über Twitter, E-Mail oder andere Methoden an den Besitzer.
