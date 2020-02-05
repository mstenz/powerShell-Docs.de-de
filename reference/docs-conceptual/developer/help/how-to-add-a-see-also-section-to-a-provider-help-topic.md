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
# <a name="how-to-add-a-see-also-section-to-a-provider-help-topic"></a><span data-ttu-id="ae3e1-102">Hinzufügen eines Bereichs „Siehe auch“ zu einem Anbieterhilfethema</span><span class="sxs-lookup"><span data-stu-id="ae3e1-102">How to Add a See Also Section to a Provider Help Topic</span></span>

<span data-ttu-id="ae3e1-103">In diesem Abschnitt wird erläutert, wie Sie den Abschnitt **Siehe auch** eines Hilfe Themas für den Anbieter auffüllen.</span><span class="sxs-lookup"><span data-stu-id="ae3e1-103">This section explains how to populate the **SEE ALSO** section of a provider help topic.</span></span>

<span data-ttu-id="ae3e1-104">Der Abschnitt " **Siehe auch** " besteht aus einer Liste mit Themen, die mit dem Anbieter verknüpft sind oder dem Benutzer helfen können, den Anbieter besser zu verstehen und zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="ae3e1-104">The **SEE ALSO** section consists of a list of topics that are related to the provider or might help the user better understand and use the provider.</span></span> <span data-ttu-id="ae3e1-105">Die Themenliste kann Hilfe Themen zu Cmdlets, Anbieter Hilfe und konzeptionelle Hilfe Themen ("Info") in Windows PowerShell enthalten.</span><span class="sxs-lookup"><span data-stu-id="ae3e1-105">The topic list can include cmdlet help, provider help and conceptual ("about") help topics in Windows PowerShell.</span></span> <span data-ttu-id="ae3e1-106">Sie können auch Verweise auf Bücher, Paper und Online Themen einschließen, einschließlich einer Online Version des aktuellen Anbieter Hilfe Themas.</span><span class="sxs-lookup"><span data-stu-id="ae3e1-106">It can also include references to books, paper, and online topics, including an online version of the current provider help topic.</span></span>

<span data-ttu-id="ae3e1-107">Wenn Sie auf Online Themen verweisen, geben Sie den URI oder einen Suchbegriff als nur-Text an.</span><span class="sxs-lookup"><span data-stu-id="ae3e1-107">When you refer to online topics, provide the URI or a search term in plain text.</span></span> <span data-ttu-id="ae3e1-108">Das `Get-Help`-Cmdlet verknüpft oder leitet keines der Themen in der Liste weiter.</span><span class="sxs-lookup"><span data-stu-id="ae3e1-108">The `Get-Help` cmdlet does not link or redirect to any of the topics in the list.</span></span> <span data-ttu-id="ae3e1-109">Außerdem kann der `Online`-Parameter des `Get-Help`-Cmdlets nicht mit der Anbieter Hilfe verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="ae3e1-109">Also, the `Online` parameter of the `Get-Help` cmdlet does not work with provider help.</span></span>

<span data-ttu-id="ae3e1-110">Der Abschnitt Siehe auch wird aus dem `RelatedLinks`-Element und den darin enthaltenen-Tags erstellt.</span><span class="sxs-lookup"><span data-stu-id="ae3e1-110">The See Also section is created from the `RelatedLinks` element and the tags that it contains.</span></span> <span data-ttu-id="ae3e1-111">Der folgende XML-Code zeigt, wie die-Tags hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="ae3e1-111">The following XML shows how to add the tags.</span></span>

### <a name="to-add-see-also-topics"></a><span data-ttu-id="ae3e1-112">So fügen Sie "Siehe auch"-Themen hinzu</span><span class="sxs-lookup"><span data-stu-id="ae3e1-112">To Add "SEE ALSO" Topics</span></span>

