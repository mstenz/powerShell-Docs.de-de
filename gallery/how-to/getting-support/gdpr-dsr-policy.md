---
ms.date: 03/27/2018
contributor: JKeithB
keywords: katalog,powershell,psgallery,GDPR
title: DSGVO-Kompatibilität für den PowerShell-Katalog
ms.openlocfilehash: 14b82fa07df52f02f0d7577cb0eef70faa4285a2
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893245"
---
# <a name="powershell-gallery-gdpr-compliance"></a>DSGVO-Kompatibilität für den PowerShell-Katalog

## <a name="overview"></a>Übersicht

Im Mai 2018 tritt die Datenschutz-Grundverordnung (DSGVO) der Europäischen Union in Kraft.
Im Rahmen der DSGVO treten neue Regeln für Unternehmen, Behörden und gemeinnützige sowie andere Organisationen in Kraft, die den Verbrauchern in der Europäischen Union Güter und Dienstleitungen anbieten bzw. personenbezogene Daten der EU-Bürger sammeln und analysieren.
Diese Grundverordnung gilt unabhängig von Ihrem Unternehmenssitz.

> [!NOTE]
> In diesem Artikel wird erläutert, wie Sie personenbezogene Daten aus dem PowerShell-Katalog löschen und Ihre Verpflichtungen gemäß der DSGVO erfüllen. Allgemeine Informationen zur DSGVO finden Sie unter [GDPR section of the Service Trust portal (DSGVO-Bereich des Service Trust Portals)](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).

## <a name="personally-identifiable-data"></a>Personenbezogene Daten

Im PowerShell-Katalog werden die folgenden Informationen gespeichert, die möglicherweise von Benutzern bereitgestellt werden und personenbezogene Daten enthalten:

- PowerShell-Katalog-Konto
- Im PowerShell-Katalog veröffentlichte Elemente
- E-Mail-Korrespondenz mit dem PowerShell-Katalog-Team

Die meisten Benutzer erstellen kein Konto für den PowerShell-Katalog.
Ein Konto ist nur erforderlich, wenn Sie ein Element veröffentlichen oder das Feature „Contact Owner“ (Besitzer kontaktieren) im PowerShell-Katalog verwenden wollen.
Neben der vom Benutzer ausgehenden E-Mail-Korrespondenz speichert der PowerShell-Katalog keine personenbezogenen Daten von Benutzern, die kein Konto erstellt haben.

Benutzer, die ein PowerShell-Katalog-Konto erstellen, können Elemente in PowerShell-Katalog veröffentlichen.
Es wird zwar erwartet, dass es sich bei diesen Elementen um PowerShell-Code handelt, sie können jedoch auch andere Informationen enthalten, einschließlich personenbezogener Daten.
Im Folgenden erhalten Sie Informationen dazu, wie Sie sämtliche Elemente abrufen können, die Sie im PowerShell-Katalog veröffentlich haben.

## <a name="dsr-export-of-powershell-gallery-data"></a>DSR-Export von Daten aus dem PowerShell-Katalog

In den folgenden Abschnitten wird erläutert, wie der PowerShell-Katalog sämtliche DSR-Anforderungen (Data Subject Rights) unterstützt. Sie erhalten Informationen dazu, wie Sie im PowerShell-Katalog gespeicherte Informationen exportieren und wie Sie das Löschen dieser Informationen anfordern.

### <a name="email"></a>E-Mail

Die E-Mail-Korrespondenz kann Folgendes umfassen:

- E-Mails, die an die Besitzer der Elemente im PowerShell-Katalog gesendet wurden, wenn im Rahmen der Codeanalyseüberprüfungen ein Problem mit einem Element festgestellt wurde, das sie im PowerShell-Katalog veröffentlich haben
- E-Mail von einer beliebigen Person an das PowerShell-Katalogteam, die an die auf der Seite „Kontakt“ ([cgadmin@microsoft.com](mailto:cgadmin@microsoft.com)) genannte E-Mail-Adresse gesendet wurde
- Registrierte Benutzer, die das Feature „Contact Owner“ (Besitzer kontaktieren) im PowerShell-Katalog verwenden, um eine E-Mail an den Besitzer eines Element zu senden, das sich im PowerShell-Katalog befindet

