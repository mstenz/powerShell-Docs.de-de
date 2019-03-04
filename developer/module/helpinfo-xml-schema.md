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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862316"
---
# <a name="helpinfo-xml-schema"></a><span data-ttu-id="67c41-102">XML-Schema von HelpInfo</span><span class="sxs-lookup"><span data-stu-id="67c41-102">HelpInfo XML Schema</span></span>

<span data-ttu-id="67c41-103">Dieses Thema enthält das XML-Schema für aktualisierbare Hilfe-Informationen-Dateien, die so genannte "HelpInfo XML-Dateien."</span><span class="sxs-lookup"><span data-stu-id="67c41-103">This topic contains the XML schema for Updatable Help Information files, commonly known as "HelpInfo XML files."</span></span>

## <a name="helpinfo-xml-schema"></a><span data-ttu-id="67c41-104">XML-Schema von HelpInfo</span><span class="sxs-lookup"><span data-stu-id="67c41-104">HelpInfo XML Schema</span></span>

<span data-ttu-id="67c41-105">HelpInfo XML-Dateien basieren auf dem folgenden XML-Schema.</span><span class="sxs-lookup"><span data-stu-id="67c41-105">HelpInfo XML files are based on the following XML schema.</span></span>

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

## <a name="helpinfo-xml-elements"></a><span data-ttu-id="67c41-106">HelpInfo-XML-Elemente</span><span class="sxs-lookup"><span data-stu-id="67c41-106">HelpInfo XML Elements</span></span>

<span data-ttu-id="67c41-107">Die HelpInfo XML-Datei enthält die folgenden Elemente.</span><span class="sxs-lookup"><span data-stu-id="67c41-107">The HelpInfo XML file includes the following elements.</span></span>

<span data-ttu-id="67c41-108">HelpContentURI enthält den URI, der den Speicherort der CAB-Dateien für das Modul-Hilfe.</span><span class="sxs-lookup"><span data-stu-id="67c41-108">HelpContentURI Contains the URI of the location of the help CAB files for the module.</span></span> <span data-ttu-id="67c41-109">Der URI muss mit "http" oder "Https" beginnen.</span><span class="sxs-lookup"><span data-stu-id="67c41-109">The URI must begin with "http" or "https".</span></span> <span data-ttu-id="67c41-110">Der URI sollte einen Speicherort im Internet angeben, aber Sie dürfen keine den Namen der CAB-Datei.</span><span class="sxs-lookup"><span data-stu-id="67c41-110">The URI should specify an Internet location, but must not include the CAB file name.</span></span> <span data-ttu-id="67c41-111">Die **HelpContentURI** Wert gleich sein oder sich von der **HelpInfoURI** Wert.</span><span class="sxs-lookup"><span data-stu-id="67c41-111">The **HelpContentURI** value can be the  same or different from the **HelpInfoURI** value.</span></span>

<span data-ttu-id="67c41-112">SupportedUICultures stellt die Hilfedateien für Module in allen UI-Kulturen.</span><span class="sxs-lookup"><span data-stu-id="67c41-112">SupportedUICultures Represents the module help files in all UI cultures.</span></span> <span data-ttu-id="67c41-113">Enthält **UICulture** Elemente, von denen jedes eine Reihe von Hilfedateien für das Modul in einer angegebenen UI-Kultur darstellt.</span><span class="sxs-lookup"><span data-stu-id="67c41-113">Contains **UICulture** elements, each of which represents a set of help files for the module in a specified UI culture.</span></span>

<span data-ttu-id="67c41-114">UICulture stellt eine Reihe von Hilfedateien für das Modul in eine angegebene Benutzeroberflächenkultur dar.</span><span class="sxs-lookup"><span data-stu-id="67c41-114">UICulture Represents a set of help files for the module in a specified UI culture.</span></span> <span data-ttu-id="67c41-115">Hinzufügen einer **UICulture** -Element für jede Benutzeroberflächenkultur, die in der die Dateien geschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="67c41-115">Add a **UICulture** element for each UI culture in which the help files are written.</span></span>

<span data-ttu-id="67c41-116">UICultureName enthält der Sprachcode für die Kultur der Benutzeroberfläche, in der die Hilfedateien geschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="67c41-116">UICultureName Contains the language code for the UI culture in which the help files are written.</span></span>

<span data-ttu-id="67c41-117">UICultureVersion enthält eine 4-Part-Versionsnummer in "N1. N2. N3. N4 "Format, das die Version der Hilfedatei CAB-Datei in der UI-Kultur darstellt.</span><span class="sxs-lookup"><span data-stu-id="67c41-117">UICultureVersion Contains a 4-part version number in "N1.N2.N3.N4" format that represents the version of the help CAB file in the UI culture.</span></span> <span data-ttu-id="67c41-118">Diese Versionsnummer sollte erhöht werden, wenn Sie neue Hilfe in der UI-Kultur eine CAB-Dateien hochladen, die angegeben wird **UICultureName**.</span><span class="sxs-lookup"><span data-stu-id="67c41-118">Increment this version number whenever you upload new help CAB files in the UI culture that is specified by **UICultureName**.</span></span> <span data-ttu-id="67c41-119">Weitere Informationen zu diesen Wert zu erhalten finden Sie unter "Version Class (System)" in MSDN.</span><span class="sxs-lookup"><span data-stu-id="67c41-119">For more information about this value, see "Version Class (System)" in MSDN.</span></span>