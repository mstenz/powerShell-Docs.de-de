---
ms.date: 03/27/2018
contributor: JKeithB
keywords: katalog,powershell,psgallery,GDPR
title: DSGVO-Kompatibilität für den PowerShell-Katalog
ms.openlocfilehash: fb1191d8a1cd12d5994e41238c384eb504d0c261
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71328321"
---
# <a name="powershell-gallery-gdpr-compliance"></a>DSGVO-Kompatibilität für den PowerShell-Katalog

## <a name="overview"></a>Übersicht

Im Mai 2018 trat die Datenschutz-Grundverordnung (DSGVO) der Europäischen Union in Kraft.
Im Rahmen der DSGVO treten neue Regeln für Unternehmen, Behörden und gemeinnützige sowie andere Organisationen in Kraft, die den Verbrauchern in der Europäischen Union Güter und Dienstleitungen anbieten bzw. personenbezogene Daten der EU-Bürger sammeln und analysieren.
Diese Grundverordnung gilt unabhängig von Ihrem Unternehmenssitz.

> [!NOTE]
> In diesem Artikel wird erläutert, wie Sie personenbezogene Daten aus dem PowerShell-Katalog löschen und Ihre Verpflichtungen gemäß der DSGVO erfüllen. Allgemeine Informationen zur DSGVO finden Sie unter [GDPR section of the Service Trust portal (DSGVO-Bereich des Service Trust Portals)](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).

## <a name="personally-identifiable-data"></a>Personenbezogene Daten

Im PowerShell-Katalog werden die folgenden Informationen gespeichert, die möglicherweise von Benutzern bereitgestellt werden und personenbezogene Daten enthalten:

- PowerShell-Katalog-Konto
- Im PowerShell-Katalog veröffentlichte Pakete
- E-Mail-Korrespondenz mit dem PowerShell-Katalog-Team

Die meisten Benutzer erstellen kein Konto für den PowerShell-Katalog.
Ein Konto ist nur erforderlich, wenn Sie ein Paket veröffentlichen oder das Feature „Besitzer kontaktieren“ im PowerShell-Katalog verwenden wollen.
Neben der vom Benutzer ausgehenden E-Mail-Korrespondenz speichert der PowerShell-Katalog keine personenbezogenen Daten von Benutzern, die kein Konto erstellt haben.

Benutzer, die ein Konto im PowerShell-Katalog erstellen, können dort Pakete veröffentlichen.
Es wird zwar erwartet, dass es sich bei diesen Paketen um PowerShell-Code handelt, sie können jedoch auch andere Informationen enthalten, z.B. personenbezogene Daten.
Im Folgenden erhalten Sie Informationen dazu, wie Sie sämtliche Pakete abrufen, die Sie im PowerShell-Katalog veröffentlicht haben.

## <a name="dsr-export-of-powershell-gallery-data"></a>DSR-Export von Daten aus dem PowerShell-Katalog

In den folgenden Abschnitten wird erläutert, wie der PowerShell-Katalog sämtliche DSR-Anforderungen (Data Subject Rights) unterstützt. Sie erhalten Informationen dazu, wie Sie im PowerShell-Katalog gespeicherte Informationen exportieren und wie Sie das Löschen dieser Informationen anfordern.

### <a name="email"></a>E-Mail

Die E-Mail-Korrespondenz kann Folgendes umfassen:

- E-Mails an Besitzer von Paketen im PowerShell-Katalog, wenn die Codeanalyse ein Problem mit einem Paket erkennt, das diese im PowerShell-Katalog veröffentlicht haben
- E-Mail von einer beliebigen Person an das PowerShell-Katalogteam, die an die auf der Seite „Kontakt“ ([cgadmin@microsoft.com](mailto:cgadmin@microsoft.com)) genannte E-Mail-Adresse gesendet wurde
- E-Mails registrierter Benutzer, die im PowerShell-Katalog das Feature „Besitzer kontaktieren“ verwenden, um eine E-Mail an den Besitzer eines Pakets zu senden, das sich im PowerShell-Katalog befindet

Für E-Mails, die vom PowerShell-Katalog oder an diesen gesendet werden, gilt eine Aufbewahrungsrichtlinie, gemäß derer die E-Mails 90 Tage lang für mögliche Sicherheitsuntersuchungen gespeichert werden müssen, die durchgeführt werden, wenn schädlicher Code im PowerShell-Katalog entdeckt werden sollte.
Gemäß der Richtlinie werden diese E-Mails nach 90 Tagen gelöscht.

