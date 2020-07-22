---
title: Hinzufügen eines Bereichs „Siehe auch“ zu einem Anbieterhilfethema
ms.date: 09/12/2016
ms.openlocfilehash: 54adf4bb941888583eb749b7b5322b27d84c7af7
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893474"
---
# <a name="how-to-add-a-see-also-section-to-a-provider-help-topic"></a>Hinzufügen eines Bereichs „Siehe auch“ zu einem Anbieterhilfethema

In diesem Abschnitt wird erläutert, wie Sie den Abschnitt **Siehe auch** eines Hilfe Themas für den Anbieter auffüllen.

Der Abschnitt " **Siehe auch** " besteht aus einer Liste mit Themen, die mit dem Anbieter verknüpft sind oder dem Benutzer helfen können, den Anbieter besser zu verstehen und zu verwenden. Die Themenliste kann Hilfe Themen zu Cmdlets, Anbieter Hilfe und konzeptionelle Hilfe Themen ("Info") in Windows PowerShell enthalten. Sie können auch Verweise auf Bücher, Paper und Online Themen einschließen, einschließlich einer Online Version des aktuellen Anbieter Hilfe Themas.

Wenn Sie auf Online Themen verweisen, geben Sie den URI oder einen Suchbegriff als nur-Text an. Das- `Get-Help` Cmdlet verknüpft oder leitet keines der Themen in der Liste weiter. Außerdem funktioniert der- `Online` Parameter des `Get-Help` Cmdlets nicht mit der Anbieter Hilfe.

Der Abschnitt **Siehe auch** wird aus dem `RelatedLinks` -Element und den darin enthaltenen-Tags erstellt.
Der folgende XML-Code zeigt, wie die-Tags hinzugefügt werden.

### <a name="to-add-see-also-topics"></a>So fügen Sie auch Themen zu

1. Fügen Sie in der-Datei im- `<AssemblyName>.dll-help.xml` `providerHelp` Element ein- `RelatedLinks` Element hinzu. Das- `RelatedLinks` Element muss das letzte Element im- `providerHelp` Element sein. Nur ein- `RelatedLinks` Element ist in jedem Hilfethema des Anbieters zulässig.

   Beispiel:

    ```xml
    <providerHelp>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

1. Fügen Sie für jedes Thema im Abschnitt **Siehe auch** Abschnitt im- `RelatedLinks` Element ein- `navigationLink` Element hinzu. Fügen Sie dann in jedem `navigationLink` -Element ein `linkText` -Element und ein- `uri` Element hinzu. Wenn Sie das-Element nicht verwenden `uri` , können Sie es als leeres-Element () hinzufügen \<uri/> .

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

1. Geben Sie den Namen des Themas zwischen den `linkText` Tags ein. Wenn Sie einen URI bereitstellen, geben Sie ihn zwischen den `uri` Tags ein. Um die Online Version des aktuellen Anbieter Hilfe Themas anzugeben, geben Sie zwischen den `linkText` Tags "Online Version:" anstelle des Themen namens ein. In der Regel ist der Link "Online Version:" das erste Thema in der Liste "Siehe auch Themen".

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
