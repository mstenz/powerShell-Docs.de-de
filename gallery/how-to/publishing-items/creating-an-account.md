---
ms.date: 09/11/2018
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Erstellen eines PowerShell-Katalogkontos
ms.openlocfilehash: 08d18310d9e18b00bd9e22efcc552dfd29f8982c
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/13/2018
ms.locfileid: "45522834"
---
# <a name="creating-a-powershell-gallery-account"></a>Erstellen eines PowerShell-Katalogkontos

Bevor Sie Elemente im PowerShell-Katalog veröffentlichen können, müssen Sie ein PowerShell-Katalog-Konto einrichten.
PowerShell-Katalog-Konten müssen mit einem E-Mail-fähigen Anmeldekonto verknüpft sein. Dieses Konto kann ein Azure Active Directory-Konto oder eine Microsoft-ID sein, wie etwa ein E-Mail-Konto von outlook.com oder hotmail.com.

Besuchen Sie [https://PowerShellGallery.com](https://PowerShellGallery.com), und klicken Sie auf **Sign in** (Anmelden), so wie in der folgenden Abbildung dargestellt.

![Registrieren eines neuen Kontos](../../Images/CreateAccount-Register.png)

Verwenden Sie ein Azure Active Directory-Konto, wählen Sie **Work or School Account** (Geschäfts-, Schul- oder Unikonto) aus, und melden Sie sich mit Ihrem Konto an. Wählen Sie **Personal Account** (Persönliches Konto) aus, und melden Sie sich an, um eine Microsoft-ID zu verwenden.

Als Nächstes werden Sie aufgefordert, einen Benutzernamen für den PowerShell-Katalog zu erstellen. Lesen Sie die Nutzungsbestimmungen und die Datenschutzrichtlinie, geben Sie einen Benutzernamen ein, und klicken Sie dann auf **Register** (Registrieren).

> [!NOTE]
> Der Kontoname kann nach der Erstellung nicht mehr geändert werden. Weitere Informationen finden Sie unter [Verwalten von Elementbesitzern](managing-item-owners.md).

## <a name="recommended-practices-for-powershell-gallery-accounts"></a>Empfohlene Vorgehensweisen für PowerShell-Katalog-Konten

Es ist wichtig, das mit Ihrem PowerShell-Katalog-Konto verwendete E-Mail-Konto aktiv zu überwachen. Die gesamte Kommunikation mit Besitzern von PowerShell-Katalog-Elementen läuft über diese E-Mail-Adresse. Wenn das Betriebsteam des PowerShell-Katalogs einen Elementbesitzer nicht kontaktieren kann, müssen wir ggf. ein Element löschen.

Organisationen, die Elemente im PowerShell-Katalog veröffentlichen, erstellen zu diesem Zweck häufig ein eindeutiges externes Konto. Es wird empfohlen, die E-Mail-Weiterleitung zu nutzen, um Benachrichtigung an eine Adresse innerhalb Ihrer Organisation weiterzuleiten.

Wenn mehrere Besitzer einem Element zugeordnet werden, werden alle PowerShell-Katalog-Benachrichtigungen an alle Besitzer gesendet. Weitere Informationen finden Sie unter [Verwalten von Elementbesitzern](managing-item-owners.md).
