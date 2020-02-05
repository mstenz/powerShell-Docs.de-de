---
title: Vorgehensweise beim Hinzufügen eines Abschnitts "Siehe auch" zu einem Anbieter-Hilfethema | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c754ac3-cee3-4c13-9bad-e499c8a68a09
caps.latest.revision: 4
ms.openlocfilehash: 1c1b7f4cf56ea2f9e30438a60e7bee29d87b80ba
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/04/2020
ms.locfileid: "76995952"
---
# <a name="how-to-add-a-see-also-section-to-a-provider-help-topic"></a>Hinzufügen eines Bereichs „Siehe auch“ zu einem Anbieterhilfethema

In diesem Abschnitt wird erläutert, wie Sie den Abschnitt **Siehe auch** eines Hilfe Themas für den Anbieter auffüllen.

Der Abschnitt " **Siehe auch** " besteht aus einer Liste mit Themen, die mit dem Anbieter verknüpft sind oder dem Benutzer helfen können, den Anbieter besser zu verstehen und zu verwenden. Die Themenliste kann Hilfe Themen zu Cmdlets, Anbieter Hilfe und konzeptionelle Hilfe Themen ("Info") in Windows PowerShell enthalten. Sie können auch Verweise auf Bücher, Paper und Online Themen einschließen, einschließlich einer Online Version des aktuellen Anbieter Hilfe Themas.

Wenn Sie auf Online Themen verweisen, geben Sie den URI oder einen Suchbegriff als nur-Text an. Das `Get-Help`-Cmdlet verknüpft oder leitet keines der Themen in der Liste weiter. Außerdem kann der `Online`-Parameter des `Get-Help`-Cmdlets nicht mit der Anbieter Hilfe verwendet werden.

Der Abschnitt Siehe auch wird aus dem `RelatedLinks`-Element und den darin enthaltenen-Tags erstellt. Der folgende XML-Code zeigt, wie die-Tags hinzugefügt werden.

### <a name="to-add-see-also-topics"></a>So fügen Sie "Siehe auch"-Themen hinzu

1. Fügen Sie in der Datei *AssemblyName*. dll-Help. XML innerhalb des `providerHelp`-Elements ein `RelatedLinks`-Element hinzu. Das `RelatedLinks` Element muss das letzte Element im `providerHelp` Element sein. Nur ein `RelatedLinks`-Element ist in jedem Hilfethema des Anbieters zulässig.

   Zum Beispiel:

    ```xml
    <providerHelp>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

2. Fügen Sie für jedes Thema im Abschnitt " **Siehe auch** " im `RelatedLinks`-Element ein `navigationLink`-Element hinzu. Fügen Sie dann in jedem `navigationLink`-Element ein `linkText`-Element und ein `uri`-Element hinzu. Wenn Sie das `uri`-Element nicht verwenden, können Sie es als leeres Element (\<URI/>) hinzufügen.

   Zum Beispiel:

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

3. Geben Sie den Namen des Themas zwischen den `linkText` Tags ein. Wenn Sie einen URI bereitstellen, geben Sie ihn zwischen den `uri`-Tags ein. Um die Online Version des aktuellen Hilfe Themas des Anbieters anzugeben, geben Sie zwischen den `linkText` Tags "Online Version:" anstelle des Themen namens ein. In der Regel ist der Link "Online Version:" das erste Thema in der Liste "Siehe auch Themen".

   Das folgende Beispiel enthält drei weitere Informationen. Der erste Verweis auf die Online Version des aktuellen Themas. Die zweite bezieht sich auf ein Windows PowerShell-Cmdlet-Hilfethema. Das dritte bezieht sich auf ein anderes Online Thema.

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
                <uri>https://go.microsoft.com/fwlink/?LinkID=89597<uri/>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```