Für E-Mails, die vom PowerShell-Katalog oder an diesen gesendet werden, gilt eine Aufbewahrungsrichtlinie, gemäß derer die E-Mails 90 Tage lang für mögliche Sicherheitsuntersuchungen gespeichert werden müssen, die durchgeführt werden, wenn schädlicher Code im PowerShell-Katalog entdeckt werden sollte.
Gemäß der Richtlinie werden diese E-Mails nach 90 Tagen gelöscht.

Sie können innerhalb von 90 Tagen Kopien aller E-Mails anfordern, die Sie mit Ihrer E-Mail-Adresse oder dem PowerShell-Katalog gesendet haben oder die an Sie gesendet wurden.
Wenn Sie diese Korrespondenz anfordern möchten, senden Sie eine E-Mail an [cgadmin@microsoft.com](mailto:cgadmin@microsoft.com) mit dem Betreff „DSR-Anforderung für E-Mails, die dieses Konto betreffen“.
Geben Sie in dieser E-Mail an, welche Informationen Sie anfordern, z.B.: Senden Sie mir bitte alle E-Mails, die von dieser E-Mail-Adresse aus gesendet wurden bzw. die an sie gesendet wurde. Alle E-Mails der letzten 90 Tage, die Ihre E-Mail-Adresse betreffen, werden innerhalb von sieben Werktagen an Sie gesendet.

### <a name="powershell-gallery-account-information"></a>Informationen zum PowerShell-Katalog-Konto

Wenn Sie ein PowerShell-Katalog-Konto erstellt haben, finden Sie sämtliche personenbezogenen Daten, die im PowerShell-Katalog gespeichert wurden, indem Sie die folgenden Schritte ausführen:

1. Melden Sie sich im PowerShell-Katalog an, und klicken Sie auf Ihren Benutzernamen
2. Dann wird als nächstes die Seite „Konto“ angezeigt, auf der Sie die E-Mail-Adresse sehen, die für das PowerShell-Katalog-Konto verwendet wird.

Wenn Sie mehr als ein Konto im PowerShell-Katalog erstellt haben, müssen Sie diese Schritte für jedes einzelne Konto ausführen.

### <a name="items-in-the-powershell-gallery"></a>Elemente im PowerShell-Katalog

Um das Exportieren von im PowerShell-Katalog veröffentlichten Elementen zu vereinfachen, wurde das Skript „GetPSGalleryItemsForAuthor“ im PowerShell-Katalog veröffentlicht.
Dieses Skript exportiert basierend auf den im Element gespeicherten Autoreninformationen eine Kopie jeder Version von jedem Element, das im PowerShell-Katalog gespeichert wurde.

> [!NOTE]
> Der Autor wird im Elementmanifest gespeichert, wenn Sie Ihr Element veröffentlichen.
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

Sie werden aufgefordert, den Autor und einen Ordner auf Ihrem System anzugeben, in dem die Elemente gespeichert werden sollen.

## <a name="deleting-personal-data-from-the-powershell-gallery"></a>Löschen von personenbezogenen Daten aus dem PowerShell-Katalog

Wenn Sie Ihr PowerShell-Katalog-Konto oder ein beliebiges Element, das Sie besitzen, aus dem PowerShell-Katalog löschen, senden Sie eine E-Mail an cgadmin@microsoft.com mit dem Betreff: „DSGVO-Anforderung für Elemente, die im Zusammenhang mit diesem Konto stehen“.
Geben Sie in dieser E-Mail an, welche Informationen gelöscht werden sollen. Beispiel:

- Bitte löschen Sie Version x.y.z des Elements „[Elementname]“
- Bitte löschen Sie alle Versionen des Elements „[Elementname]“
- Bitte löschen Sie mein PowerShell-Katalog-Konto

Die Administratoren von PowerShell-Katalog werden Ihnen innerhalb von sieben Werktagen eine Antwort zukommen lassen.
Die angegebenen Elemente werden innerhalb von 30 Tagen, nachdem die Anforderung gesendet wurde, gelöscht.