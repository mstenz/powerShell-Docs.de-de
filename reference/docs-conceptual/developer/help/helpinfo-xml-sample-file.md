---
title: XML-Beispieldatei HelpInfo
ms.date: 09/12/2016
ms.openlocfilehash: ec9a2a1afed4f22be00900cbc80b580ff99f8f38
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2020
ms.locfileid: "86953266"
---
# <a name="helpinfo-xml-sample-file"></a><span data-ttu-id="49f85-102">XML-Beispieldatei HelpInfo</span><span class="sxs-lookup"><span data-stu-id="49f85-102">HelpInfo XML Sample File</span></span>

<span data-ttu-id="49f85-103">In diesem Thema wird ein Beispiel für eine wohlgeformte aktualisierbare Hilfe Informationsdatei angezeigt, die häufig als "helpinfo-XML-Datei" bezeichnet wird.</span><span class="sxs-lookup"><span data-stu-id="49f85-103">This topic displays a sample of a well-formed Updatable Help Information file, commonly known as "HelpInfo XML file."</span></span> <span data-ttu-id="49f85-104">In dieser Beispieldatei werden die UI-Kulturelemente in alphabetischer Reihenfolge nach dem Namen der Benutzeroberflächen Kultur angeordnet.</span><span class="sxs-lookup"><span data-stu-id="49f85-104">In this sample file, the UI culture elements are arranged in alphabetical order by UI culture name.</span></span> <span data-ttu-id="49f85-105">Die alphabetische Reihenfolge ist eine bewährte Vorgehensweise, aber Sie ist nicht erforderlich.</span><span class="sxs-lookup"><span data-stu-id="49f85-105">Alphabetical ordering is a best practice, but it is not required.</span></span>

## <a name="helpinfo-xml-sample-file"></a><span data-ttu-id="49f85-106">XML-Beispieldatei HelpInfo</span><span class="sxs-lookup"><span data-stu-id="49f85-106">HelpInfo XML Sample File</span></span>

```xml

<?xml version="1.0" encoding="utf-8"?>
<HelpInfo xmlns="http://schemas.microsoft.com/powershell/help/2010/05">
   <HelpContentURI>https://go.microsoft.com/fwlink/?LinkID=141553</HelpContentURI>
   <SupportedUICultures>
    <UICulture>
      <UICultureName>de-DE</UICultureName>
      <UICultureVersion>2.15.0.10</UICultureVersion>
    </UICulture>
    <UICulture>
      <UICultureName>en-US</UICultureName>
      <UICultureVersion>3.2.0.7</UICultureVersion>
    </UICulture>
    <UICulture>
      <UICultureName>it-IT</UICultureName>
      <UICultureVersion>1.1.0.5</UICultureVersion>
    </UICulture>
    <UICulture>
      <UICultureName>ja-JP</UICultureName>
      <UICultureVersion>3.2.0.4</UICultureVersion>
    </UICulture>
   </SupportedUICultures>
</HelpInfo>

```
