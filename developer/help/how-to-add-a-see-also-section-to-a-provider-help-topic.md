---
title: Wie Sie einer finden Sie unter ein Hilfethema für den Anbieter auch Abschnitt hinzufügen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c754ac3-cee3-4c13-9bad-e499c8a68a09
caps.latest.revision: 4
ms.openlocfilehash: f5c48fd04c620828a6e99c5c5424d11b31fd10e5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858346"
---
# <a name="how-to-add-a-see-also-section-to-a-provider-help-topic"></a>Hinzufügen eines Bereichs „Siehe auch“ zu einem Anbieterhilfethema

In diesem Abschnitt wird erläutert, wie zum Auffüllen der **Siehe auch** Abschnitt eines Hilfethemas für den Anbieter.

Die **Siehe auch** Abschnitt besteht aus einer Liste von Themen, die an den Anbieter beziehen oder kann helfen, den Benutzer besser verstehen und verwenden Sie den Anbieter. Die Thema enthält eine Liste kann die Cmdlet-Hilfe, Hilfe durch Anbieter enthalten und ("about")-Hilfethemen in Windows PowerShell. Sie können auch Verweise auf Bücher, Artikel und online Themen, wie eine Onlineversion des Hilfethemas aktuellen Anbieter enthalten.

Wenn auf Themen verwiesen wird, geben Sie den URI oder einen Suchbegriff im nur-Text aus. Die `Get-Help` Cmdlet nicht verknüpfen oder Umleitung zu den Themen in der Liste. Darüber hinaus die `Online` Parameter, der die `Get-Help` Cmdlet funktioniert nicht mit anbieterhilfe.

Im Abschnitt Siehe auch wird erstellt, aus der `RelatedLinks` Element und die darin enthaltenen Tags. Das folgende XML zeigt, wie Sie die Tags hinzufügen.

### <a name="to-add-see-also-topics"></a>"Siehe auch" Themen hinzufügen

1. In der *AssemblyName*help.xml-DLL-Datei, in der `providerHelp` -Element, Hinzufügen einer `RelatedLinks` Element. Die `RelatedLinks` Element muss das letzte Element in der `providerHelp` Element. Nur ein `RelatedLinks` Element jedes Hilfethemas Anbieter zulässig ist.

   Beispiel:

    ```xml
    <providerHelp>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

2. Für jedes Thema in der **Siehe auch** Abschnitt innerhalb der `RelatedLinks` -Element, Hinzufügen einer `navigationLink` Element. Klicken Sie dann in jedem `navigationLink` -Element, fügen Sie eine `linkText` -Element und ein `uri` Element. Wenn Sie nicht verwenden, werden die `uri` Element können Sie ihn hinzufügen als leeres Element (\<Uri / >).

   Beispiel:

    ```xml
    <providerHelp>
        <RelatedLinks>
            <navigationLink>
                <linkText> </linkText>
                <uri> </uri>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```

3. Geben Sie den Namen des Themas zwischen der `linkText` Tags. Wenn Sie einen URI bereitstellen, geben sie zwischen den `uri` Tags. Die Onlineversion des Hilfethemas für aktuelle Anbieter zwischen an die `linkText` Tags, Typ "Online-Version:" anstelle der Name des Themas. In der Regel die "Online-Version:" Link ist das erste Thema in der Themenliste auch finden Sie unter.

   Im folgende Beispiel enthalten, siehe auch drei Themen. Die erste finden Sie in der Onlineversion des aktuellen Themas. Die zweite bezieht sich auf einem Windows PowerShell-Cmdlet-Hilfethemas. Die dritte bezieht sich auf einem anderen Thema.

    ```xml
    <providerHelp>
        <RelatedLinks>
            <navigationLink>
                <linkText> Online version: </linkText>
                <uri>http://www.fabrikam.com/help/myFunction.htm</uri>
            </navigationLink>
            <navigationLink>
                <linkText> about_functions </linkText>
                <uri/>
            </navigationLink>
            <navigationLink>
                <linkText> Windows PowerShell Getting Started Guide </linkText>
                <uri>http://go.microsoft.com/fwlink/?LinkID=89597<uri/>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```