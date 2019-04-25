---
title: HelpInfo-XML-Schema | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74dcb396-c295-4457-b84c-4432bdaa8df3
caps.latest.revision: 7
ms.openlocfilehash: 0f965f4ee1ef92a6a538b52b4348c04366cabf66
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082463"
---
# <a name="helpinfo-xml-schema"></a>XML-Schema von HelpInfo

Dieses Thema enthält das XML-Schema für aktualisierbare Hilfe-Informationen-Dateien, die so genannte "HelpInfo XML-Dateien."

## <a name="helpinfo-xml-schema"></a>XML-Schema von HelpInfo

HelpInfo XML-Dateien basieren auf dem folgenden XML-Schema.

```xml
<?xml version="1.0" encoding="utf-8"?>
<schema targetNamespace="http://schemas.microsoft.com/powershell/help/2010/05" xmlns="http://www.w3.org/2001/XMLSchema">
  <element name="HelpInfo">
    <complexType>
      <sequence>
        <element name="HelpContentURI" type="anyURI" minOccurs="1" maxOccurs="1" />
        <element name="SupportedUICultures" minOccurs="1" maxOccurs="1">
          <complexType>
            <sequence>
              <element name="UICulture" minOccurs="1" maxOccurs="unbounded">
                <complexType>
                  <sequence>
                    <element name="UICultureName" type="language" minOccurs="1" maxOccurs="1" />
                    <element name="UICultureVersion" type="string" minOccurs="1" maxOccurs="1" />
                  </sequence>
                </complexType>
              </element>
            </sequence>
          </complexType>
        </element>
      </sequence>
    </complexType>
  </element>
</schema>
```

## <a name="helpinfo-xml-elements"></a>HelpInfo-XML-Elemente

Die HelpInfo XML-Datei enthält die folgenden Elemente.

HelpContentURI enthält den URI, der den Speicherort der CAB-Dateien für das Modul-Hilfe. Der URI muss mit "http" oder "Https" beginnen. Der URI sollte einen Speicherort im Internet angeben, aber Sie dürfen keine den Namen der CAB-Datei. Die **HelpContentURI** Wert gleich sein oder sich von der **HelpInfoURI** Wert.

SupportedUICultures stellt die Hilfedateien für Module in allen UI-Kulturen. Enthält **UICulture** Elemente, von denen jedes eine Reihe von Hilfedateien für das Modul in einer angegebenen UI-Kultur darstellt.

UICulture stellt eine Reihe von Hilfedateien für das Modul in eine angegebene Benutzeroberflächenkultur dar. Hinzufügen einer **UICulture** -Element für jede Benutzeroberflächenkultur, die in der die Dateien geschrieben werden.

UICultureName enthält der Sprachcode für die Kultur der Benutzeroberfläche, in der die Hilfedateien geschrieben werden.

UICultureVersion enthält eine 4-Part-Versionsnummer in "N1. N2. N3. N4 "Format, das die Version der Hilfedatei CAB-Datei in der UI-Kultur darstellt. Diese Versionsnummer sollte erhöht werden, wenn Sie neue Hilfe in der UI-Kultur eine CAB-Dateien hochladen, die angegeben wird **UICultureName**. Weitere Informationen zu diesen Wert zu erhalten finden Sie unter "Version Class (System)" in MSDN.