---
ms.date: 09/10/2018
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Verwalten von API-Schlüsseln
ms.openlocfilehash: 954eb27c25babdb8efe50c13caf5f2d287c6b3e3
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71328291"
---
# <a name="managing-api-keys"></a>Verwalten von API-Schlüsseln

Der PowerShell-Katalog unterstützt das Erstellen mehrerer API-Schlüssel für eine Reihe von Anforderungen bei der Veröffentlichung. Ein API-Schlüssel kann sich auf ein oder mehrere Pakete beziehen, gewährt bestimmte Berechtigungen und verfügt über ein Ablaufdatum.

> [!IMPORTANT]
> Benutzer, die vor der Einführung bereichsbezogener API-Schlüssel im PowerShell-Katalog veröffentlicht haben, werden über einen API-Schlüssel mit Vollzugriff verfügen. Die Schlüssel mit Vollzugriff verfügen nicht über die Sicherheitsverbesserungen, die in bereichsbezogene API-Schlüssel eingebaut sind. Die Schlüssel mit Vollzugriff laufen nie ab und gelten für alles, was dem Benutzer gehört. Wenn Sie diesen Schlüssel löschen, kann er nicht neu erstellt werden.

Die folgende Abbildung zeigt die beim Erstellen eines bereichsbezogenen API-Schlüssels verfügbaren Optionen.

![Erstellen von API-Schlüsseln](../../Images/PSGallery_KeyScoped.png)

In diesem Beispiel haben wir einen API-Schlüssel mit dem Namen **AzureRMDataFactory** erstellt. Dieser Schlüsselwert kann zur Übertragung von Paketen mithilfe von Push genutzt werden, deren Namen mit „AzureRM.DataFactory“ beginnen, und ist 365 Tage lang gültig. Dies ist ein typisches Szenario, wenn verschiedene Teams innerhalb einer Organisation an verschiedenen Paketen arbeiten. Die Mitglieder des Teams haben einen Schlüssel, der ihnen Berechtigungen für das jeweilige Paket gewährt, an dem sie arbeiten.
Der Ablaufwert verhindert, dass veraltete oder vergessene Schlüssel verwendet werden.

## <a name="using-glob-patterns"></a>Verwenden von Globmustern

Wenn Sie an mehreren Paketen arbeiten, können Sie mit Globmustern mehrere Pakete als Gruppe zusammenfügen. API-Schlüsselberechtigungen gelten für alle neuen Pakete, die mit dem Globmuster übereinstimmen. Im vorherigen Beispiel wurde etwa als **Globmuster**-Wert „AzureRM.DataFactory*“ verwendet. Sie können ein Paket mit dem Namen „AzureRm.DataFactoryV2.Netcore“ mit diesem Schlüssel mithilfe von Push übertragen, da das Paket mit dem Globmuster übereinstimmt.

## <a name="create-api-keys-securely"></a>Sicheres Erstellen von API-Schlüsseln

Aus Sicherheitsgründen wird ein neu erstellter Schlüsselwert nie auf dem Bildschirm angezeigt und ist wie unten dargestellt nur über die Schaltfläche „Kopieren“ verfügbar.

![Abrufen eines neuen API-Schlüsselwerts](../../Images/PSGallery_CopyCreatedKey.png)

> [!IMPORTANT]
> Sie können den API-Schlüsselwert nur direkt nach dem Erstellen oder Aktualisieren kopieren. Er wird nicht angezeigt und ist nach dem Aktualisieren der Seite nicht mehr verfügbar. Wenn Sie den Schlüsselwert verlieren, müssen Sie „Erneut generieren“ anklicken und den Schlüssel danach kopieren.

## <a name="key-permissions-and-expiration"></a>Schlüsselberechtigungen und Ablaufdatum

Bereichsbezogene API-Schlüssel können folgende Berechtigungen zuweisen:

- Neue Pakete mithilfe von Push übertragen
- Neue Pakete mithilfe von Push übertragen oder Pakete aktualisieren
- Auflistung von Paketen aufheben

Jeder neue Schlüssel verfügt über ein Ablaufdatum. Der Ablaufwert wird in Tagen gemessen. Die möglichen Werte für den Ablauf sind:

- 1 Tag
- 90 Tage
- 180 Tage
- 270 Tage
- 365 Tage (Standard)

Diese Einstellungen können nicht geändert werden, nachdem der Schlüssel erstellt wurde. Sie können keinen neuen Schlüssel erstellen, der nie abläuft.

## <a name="editing-and-deleting-existing-api-keys"></a>Bearbeiten und Löschen vorhandener API-Schlüssel

Sie können einige Einstellungen eines vorhandenen Schlüssels ändern. Wie bereits erwähnt, können Sie den Sicherheitsbereich und das Ablaufdatum eines vorhandenen API-Schlüssels nicht ändern. Die Optionen, die geändert werden können, sehen Sie in folgendem Screenshot:

![Abrufen eines neuen API-Schlüsselwerts](../../Images/PSGallery_EditAPIKey.png)

Zum Ändern der Pakete, die durch einen Schlüssel kontrolliert werden, können Sie einzelne Pakete aus der Liste auswählen oder das Globmuster ändern.

Durch Klicken auf **Erneut generieren** wird ein neuer Schlüsselwert erstellt. Wie beim ursprünglichen Erstellen des Schlüssels müssen Sie den Schlüsselwert direkt nach dem Aktualisieren **Kopieren**. Die Option **Kopieren** ist nicht mehr verfügbar, wenn Sie diese Seite verlassen.

Nach dem Klicken auf **Löschen** wird eine Bestätigungsmeldung angezeigt. Wenn ein Schlüssel gelöscht wurde, kann er nicht mehr verwendet werden.

## <a name="key-expiration"></a>Ablauf des Schlüssels

Zehn Tage vor Ablauf sendet der PowerShell-Katalog eine E-Mail zur Warnung an den Kontoinhaber des API-Schlüssels. Nach Ablauf kann der Schlüssel nicht mehr verwendet werden. Eine Warnmeldung erscheint oben auf der Verwaltungsseite des API-Schlüssels und gibt an, welche Schlüssel nicht mehr gültig sind. Sie können einen neuen Schlüsselwert erstellen.
