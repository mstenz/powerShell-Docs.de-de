---
ms.date: 09/05/2018
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Kontoeinstellungen für den PowerShell-Katalog
ms.openlocfilehash: ebe784ec5aae5ff3a4d444d12a168ef38aaef65f
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71328031"
---
# <a name="powershell-gallery-account-settings"></a>Kontoeinstellungen für den PowerShell-Katalog

Ihr Konto für den PowerShell-Katalog ist ein öffentlich sichtbarer Name, der mit einer Identität verknüpft ist. Diese Identität ist entweder eine Microsoft-ID, wie z.B. `user@hotmail.com` oder `user@outlook.com`, oder ein AAD-Konto.

Über den PowerShell-Katalog können Sie die folgenden Einstellungen vornehmen:

- Sie können das E-Mail-Konto festlegen, das mit Ihrem PowerShell-Katalog-Konto verknüpft sein soll.
- Sie können die E-Mail-Benachrichtigungseinstellungen anpassen, die vom PowerShell-Katalog gesendet werden.
- Sie können das Benutzerkonto festlegen, das mit Ihrem PowerShell-Katalog-Konto verknüpft sein soll.
- Sie können das Profilbild festlegen, das mit Ihrem PowerShell-Katalog-Konto verknüpft sein soll.

## <a name="email-address"></a>E-Mail-Adresse

An die E-Mail-Adresse werden die Benachrichtigungen des PowerShell-Katalogs gesendet. Sie muss nicht mit dem Anmeldekonto übereinstimmen. Sie können eine beliebige Ihrer E-Mail-Adressen verwenden. Ihre E-Mail-Adresse wird nicht direkt an andere Benutzer des PowerShell-Katalogs weitergegeben.

![E-Mail-Adresse ändern](../../Images/PSGallery_AcccountEmailAddress.png)

Wenn Sie eine neue E-Mail-Adresse eingeben, sendet der PowerShell-Katalog eine Verifizierungs-E-Mail an diese Adresse. Die Verifizierungs-E-Mail enthält einen Link zurück zum PowerShell-Katalog, wo Sie den Vorgang abschließen können. Bis zum Abschluss der Verifizierung werden alle Benachrichtigungen an die alte E-Mail-Adresse geschickt.

## <a name="email-notifications"></a>E-Mail-Benachrichtigungen

Über den PowerShell-Katalog können Sie die folgenden Benachrichtigungseinstellungen vornehmen:

- Benutzer können mich über den PowerShell-Katalog kontaktieren
- Benachrichtigen, wenn ein Paket mit meinem Konto in den PowerShell-Katalog gepusht wird

![E-Mail-Adresse ändern](../../Images/PSGallery_AccountEmailOptions.png)

Wie auch auf der Seite angemerkt, können wichtige Benachrichtigungen des PowerShell-Katalogs nicht deaktiviert werden.
Dazu zählen:

- Sicherheitsbenachrichtigungen
- Benachrichtigungen zur Kontoverwaltung von PowerShell-Katalog-Administratoren
- Benachrichtigungen zu vom PowerShell-Katalog ausgeführten Tests bezüglich Paketen, die Sie eingereicht haben

## <a name="change-your-login-account"></a>Ändern des Anmeldekontos

Sie müssen mit dem aktuellen Konto angemeldet sein, um das Anmeldekonto zu ändern. Führen Sie zum Ändern die folgenden Schritte aus:

![Kontoeinstellungen](../../Images/PSGallery_LoginAccountSettings.png)

1. Klicken Sie auf **Kontotyp ändern**. In einem Popupfenster wird erklärt, dass die Änderung des Anmeldekontos für den gesamten PowerShell-Katalog gilt. Überprüfen Sie die Informationen, und klicken Sie dann auf **OK**.

   ![Kontoeinstellungen](../../Images/PSGallery_LoginAccountChange-1.png)

2. Dann werden Sie aufgefordert, sich mit dem _neuen Konto_ anzumelden.

   ![Kontoeinstellungen](../../Images/PSGallery_LoginAccountChange-2.png)

3. Wenn Sie auf **Weiter klicken**, wird eine Meldung angezeigt, dass Sie noch mit Ihrem alten Konto angemeldet sind.
   Klicken Sie auf **Sign out and sign in with a different account** (Abmelden und mit anderem Konto anmelden).

   ![Kontoeinstellungen](../../Images/PSGallery_LoginAccountChange-3.png)

4. Geben Sie das Kennwort für das neue Konto ein. Wenn Sie das Kennwort eingegeben haben, werden Sie zu den Kontoeinstellungen weitergeleitet. Dort wird angezeigt, dass das Anmeldekonto aktualisiert wurde.


## <a name="enable-two-factor-authentication-2fa"></a>Aktivieren der zweistufigen Authentifizierung

Die zweistufige Authentifizierung wird für alle Benutzer empfohlen, die ihre Veröffentlichungen im PowerShell-Katalog manuell durchführen. Für das Anmeldekonto müssen mindestens zwei Authentifizierungsmethoden registriert sein, damit die zweistufige Authentifizierung aktiviert werden kann. Die eine Methode ist ein Kennwort, und die andere kann eine der folgenden Methoden sein:

- eine Telefonnummer, an die SMS gesendet werden können
- eine registrierte Authentifikatoranwendung, wie z.B. Microsoft Authenticator, für Ihr Mobiltelefon

Die Authentifizierungsmethoden müssen in Ihren AAD-Kontoinformationen oder in den Kontosicherheitseinstellungen Ihrer Microsoft-ID konfiguriert werden.

Wenn Sie die zweistufige Authentifizierung aktivieren, müssen Sie sich bei jeder Anmeldung beim PowerShell-Katalog mit den konfigurierten Methoden authentifizieren.

> [!IMPORTANT]
> Sie müssen die zweistufige Authentifizierung nicht für alle Benutzer des Anmeldekontos aktivieren, wenn Sie sie für den PowerShell-Katalog aktiviert haben. Weitere Informationen finden Sie unter [Informationen zur Überprüfung in zwei Schritten](https://support.microsoft.com/help/12408/microsoft-account-about-two-step-verification).

## <a name="change-your-profile-picture"></a>Ändern des Profilbilds

Gravatar ist im PowerShell-Katalog für das Speichern und Anzeigen von Profilbildern zuständig. Besuchen Sie [gravatar.com](http://www.gravatar.com/), um Ihr Profilbild zu ändern.