1. <span data-ttu-id="ae3e1-113">Fügen Sie in der Datei *AssemblyName*. dll-Help. XML innerhalb des `providerHelp`-Elements ein `RelatedLinks`-Element hinzu.</span><span class="sxs-lookup"><span data-stu-id="ae3e1-113">In the *AssemblyName*.dll-help.xml file, within the `providerHelp` element, add a `RelatedLinks` element.</span></span> <span data-ttu-id="ae3e1-114">Das `RelatedLinks` Element muss das letzte Element im `providerHelp` Element sein.</span><span class="sxs-lookup"><span data-stu-id="ae3e1-114">The `RelatedLinks` element should be the last element in the `providerHelp` element.</span></span> <span data-ttu-id="ae3e1-115">Nur ein `RelatedLinks`-Element ist in jedem Hilfethema des Anbieters zulässig.</span><span class="sxs-lookup"><span data-stu-id="ae3e1-115">Only one `RelatedLinks` element is permitted in each provider help topic.</span></span>

   <span data-ttu-id="ae3e1-116">Zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="ae3e1-116">For example:</span></span>

    ```xml
    <providerHelp>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

2. <span data-ttu-id="ae3e1-117">Fügen Sie für jedes Thema im Abschnitt " **Siehe auch** " im `RelatedLinks`-Element ein `navigationLink`-Element hinzu.</span><span class="sxs-lookup"><span data-stu-id="ae3e1-117">For each topic in the **SEE ALSO** section, within the `RelatedLinks` element, add a `navigationLink` element.</span></span> <span data-ttu-id="ae3e1-118">Fügen Sie dann in jedem `navigationLink`-Element ein `linkText`-Element und ein `uri`-Element hinzu.</span><span class="sxs-lookup"><span data-stu-id="ae3e1-118">Then, within each `navigationLink` element, add one `linkText` element and one `uri` element.</span></span> <span data-ttu-id="ae3e1-119">Wenn Sie das `uri`-Element nicht verwenden, können Sie es als leeres Element (\<URI/>) hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="ae3e1-119">If you are not using the `uri` element, you can add it as an empty element (\<uri/>).</span></span>

   <span data-ttu-id="ae3e1-120">Zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="ae3e1-120">For example:</span></span>

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

3. <span data-ttu-id="ae3e1-121">Geben Sie den Namen des Themas zwischen den `linkText` Tags ein.</span><span class="sxs-lookup"><span data-stu-id="ae3e1-121">Type the topic name between the `linkText` tags.</span></span> <span data-ttu-id="ae3e1-122">Wenn Sie einen URI bereitstellen, geben Sie ihn zwischen den `uri`-Tags ein.</span><span class="sxs-lookup"><span data-stu-id="ae3e1-122">If you are providing a URI, type it between the `uri` tags.</span></span> <span data-ttu-id="ae3e1-123">Um die Online Version des aktuellen Hilfe Themas des Anbieters anzugeben, geben Sie zwischen den `linkText` Tags "Online Version:" anstelle des Themen namens ein.</span><span class="sxs-lookup"><span data-stu-id="ae3e1-123">To indicate the online version of the current provider help topic, between the `linkText` tags, type "Online version:" instead of the topic name.</span></span> <span data-ttu-id="ae3e1-124">In der Regel ist der Link "Online Version:" das erste Thema in der Liste "Siehe auch Themen".</span><span class="sxs-lookup"><span data-stu-id="ae3e1-124">Typically, the "Online version:" link is the first topic in the SEE ALSO topic list.</span></span>

   <span data-ttu-id="ae3e1-125">Das folgende Beispiel enthält drei weitere Informationen.</span><span class="sxs-lookup"><span data-stu-id="ae3e1-125">The following example include three SEE ALSO topics.</span></span> <span data-ttu-id="ae3e1-126">Der erste Verweis auf die Online Version des aktuellen Themas.</span><span class="sxs-lookup"><span data-stu-id="ae3e1-126">The first refer to the online version of the current topic.</span></span> <span data-ttu-id="ae3e1-127">Die zweite bezieht sich auf ein Windows PowerShell-Cmdlet-Hilfethema.</span><span class="sxs-lookup"><span data-stu-id="ae3e1-127">The second refers to a Windows PowerShell cmdlet help topic.</span></span> <span data-ttu-id="ae3e1-128">Das dritte bezieht sich auf ein anderes Online Thema.</span><span class="sxs-lookup"><span data-stu-id="ae3e1-128">The third refers to another online topic.</span></span>

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