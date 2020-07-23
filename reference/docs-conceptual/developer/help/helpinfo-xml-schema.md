---
title: XML-Schema von HelpInfo
ms.date: 09/12/2016
ms.openlocfilehash: f94d053b8fc558d9efc13e6b9fbd597287970e38
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2020
ms.locfileid: "86953249"
---
# <a name="helpinfo-xml-schema"></a>XML-Schema von HelpInfo

Dieses Thema enthält das XML-Schema für aktualisierbare Hilfe Informationsdateien, die häufig als "helpinfo-XML-Dateien" bezeichnet werden.

## <a name="helpinfo-xml-schema"></a>XML-Schema von HelpInfo

Helpinfo-XML-Dateien basieren auf dem folgenden XML-Schema.

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

## <a name="helpinfo-xml-elements"></a>Helpinfo-XML-Elemente

Die helpinfo-XML-Datei enthält die folgenden Elemente:

- **Helpcontenturi** : enthält den URI des Speicher Orts der Hilfe-CAB-Dateien für das Modul. Der URI muss mit "http" oder "https" beginnen. Der URI sollte einen Internet Speicherort angeben, darf jedoch nicht den CAB-Dateinamen enthalten. Der **helpcontenturi** -Wert kann identisch oder vom **helpinfouri** -Wert abweichen.

- **Supporteduicultures** : stellt die Modul Hilfedateien in allen Benutzeroberflächen Kulturen dar. Enthält **UICulture** -Elemente, von denen jede einen Satz von Hilfedateien für das Modul in einer angegebenen Benutzeroberflächen Kultur darstellt.

- **UICulture** : stellt einen Satz von Hilfedateien für das Modul in einer angegebenen Benutzeroberflächen Kultur dar. Fügen Sie für jede Benutzeroberflächen Kultur, in der die Hilfedateien geschrieben werden, ein **UICulture** -Element hinzu.

- **Uiculturename** : enthält den Sprachcode für die Benutzeroberflächen Kultur, in der die Hilfedateien geschrieben werden.

- **Uicultureversion** : enthält eine 4-teilige Versionsnummer in "N1. N2. N3. N4-Format, das die Version der Hilfe-CAB-Datei in der Benutzeroberflächen Kultur darstellt. Erhöhen Sie diese Versionsnummer immer dann, wenn Sie neue Hilfe-CAB-Dateien in der Benutzeroberflächen Kultur hochladen, die von **uiculturename**angegeben wird. Weitere Informationen zu diesem Wert finden Sie unter [Version Class](/dotnet/api/system.version).