Sie können innerhalb von 90 Tagen Kopien aller E-Mails anfordern, die Sie mit Ihrer E-Mail-Adresse oder dem PowerShell-Katalog gesendet haben oder die an Sie gesendet wurden.
Um diese Zuordnung anzufordern, senden Sie eine E-Mail mit dem folgenden Titel an [cgadmin@microsoft.com](mailto:cgadmin@microsoft.com): DSR-Anforderung für E-Mails im Zusammenhang mit diesem Konto.
Geben Sie in dieser E-Mail an, welche Informationen Sie anfordern (Beispiel: Bitte übermitteln Sie alle E-Mail-Nachrichten, die an diese E-Mail-Adresse gesendet oder von ihr empfangen wurden). Alle E-Mails der letzten 90 Tage, die Ihre E-Mail-Adresse betreffen, werden innerhalb von sieben Werktagen an Sie gesendet.

### <a name="powershell-gallery-account-information"></a>Informationen zum PowerShell-Katalog-Konto

Wenn Sie ein PowerShell-Katalog-Konto erstellt haben, finden Sie sämtliche personenbezogenen Daten, die im PowerShell-Katalog gespeichert wurden, indem Sie die folgenden Schritte ausführen:

1. Melden Sie sich im PowerShell-Katalog an, und klicken Sie auf Ihren Benutzernamen
2. Dann wird als nächstes die Seite „Konto“ angezeigt, auf der Sie die E-Mail-Adresse sehen, die für das PowerShell-Katalog-Konto verwendet wird.

Wenn Sie mehr als ein Konto im PowerShell-Katalog erstellt haben, müssen Sie diese Schritte für jedes einzelne Konto ausführen.

### <a name="packages-in-the-powershell-gallery"></a>Pakete im PowerShell-Katalog

Um das Exportieren von im PowerShell-Katalog veröffentlichten Pakete zu vereinfachen, wurde das Skript „GetPSGalleryItemsForAuthor“ im PowerShell-Katalog veröffentlicht.
Dieses Skript exportiert auf Grundlage der im Paket gespeicherten Autorinformationen eine Kopie jeder Version von jedem Paket, das im PowerShell-Katalog gespeichert wurde.

> [!NOTE]
> Der Autor wird im Paketmanifest gespeichert, wenn Sie Ihr Paket veröffentlichen.
> Es gibt keine Garantie dafür, dass der Autor dieselbe Identität aufweist wie das von Ihnen im PowerShell-Katalog verwendete Konto.
> Wenn Sie im Feld „Autor“ einen anderen Wert verwenden, müssen Sie den Wert angeben, wenn Sie dieses Skript verwenden.

Sie können das Skript über den folgenden PowerShell-Befehl downloaden:

```powershell
Save-Script Get-repository psgallery
```

Sie können das Skript direkt ausführen, indem Sie den folgenden PowerShell-Befehl ausführen:

```powershell
# cd <local folder location>
.\GetPSGalleryItemsForAuthor.ps1
```

Sie werden aufgefordert, den Autor und einen Ordner in Ihrem System anzugeben, in dem die Pakete gespeichert werden sollen.

## <a name="deleting-personal-data-from-the-powershell-gallery"></a>Löschen von personenbezogenen Daten aus dem PowerShell-Katalog

Um Ihr PowerShell-Katalogkonto oder ein beliebiges Paket zu löschen, das Sie im PowerShell-Katalog besitzen, senden Sie eine E-Mail an cgadmin@microsoft.com mit dem Betreff: „DSGVO-Anfrage für Elemente in Zusammenhang mit diesem Konto“.
Geben Sie in dieser E-Mail an, welche Informationen gelöscht werden sollen. Beispiel:

- Bitte löschen Sie Version x.y.z des Pakets „Paketname“.
- Bitte löschen Sie alle Versionen des Pakets „Paketname“.
- Bitte löschen Sie mein PowerShell-Katalog-Konto

Die Administratoren von PowerShell-Katalog werden Ihnen innerhalb von sieben Werktagen eine Antwort zukommen lassen.
Die angegebenen Pakete werden innerhalb von 30 Tagen nach Senden der Anfrage gelöscht.
